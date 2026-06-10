---
title: "Week 4 Worklog - Auto Scaling, Route 53, DynamoDB, CloudFront & HA Architecture"
date: 2026-04-20
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

## Week 4 - Auto Scaling, Route 53, DynamoDB, CloudFront & HA Architecture

### Weekly Focus
Auto Scaling + Route 53 + DynamoDB + CloudFront + highly available architecture

### Objectives
- Learn EC2 Auto Scaling, Application Load Balancer, Route 53 DNS, DynamoDB, CloudFront, and Highly Available architecture.

### Work Schedule

| Date | Day | Work Items | Lab / Project |
|------|-----|------------|---------------|
| 11/05/2026 | Monday | Create a launch template and Auto Scaling Group.<br>Configure a target tracking scaling policy.<br>Set up an Application Load Balancer with listener rules.<br>Test scale-out, scale-in, and health check behavior in Lab 000006. | [Lab 000006 - Scaling Apps with EC2 Auto Scaling](https://000006.awsstudygroup.com) |
| 12/05/2026 | Tuesday | Learn Route 53 hosted zones and common record types such as A, CNAME, and Alias.<br>Configure basic routing policies.<br>Set up a hybrid DNS pattern with VPC integration.<br>Practice Lab 000010. | [Lab 000010 - Hybrid DNS Management with Amazon Route 53](https://000010.awsstudygroup.com) |
| 13/05/2026 | Wednesday | Create a DynamoDB table with partition key and sort key design.<br>Perform CRUD operations through the console and CLI.<br>Configure a Global Secondary Index and compare on-demand versus provisioned capacity.<br>Practice Lab 000060 and clean up resources. | [Lab 000060 - NoSQL Database Essentials with Amazon DynamoDB](https://000060.awsstudygroup.com) |
| 14/05/2026 | Thursday | Learn CloudFront fundamentals including distributions, origins, and cache behaviors.<br>Integrate CloudFront with an S3 static website.<br>Configure HTTPS with ACM and perform cache invalidation.<br>Practice Lab 000094. | [Lab 000094 - Content Delivery with CloudFront](https://000094.awsstudygroup.com) |
| 15/05/2026 | Friday | Design a Multi-AZ architecture using ALB, EC2, and RDS.<br>Configure target groups and listener rules.<br>Deploy RDS Multi-AZ and test health checks plus failover behavior.<br>Practice Lab 000101. | [Lab 000101 - Building Highly Available Web Apps](https://000101.awsstudygroup.com) |

### Expected Outcomes
- Understand how EC2 Auto Scaling, ALB, and scaling policies work together in an elastic architecture.
- Configure Route 53 DNS records and basic routing strategies, including hybrid DNS concepts.
- Work with DynamoDB table design, CRUD operations, secondary indexes, and capacity models.
- Use CloudFront to deliver S3 content securely over HTTPS with cache management.
- Build and validate a highly available Multi-AZ web architecture using ALB, EC2, and RDS.

### Week 4 References
- [Lab 000006 - Scaling Applications with EC2 Auto Scaling](https://000006.awsstudygroup.com)
- [Lab 000010 - Hybrid DNS Management with Amazon Route 53](https://000010.awsstudygroup.com)
- [Lab 000060 - NoSQL Database Essentials with Amazon DynamoDB](https://000060.awsstudygroup.com)
- [Lab 000094 - Content Delivery with Amazon CloudFront](https://000094.awsstudygroup.com)
- [Lab 000101 - Building Highly Available Web Applications](https://000101.awsstudygroup.com)
