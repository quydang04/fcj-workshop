---
title : "Validation & Analysis"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

We conducted practical testing procedures to validate the integrity and performance of the deployed cloud architecture, covering private DNS routing through the VPC Endpoints, S3 access control, DynamoDB/SQS integration, CloudWatch monitoring, and overall application behavior end-to-end against the live EC2/ALB backend.

### Web Application Walkthrough

The recording below walks through the full **Web** application flow running on the deployed infrastructure: DNS routing to the private S3 endpoint, monthly report export/download via S3, the Nova Money AI assistant with DynamoDB-backed chat history, asynchronous transaction processing through SQS, and the CloudWatch monitoring dashboard.

{{< youtube oCs0s21PJMw >}}

> **Mobile validation:** The Mobile app (React Native Expo) walkthrough will be added in a future update.
