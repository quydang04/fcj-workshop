---
title : "Validation & Analysis"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

We conducted practical testing procedures to validate the integrity and performance of the deployed cloud architecture:

### DNS Routing Verification

Running DNS lookup tools inside the EC2 API server container targets the S3 public domain name. The query resolves directly to the **Private IP** addresses of the Interface Endpoint ENIs instead of S3 public IPs, confirming private routing and DNS mappings are active.

### S3 Storage Access Verification

Uploading invoice images from the EC2 instance succeeds via the SDK Client. When a personal workstation outside the AWS network attempts to access the S3 bucket (even when utilizing Admin IAM credentials), AWS rejects the request with a **403 Access Denied** error, validating that the S3 Bucket Policy restricts external access.

### DynamoDB & SQS Integration Verification

Nova Money chat records are successfully written to both DynamoDB tables. Transaction events sent to SQS are pulled and processed by the Worker container instantly, leaving no pending messages in SQS or DLQ queues.

### Performance & Cost Impact Analysis

Routing traffic privately reduces file upload latency to S3 from an average of **180ms to 45ms**. Crucially, S3 data transfers via the NAT Gateway drop to **zero**, eliminating all associated NAT Gateway data processing charges on the AWS cloud environment.
