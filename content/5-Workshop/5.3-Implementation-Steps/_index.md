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

![VPC list showing the custom VPC with CIDR block 10.0.0.0/16](/images/5-Workshop/5.3-Implementation-Steps/vpc-list.png?width=60pc&classes=shadow)

- Segment the network into **Public Subnets** (hosting the ALB and NAT Gateway for direct public internet access) and **Private Subnets** (hosting the EC2 API and Worker instances to prevent direct routing to the Internet Gateway).

![Subnets list showing 6 subnets distributed across Public and Private tiers](/images/5-Workshop/5.3-Implementation-Steps/subnets-list.png?width=60pc&classes=shadow)

- Configure corresponding **Route Tables**, where the Public Subnet routes outbound traffic directly through the Internet Gateway, and the Private Subnet routes outbound traffic through the NAT Gateway provisioned in the Public Subnet.
- Launch a `t3.micro` EC2 instance within the Private Subnet running **Amazon Linux 2023**. Install **Docker** and **Docker Compose** to manage and execute the containerized Spring Boot backend application.

![EC2 Instances list showing the moneymanager-app t3.micro instance in Running state](/images/5-Workshop/5.3-Implementation-Steps/ec2-instances-list.png?width=60pc&classes=shadow)

![EC2 instance detail page for moneymanager-app showing its private IP address](/images/5-Workshop/5.3-Implementation-Steps/ec2-instance-detail.png?width=60pc&classes=shadow)

- The Spring Boot backend is separated into two independently executing containers: the `moneymanager-api` container handles external REST API requests on port `8080` (the ALB offloads external HTTPS traffic and forwards it here), and the `moneymanager-worker` container processes SQS messages and background cron schedules without exposing any network ports.
- The environment configuration file `/app/.env` is stored securely on the EC2 host EBS volume and dynamically injected into the running containers during system startup.

### Step 2: Configure RDS MySQL & ElastiCache Redis

Deploy the relational storage tier and the high-speed caching engine:

- Provision an **RDS MySQL 8.0** database with a `db.t3.micro` instance class. The database is placed inside a dedicated private Subnet Group spanning the Private Subnets to completely block external access.

![RDS Databases list showing the db-moneymanager MySQL 8.0 instance](/images/5-Workshop/5.3-Implementation-Steps/rds-databases-list.png?width=60pc&classes=shadow)

![RDS instance detail page showing the Connectivity & security tab](/images/5-Workshop/5.3-Implementation-Steps/rds-instance-detail.png?width=60pc&classes=shadow)

- The RDS **Security Group** is configured with a strict deny-all policy, only allowing TCP connection requests originating from the EC2 API host security group on default port `3306`. The connection from the API server leverages **Hibernate JPA** to automatically update the database schema based on Java Entity classes.
- Create an **ElastiCache Redis** cluster utilizing `cache.t3.micro` nodes running inside the Private Subnet. The Redis Security Group restricts inbound traffic to port `6379`, only accepting connections from the EC2 API security group.

![ElastiCache Redis OSS caches list showing the moneymanager-redis cluster](/images/5-Workshop/5.3-Implementation-Steps/elasticache-redis-list.png?width=60pc&classes=shadow)

![ElastiCache cluster detail page for moneymanager-redis](/images/5-Workshop/5.3-Implementation-Steps/elasticache-cluster-detail.png?width=60pc&classes=shadow)

- The Spring Boot API uses Redis as a data caching layer for static metadata to reduce MySQL IO utilization, and implements a rate-limiting algorithm for the **Nova Money** AI assistant chats to prevent spam attacks from exhausting API credentials.

### Step 3: Implement Amazon DynamoDB & AWS SQS

Establish the unstructured NoSQL storage layer and the event-driven message queue system:

- In the **DynamoDB** dashboard, create two tables using the **On-Demand Capacity Mode**: `chat_sessions` for active conversation metadata (Partition key: `id` of type String) and `chat_messages` for individual message history (Partition key: `id` of type String).

