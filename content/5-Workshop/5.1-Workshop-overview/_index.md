---
title : "Introduction"
date : 2024-01-01 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

### Deploying Infrastructure and Secure Connection to Amazon S3

![Overall Network Architecture and AWS Services Integration](/images/5-Workshop/5.1-Workshop-overview/architecture-diagram.png?width=70pc&classes=shadow)

*Figure 1. Overall Network Architecture and AWS Services Integration*

### General Introduction

This workshop documents the complete hands-on execution of building and validating the cloud infrastructure for the **Money Manager** personal finance management platform.

The workshop covers:

- Deployment of a highly secure private network (VPC).
- Separation of frontend API and background Worker instances.
- Integration of data storage tiers: **MySQL RDS**, **Redis ElastiCache**, **DynamoDB**.
- Deployment of **SQS** asynchronous queues.
- Optimization of data transfer costs using **S3 VPC Endpoints** to shield OCR receipt images from public Internet routing and NAT Gateway charges.

Through this practical exercise, we adopted cloud architecture methodologies aligned with the **AWS Well-Architected Framework**, placing specific emphasis on two core pillars: **Security** and **Cost Optimization**.
