---
title : "Challenges & Future Direction"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

This section records the real difficulties encountered while implementing each infrastructure step for Money Manager in section **5.3** (VPC/EC2, RDS/ElastiCache, DynamoDB/SQS, S3/VPC Endpoints, CloudWatch), compared against the High Availability architecture proposed in section **2**, how they were resolved, and the direction for future improvement.

### Difficulties encountered

- **A single EC2 instance instead of a multi-AZ Auto Scaling Group:** The proposal in section 2, item 4 sets a High Availability target using EC2 + Auto Scaling Group spread across 2 Availability Zones. Within the workshop timeframe we only got as far as a single `t3.micro` EC2 instance running the `moneymanager-api`/`moneymanager-worker` containers (Step 1, section 5.3) — the Launch Template, ALB Target Group, and Auto Scaling Policy were left out, since they needed more time to validate health checks before instances could be safely replicated.
- **Confusion between Gateway Endpoint and Interface Endpoint for S3:** Initially we assumed a single VPC Endpoint type would be enough. After reading the documentation more carefully, we understood that the Gateway Endpoint is free but only works for traffic originating inside the VPC, while the Interface Endpoint (PrivateLink) is billed hourly but provides private IPs and allows access from VPN/on-prem clients through a Route 53 Resolver. Since Step 4 (section 5.3) required both EC2 inside the VPC and office workstations over VPN to reach S3, both endpoint types ended up being needed together.
- **Endpoint Policy and S3 Bucket Policy conflicting with each other:** When first setting this up, we configured the Bucket Policy to deny all access not coming through a VPC Endpoint before the Endpoint Policy had the correct bucket ARN attached as a Resource, which caused the EC2 API itself to get `Access Denied` when calling S3. It took going back through each step and testing with `aws s3 cp` directly from EC2 to find the misordered configuration.
- **Route 53 Resolver Inbound Endpoint was entirely new territory:** We had only used Route 53 for ordinary public DNS records before, never for an internal DNS resolver that lets an office VPN client resolve the S3 domain name to the Interface Endpoint's IP. This took the most time to understand out of all of Step 4.
- **Moving from MongoDB Atlas to DynamoDB and redesigning the SQS queue:** During Step 3 (section 5.3), removing the old MongoDB Atlas library and redesigning the Partition Key for the `chat_sessions`/`chat_messages` tables with the AWS SDK v2 took a fair amount of trial and error. The Redrive Policy for the `moneymanager-async-jobs-dlq` DLQ (max 3 retries) also needed a few adjustments, since the default retry count was too low and pushed otherwise-valid jobs into the DLQ.

### How they were resolved

- Compared the architecture proposed in section 2 against what could realistically be finished within the workshop timeframe: prioritized getting the core data flow working correctly (VPC, EC2 running the containers, RDS/Redis, DynamoDB/SQS, S3/VPC Endpoint, CloudWatch) first, and logged the multi-AZ Auto Scaling Group/ALB piece as a known gap to close later, rather than trying to do everything at once and finishing nothing cleanly.
- Re-read the official AWS documentation on VPC Endpoints and Route 53 Resolver, and compared Gateway vs. Interface Endpoint in a table to pick the right type for each traffic flow.
- Tested in small increments instead of configuring everything at once: created the Gateway Endpoint first, tested access from EC2 via the CLI (`aws s3 cp`, `aws dynamodb scan`, `aws sqs receive-message`), then added the Interface Endpoint and Endpoint Policy, re-testing after each change to isolate issues quickly.
- When access errors occurred, checked CloudWatch Logs and VPC Flow Logs to pinpoint which layer was blocking the request (Security Group, Bucket Policy, or Endpoint Policy) instead of guessing.

### Future direction

- Add a multi-AZ Auto Scaling Group and Application Load Balancer, matching the High Availability architecture proposed in section 2, item 4, in place of the single EC2 instance used today.
- Apply Reserved Instances to the components that run continuously (EC2, RDS, ElastiCache), as noted under the cost-optimization direction in section 2, item 8 (risk assessment).
- Move this infrastructure (VPC, Endpoints, Route Tables, Bucket Policy, etc.), currently configured manually through the Console, into Infrastructure as Code (CloudFormation or Terraform) for easier reproducibility, review, and version control.
- Add Gateway/Interface Endpoints for other services still routed through the NAT Gateway (DynamoDB, SQS) to further cut NAT Gateway costs and tighten network security.
- Consolidate the currently separate CloudWatch Alarms and Log Groups into a single unified Dashboard for faster monitoring when issues occur.
- Run recovery/failover testing for RDS multi-AZ and ElastiCache HA as planned for Week 12 in section 2, item 6 — this was not yet exercised within the scope of this workshop.
