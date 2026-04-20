---
title: "Week 4 Worklog"
date: 2026-04-20
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:
- Learn EC2 Auto Scaling, Application Load Balancer, Route 53 DNS, DynamoDB, CloudFront, and Highly Available architecture.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
|-----|------|------------|-----------------|-------------------|
| 2 | - Create Launch Template and Auto Scaling Group | 11/05/2026 | 11/05/2026 | [https://000006.awsstudygroup.com](https://000006.awsstudygroup.com) |
|  | - Configure Target Tracking Scaling Policy |  |  |  |
|  | - Set up ALB + Listener Rules |  |  |  |
|  | - Test scale-out/scale-in and health checks |  |  |  |
|  | - Practice: Lab 000006 – Scaling Apps with EC2 Auto Scaling |  |  |  |
| 3 | - Learn Route 53: Hosted Zone, Record Types (A, CNAME, Alias) | 12/05/2026 | 12/05/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Configure basic Routing Policies |  |  |  |
|  | - Set up Hybrid DNS with VPC |  |  |  |
|  | - Practice: Lab 000010 – Hybrid DNS with Amazon Route 53 |  |  |  |
| 4 | - Create DynamoDB Table with Partition Key & Sort Key | 13/05/2026 | 13/05/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Perform CRUD operations (console + CLI) |  |  |  |
|  | - Configure Global Secondary Index (GSI) |  |  |  |
|  | - Compare On-demand vs Provisioned capacity |  |  |  |
|  | - Compare DynamoDB vs RDS |  |  |  |
|  | - Practice: Lab 000060 – NoSQL with Amazon DynamoDB |  |  |  |
|  | - Clean up resources |  |  |  |
| 5 | - Learn CloudFront: Distribution, Origin, Behaviors | 14/05/2026 | 14/05/2026 | [https://000094.awsstudygroup.com](https://000094.awsstudygroup.com) |
|  | - Integrate CloudFront with S3 Static Website |  |  |  |
|  | - Configure HTTPS with ACM Certificate |  |  |  |
|  | - Perform cache invalidation |  |  |  |
|  | - Practice: Lab 000094 – Content Delivery with CloudFront |  |  |  |
| 6 | - Design Multi-AZ architecture: ALB + EC2 + RDS | 15/05/2026 | 15/05/2026 | [https://000101.awsstudygroup.com](https://000101.awsstudygroup.com) |
|  | - Configure Target Groups and Listener Rules |  |  |  |
|  | - Deploy RDS Multi-AZ |  |  |  |
|  | - Test health check & failover |  |  |  |
|  | - Practice: Lab 000101 – Building Highly Available Web Apps |  |  |  |

### Week 4 Achievements:
- Implemented EC2 Auto Scaling with:
  + Launch Template configuration
  + Auto Scaling Group with Target Tracking policy
  + Application Load Balancer with Listener Rules
  + Verified scale-out and scale-in behavior under load
- Configured Amazon Route 53 with Hosted Zones, multiple record types, and routing policies.
- Mastered Amazon DynamoDB fundamentals:
  + Table design with Partition Key and Sort Key
  + CRUD operations via both console and CLI
  + Global Secondary Index (GSI) for flexible querying
  + Understood On-demand vs Provisioned pricing model
- Deployed Amazon CloudFront as a CDN layer over S3:
  + Configured HTTPS using ACM Certificate
  + Managed cache behaviors and performed invalidation
- Built a fully Highly Available 3-tier web architecture:
  + Multi-AZ ALB → EC2 → RDS Multi-AZ deployment
  + Verified failover and health check behavior
