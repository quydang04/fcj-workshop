---
title: "Week 9 Worklog - Money Manager Development & AWS Deployment"
date: 2026-04-20
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

## Week 9 - Money Manager Development & AWS Deployment

### Weekly Focus
Building core Money Manager features and deploying to AWS following the architecture designed in week 8

### Objectives
- Develop the main features of Money Manager (backend + frontend).
- Deploy to AWS following the multi-AZ architecture designed in week 8.

### Work Schedule

| Date | Day | Work Items | Lab / Project |
|------|-----|------------|---------------|
| 15/06/2026 | Monday | Review the source code and prioritize which modules to build first.<br>Make sure the dev environment is stable (Spring Boot backend, React frontend).<br>Double-check the build & deploy process before starting new feature work. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 16/06/2026 | Tuesday | Develop the core business APIs: income/expense tracking, budgets, savings jars.<br>Verify entity mappings, table relationships and data access flows.<br>Test locally and make sure the APIs work correctly with MySQL. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 17/06/2026 | Wednesday | Finish the authentication flow: JWT token + Google OAuth2.<br>Build the APIs for subscription-based access control (Free/Premium tiers).<br>Update the technical docs and API documentation. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 18/06/2026 | Thursday | Deploy the Spring Boot backend to EC2 in the Private Subnet.<br>Set up the ALB in the Public Subnet to route traffic to EC2.<br>Configure the Auto Scaling Group for EC2 Web-API to scale automatically. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 19/06/2026 | Friday | Configure RDS MySQL with multi-AZ.<br>Configure ElastiCache Redis for caching and session storage, test connectivity from EC2. | [Final Project](https://github.com/vinhpham2808/J2EE) |

### Expected Outcomes
- Core business APIs working (income/expense tracking, authentication, access control).
- Backend deployed on EC2 with ALB + Auto Scaling Group.
- RDS MySQL and ElastiCache Redis configured and connected successfully.

### Week 9 References
- [Final Project](https://github.com/vinhpham2808/J2EE) — Money Manager (Spring Boot + React 19 + React Native Expo)
- AWS services: EC2 ASG, ALB, RDS MySQL, ElastiCache Redis