![DynamoDB Tables list showing chat_messages and chat_sessions](/images/5-Workshop/5.3-Implementation-Steps/dynamodb-tables-list.png?width=60pc&classes=shadow)

![chat_messages table detail page](/images/5-Workshop/5.3-Implementation-Steps/dynamodb-chat-messages-detail.png?width=60pc&classes=shadow)

![chat_sessions table detail page](/images/5-Workshop/5.3-Implementation-Steps/dynamodb-chat-sessions-detail.png?width=60pc&classes=shadow)

- Grant DynamoDB read/write permissions to the EC2 instances via **IAM Instance Profiles**. In the Spring Boot codebase, remove the legacy MongoDB Atlas dependencies, integrate the **AWS SDK v2** for DynamoDB, and define a `DynamoDbClient` bean targeting the `ap-southeast-1` region to enable fast, serverless, and cost-efficient storage for Nova Money assistant conversation logs.
- Create a standard **AWS SQS** queue named `moneymanager-async-jobs`. To manage messages that fail processing repeatedly, provision a **Dead Letter Queue (DLQ)** named `moneymanager-async-jobs-dlq` linked with the main queue via a Redrive Policy set to a maximum of 3 retries.

![SQS Queues list showing moneymanager-async-jobs and its DLQ](/images/5-Workshop/5.3-Implementation-Steps/sqs-queues-list.png?width=60pc&classes=shadow)

![Main queue moneymanager-async-jobs detail page](/images/5-Workshop/5.3-Implementation-Steps/sqs-main-queue-detail.png?width=60pc&classes=shadow)

![Dead Letter Queue moneymanager-async-jobs-dlq detail page](/images/5-Workshop/5.3-Implementation-Steps/sqs-dlq-detail.png?width=60pc&classes=shadow)

- In the application backend, when a major financial transaction is recorded, the API container serializes the event data to a JSON string and uses `SqsTemplate` to publish it to SQS. The Worker container uses the `@SqsListener` annotation to pull from SQS and execute heavy processing asynchronously (e.g., dispatching email receipts and budget re-allocation) without slowing down the user's API response time.
- The IAM Role attached to the EC2 instances is scoped to the minimum set of SQS actions required, following the least-privilege principle:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "sqs:SendMessage",
        "sqs:ReceiveMessage",
        "sqs:DeleteMessage",
        "sqs:GetQueueAttributes"
      ],
      "Resource": "arn:aws:sqs:ap-southeast-1:123456789012:moneymanager-async-jobs"
    }
  ]
}
```

### Step 4: Configure S3 Security & VPC Endpoints

Establish private network connections to optimize latency and minimize costs when interacting with S3:

- Create an **Amazon S3 Bucket** named `botdevgroup-documents` with **Block Public Access** enabled and **SSE-S3** server-side encryption enabled.

![S3 Buckets list showing botdevgroup-documents alongside the project's static website bucket](/images/5-Workshop/5.3-Implementation-Steps/s3-buckets-list.png?width=60pc&classes=shadow)

![Objects stored in the botdevgroup-documents bucket](/images/5-Workshop/5.3-Implementation-Steps/s3-documents-bucket-objects.png?width=60pc&classes=shadow)

![Objects stored in the botdevgroup.me static website bucket](/images/5-Workshop/5.3-Implementation-Steps/s3-website-bucket-objects.png?width=60pc&classes=shadow)

- Create a **Gateway VPC Endpoint** for S3 and attach it to the Route Tables of the Private Subnets. The automatically generated routing rule directs S3 traffic from EC2 over the internal AWS backbone network rather than through the NAT Gateway, eliminating 100% of NAT Gateway data processing fees for S3 traffic and improving file transfer speeds. The endpoint was provisioned via the AWS CLI and attached directly to the Private Subnet route tables:

```bash
aws ec2 create-vpc-endpoint \
  --vpc-id vpc-0123456789abcdef0 \
  --vpc-endpoint-type Gateway \
  --service-name com.amazonaws.ap-southeast-1.s3 \
  --route-table-ids rtb-0123456789abcdef0
