---
title : "Implementation Steps"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

### Step 1: Deploy VPC Network & EC2 Instances

Workflow for constructing the isolated network topology and primary compute hosts:

- Create a custom **VPC** with a CIDR block of `10.0.0.0/16` to establish the primary private network envelope.
- Segment the network into **Public Subnets** (hosting the ALB and NAT Gateway for direct public internet access) and **Private Subnets** (hosting the EC2 API and Worker instances to prevent direct routing to the Internet Gateway).
- Configure corresponding **Route Tables**, where the Public Subnet routes outbound traffic directly through the Internet Gateway, and the Private Subnet routes outbound traffic through the NAT Gateway provisioned in the Public Subnet.
- Launch a `t3.micro` EC2 instance within the Private Subnet running **Amazon Linux 2023**. Install **Docker** and **Docker Compose** to manage and execute the containerized Spring Boot backend application.
- The Spring Boot backend is separated into two independently executing containers: the `moneymanager-api` container handles external REST API requests on port `8080` (the ALB offloads external HTTPS traffic and forwards it here), and the `moneymanager-worker` container processes SQS messages and background cron schedules without exposing any network ports.
- The environment configuration file `/app/.env` is stored securely on the EC2 host EBS volume and dynamically injected into the running containers during system startup.

### Step 2: Configure RDS MySQL & ElastiCache Redis

Deploy the relational storage tier and the high-speed caching engine:

- Provision an **RDS MySQL 8.0** database with a `db.t3.micro` instance class. The database is placed inside a dedicated private Subnet Group spanning the Private Subnets to completely block external access.
- The RDS **Security Group** is configured with a strict deny-all policy, only allowing TCP connection requests originating from the EC2 API host security group on default port `3306`. The connection from the API server leverages **Hibernate JPA** to automatically update the database schema based on Java Entity classes.
- Create an **ElastiCache Redis** cluster utilizing `cache.t3.micro` nodes running inside the Private Subnet. The Redis Security Group restricts inbound traffic to port `6379`, only accepting connections from the EC2 API security group.
- The Spring Boot API uses Redis as a data caching layer for static metadata to reduce MySQL IO utilization, and implements a rate-limiting algorithm for the **Nova Money** AI assistant chats to prevent spam attacks from exhausting API credentials.

### Step 3: Implement Amazon DynamoDB & AWS SQS

Establish the unstructured NoSQL storage layer and the event-driven message queue system:

- In the **DynamoDB** dashboard, create two tables using the **On-Demand Capacity Mode**: `chat_sessions` for active conversation metadata (Partition key: `id` of type String) and `chat_messages` for individual message history (Partition key: `id` of type String).
- Grant DynamoDB read/write permissions to the EC2 instances via **IAM Instance Profiles**. In the Spring Boot codebase, remove the legacy MongoDB Atlas dependencies, integrate the **AWS SDK v2** for DynamoDB, and define a `DynamoDbClient` bean targeting the `ap-southeast-1` region to enable fast, serverless, and cost-efficient storage for Nova Money assistant conversation logs.
- Create a standard **AWS SQS** queue named `moneymanager-async-jobs`. To manage messages that fail processing repeatedly, provision a **Dead Letter Queue (DLQ)** named `moneymanager-async-jobs-dlq` linked with the main queue via a Redrive Policy set to a maximum of 3 retries.
- In the application backend, when a major financial transaction is recorded, the API container serializes the event data to a JSON string and uses `SqsTemplate` to publish it to SQS. The Worker container uses the `@SqsListener` annotation to pull from SQS and execute heavy processing asynchronously (e.g., dispatching email receipts and budget re-allocation) without slowing down the user's API response time.

### Step 4: Configure S3 Security & VPC Endpoints

Establish private network connections to optimize latency and minimize costs when interacting with S3:

- Create an **Amazon S3 Bucket** named `botdevgroup-documents` with **Block Public Access** enabled and **SSE-S3** server-side encryption enabled.
- Create a **Gateway VPC Endpoint** for S3 and attach it to the Route Tables of the Private Subnets. The automatically generated routing rule directs S3 traffic from EC2 over the internal AWS backbone network rather than through the NAT Gateway, eliminating 100% of NAT Gateway data processing fees for S3 traffic and improving file transfer speeds.
- Create an **Interface VPC Endpoint (AWS PrivateLink)** within the Private Subnets across two different Availability Zones to guarantee high availability. This endpoint allocates private IP addresses directly from the VPC CIDR.
- Configure a **Route 53 Inbound Resolver** in the VPC to listen for DNS requests from on-premises office networks connecting via VPN. The resolver maps S3 public domains to the Interface Endpoint ENIs' private IPs, enabling secure file uploads and report downloads from office workstations over VPN.
- Configure **Endpoint Policies** on both VPC Endpoints to restrict access exclusively to the project's S3 bucket, preventing data leaks. Simultaneously, apply an **S3 Bucket Policy** to explicitly deny all S3 bucket access requests from any source unless they originate from the authorized VPC Endpoints.

> See the overall architecture diagram in section **5.1. Introduction** for how these components fit together.
