---
title: "Week 10 Worklog - Security, Testing & AWS Service Integration"
date: 2026-04-20
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

## Week 10 - Security, Testing & AWS Service Integration

### Weekly Focus
Locking down security, integrating remaining AWS services and running tests for Money Manager

### Objectives
- Set up end-to-end security for the system (IAM, Cloudflare, JWT/OAuth2).
- Integrate the async services (SQS, Lambda) and run comprehensive tests.

### Work Schedule

| Date | Day | Work Items | Lab / Project |
|------|-----|------------|---------------|
| 22/06/2026 | Monday | Configure IAM Roles & Policies for EC2 Web-API, Lambda and S3 in the Money Manager project.<br>Review and finalize app-level security: JWT authentication, Google OAuth2 on Spring Boot.<br>Set up Cloudflare WAF, Rate Limit and Turnstile bot protection for the domain. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 23/06/2026 | Tuesday | Build the async flow: set up SQS + Dead-Letter Queue for background jobs.<br>Configure EC2 Worker to consume messages from SQS, trigger Lambda for Excel report generation and PDF invoice rendering.<br>Set up S3 buckets for storing output files (reports, invoices). | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 24/06/2026 | Wednesday | Write unit tests and integration tests for the core business APIs (income/expense, budgets, savings jars).<br>Test the async flow end-to-end: SQS -> EC2 Worker -> Lambda -> S3.<br>Run load tests and optimize performance: connection pool, cache hit rate, query tuning. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 25/06/2026 | Thursday | Prepare the Money Manager system architecture documentation.<br>Document all processing flows in detail: main business, AI chat (DynamoDB), async (SQS/Lambda), notifications (SNS).<br>Start building the presentation slides. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 26/06/2026 | Friday | Test the PayOS integration (QR payment) and Brevo SMTP (email OTP, reports) through NAT Gateway.<br>Review AWS costs: RDS MySQL, ElastiCache, EC2 ASG, Lambda usage.<br>Wrap up the week and plan for the final stretch. | [Final Project](https://github.com/vinhpham2808/J2EE) |

### Expected Outcomes
- System security fully configured: IAM, Cloudflare WAF, JWT/OAuth2.
- Async flow working: SQS -> EC2 Worker -> Lambda -> S3.
- Solid test coverage for the main APIs and critical processing flows.

### Week 10 References
- [Final Project](https://github.com/vinhpham2808/J2EE) — Money Manager (Spring Boot + React 19 + React Native Expo)
- AWS services: IAM, SQS + DLQ, Lambda, S3, SNS, CloudWatch
- External services: Cloudflare WAF, PayOS, Brevo SMTP
