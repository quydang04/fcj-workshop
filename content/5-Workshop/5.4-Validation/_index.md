---
title : "Validation & Analysis"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

We conducted practical testing procedures to validate the integrity and performance of the deployed cloud architecture:

### DNS Routing Verification

Running DNS lookup tools inside the EC2 API server container targets the S3 public domain name. The query resolves directly to the **Private IP** addresses of the Interface Endpoint ENIs instead of S3 public IPs, confirming private routing and DNS mappings are active. As an end-to-end check, the `botdevgroup.me` application domain (served through the same private routing path) loads successfully in the browser.

![Money Manager application homepage at botdevgroup.me loading successfully, confirming DNS routing works end-to-end](/images/5-Workshop/5.4-Validation/dns-routing-site-loaded.png?width=60pc&classes=shadow)

### S3 Storage Access Verification

Uploading invoice images from the EC2 instance succeeds via the SDK Client. When a personal workstation outside the AWS network attempts to access the S3 bucket (even when utilizing Admin IAM credentials), AWS rejects the request with a **403 Access Denied** error, validating that the S3 Bucket Policy restricts external access. As a functional test, the application exports a monthly transaction report to S3 and confirms it is downloadable and readable.

![Dashboard notification confirming the monthly report file was generated and exported successfully](/images/5-Workshop/5.4-Validation/s3-export-notification.png?width=60pc&classes=shadow)

![Content of the exported report file, confirming the S3 upload/download round trip works correctly](/images/5-Workshop/5.4-Validation/s3-exported-report-content.png?width=40pc&classes=shadow)

### DynamoDB & SQS Integration Verification

Nova Money chat records are successfully written to both DynamoDB tables. Transaction events sent to SQS are pulled and processed by the Worker container instantly, leaving no pending messages in SQS or DLQ queues.

![Test conversation with the Nova Money AI assistant used to generate chat records](/images/5-Workshop/5.4-Validation/nova-money-chat-test.png?width=60pc&classes=shadow)

![DynamoDB console scan of the chat_messages table confirming the test conversation was persisted correctly](/images/5-Workshop/5.4-Validation/dynamodb-chat-messages-scan.png?width=60pc&classes=shadow)

### Performance & Cost Impact Analysis

Routing traffic privately reduces file upload latency to S3 from an average of **180ms to 45ms**. Crucially, S3 data transfers via the NAT Gateway drop to **zero**, eliminating all associated NAT Gateway data processing charges on the AWS cloud environment.