```
- Create an **Interface VPC Endpoint (AWS PrivateLink)** within the Private Subnets across two different Availability Zones to guarantee high availability. This endpoint allocates private IP addresses directly from the VPC CIDR.

![VPC dashboard listing the VPCs used to configure the PrivateLink endpoint](/images/5-Workshop/5.3-Implementation-Steps/vpc-dashboard-list.png?width=60pc&classes=shadow)

![VPC resource map for botdevgroup-vpc showing subnets, route tables, and endpoint connections](/images/5-Workshop/5.3-Implementation-Steps/vpc-resource-map.png?width=60pc&classes=shadow)

- Configure a **Route 53 Inbound Resolver** in the VPC to listen for DNS requests from on-premises office networks connecting via VPN. The resolver maps S3 public domains to the Interface Endpoint ENIs' private IPs, enabling secure file uploads and report downloads from office workstations over VPN.
- Configure **Endpoint Policies** on both VPC Endpoints to restrict access exclusively to the project's S3 bucket, preventing data leaks. Simultaneously, apply an **S3 Bucket Policy** to explicitly deny all S3 bucket access requests from any source unless they originate from the authorized VPC Endpoints.

### Step 5: Configure CloudWatch Monitoring & Alerting

Deploy centralized observability for the EC2 API/Worker fleet and its dependent services:

- Configure a **Log Appender** in the Spring Boot application (using the AWS Logback Appender library) to automatically stream application logs from the API and Worker containers to the CloudWatch Log Group `/aws/ec2/moneymanager-app`. The RDS MySQL error log (`/aws/rds/moneymanager-db`) and VPC network traffic (`/aws/vpc/flow-logs`) are streamed into their own dedicated Log Groups as well, giving a single place to inspect activity across the stack.

![CloudWatch Log Groups list showing /aws/ec2/moneymanager-app, /aws/rds/moneymanager-db and /aws/vpc/flow-logs actively receiving log streams](/images/5-Workshop/5.3-Implementation-Steps/cloudwatch-log-groups-list.png?width=60pc&classes=shadow)

- Set up a **Metric Filter** named `EC2ErrorFilter` on the `/aws/ec2/moneymanager-app` Log Group to scan incoming log streams and count the frequency of critical errors (matching patterns such as `ERROR` or `Exception`), emitting the result as the custom metric `EC2ErrorCount`. A matching `RDSLogErrorFilter` was also configured on `/aws/rds/moneymanager-db` to track database-level error frequency.

![EC2ErrorFilter metric filter detail on the /aws/ec2/moneymanager-app log group, linked to the EC2ErrorAlarm alarm](/images/5-Workshop/5.3-Implementation-Steps/cloudwatch-ec2-metric-filter-detail.png?width=60pc&classes=shadow)

![RDSLogErrorFilter metric filter detail on the /aws/rds/moneymanager-db log group](/images/5-Workshop/5.3-Implementation-Steps/cloudwatch-rds-metric-filter-detail.png?width=60pc&classes=shadow)

- Provision a **CloudWatch Alarm** named `EC2ErrorAlarm` on the `EC2ErrorCount` metric, configured to enter the `ALARM` state once the count reaches 1 within a 5-minute evaluation period, automatically dispatching a notification via SNS.

```xml
<!-- logback-spring.xml -->
<configuration>
    <appender name="CLOUDWATCH" class="ca.pjer.logback.AwsLogsAppender">
        <groupName>/aws/ec2/moneymanager-app</groupName>
        <streamName>backend-logs</streamName>
        <regionName>ap-southeast-1</regionName>
        <layout>
            <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n</pattern>
        </layout>
    </appender>

    <root level="INFO">
        <appender-ref ref="CLOUDWATCH" />
    </root>
</configuration>
```

> See the overall architecture diagram in section **5.1. Introduction** for how these components fit together.
