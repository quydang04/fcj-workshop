---
title: "Proposal"
date: 2026-04-20
weight: 2
chapter: false
pre: "<b>2. </b>"
---

### Money Manager – Personal Finance Management System on AWS

## A Full-Stack Solution for Personal Finance on AWS Cloud

### 1. Summary

Money Manager is a personal finance app built for both **Web and Mobile**. It lets users track income and expenses, set budgets, manage spending jars and savings goals, forecast finances, export reports via Excel/Email, scan invoices using OCR, and chat with an integrated AI assistant called **Nova Money**.

On the technical side, the system follows a multi-tier architecture — Web/Mobile apps on the client side, and AWS services powering the backend infrastructure.

### 2. Problem Statement

**The problem:** Most people manage their finances manually or with basic apps that lack deep analytics, spending forecasts, and AI-powered financial advice.

**Our solution:** Money Manager uses a multi-tier AWS Cloud architecture with High Availability, combined with AI (Google Gemini and OpenRouter GPT-OSS) to deliver a complete finance management experience — from expense tracking, budgeting, and financial forecasting to invoice recognition via OCR and the Nova Money AI assistant.

**Value proposition:** Saves users time on financial management, enables smarter spending decisions through AI forecasting, and provides a solid foundation for Premium features down the road.

### 3. Solution Architecture

The entire system is deployed on **AWS Cloud in the Singapore Region (ap-southeast-1)**, inside a VPC spanning **2 Availability Zones** for High Availability.

![Money Manager Platform Architecture](/images/2-Proposal/platform_architecture.jpg)

**Tech stack:**

- **Backend:** Spring Boot (Java 21), layered architecture — Controller -> Service -> Repository
- **Frontend Web:** React 19 + Vite
- **Mobile:** React Native (Expo)
- **AI:** Google Gemini (chat, agent, OCR, forecasting) and OpenRouter GPT-OSS (in-depth report analysis for Premium tier)

**AWS services used:**

- **Application Load Balancer (ALB):** Sits in the Public Subnet, distributes traffic across EC2 instances, spans 2 AZs.
- **Amazon EC2 + Auto Scaling Group:** Runs the Spring Boot backend in Private Subnets, auto-scales based on load.
- **EC2 Worker:** Dedicated instance for processing background jobs (consumes from SQS).
- **Amazon RDS MySQL:** Primary relational database, deployed multi-AZ.
- **Amazon ElastiCache (Redis):** Used for caching, session storage and rate limiting. Deployed HA across 2 AZs.
- **Amazon DynamoDB:** Stores Nova Money AI chat history with low latency reads.
- **Amazon SQS + DLQ:** Message queue for heavy tasks (Excel report export, PDF invoice rendering, scheduled reports). Dead-Letter Queue handles failed jobs.
- **AWS Lambda:** Serverless functions to generate report and invoice files.
- **Amazon S3:** Stores report files, PDF invoices and invoice images.
- **Amazon SNS:** Sends email alerts to admin when budgets are exceeded or subscriptions are expiring.
- **Amazon CloudWatch:** Full monitoring — logs, metrics, alarms across ALB, EC2, RDS, Lambda, SQS.
- **NAT Gateway:** Allows EC2 in Private Subnets to reach external services.
- **IAM Roles:** Access control between AWS services.

**Main processing flows:**

- **User flow:** User accesses via Web/Mobile -> Cloudflare (DNS, WAF, DDoS protection, Rate Limit, Turnstile bot detection) -> ALB -> EC2 Web-API.
- **Business logic flow:** EC2 handles login (JWT + Google OAuth2), income/expense management, budgets, savings jars -> writes to RDS MySQL, caches in ElastiCache Redis.
- **AI chat flow:** User chats with Nova Money -> conversation history saved to DynamoDB -> recent messages pulled as context for the AI model.
- **Async flow:** EC2 Web-API pushes job to SQS -> EC2 Worker consumes -> calls Lambda to generate files -> stores result in S3.
- **Notification flow:** Alert event triggers -> SNS sends email to Admin.
- **Outbound flow:** EC2 -> NAT Gateway -> PayOS (QR payment), Brevo SMTP (email OTP, reports), Google Gemini API.

### 4. Technical Implementation

**Implementation phases:**

- **Research and design:** Requirements analysis, AWS architecture design following Well-Architected Framework, database schema and API endpoint design.
- **Cost estimation:** Using AWS Pricing Calculator to estimate costs for RDS, ElastiCache, EC2, Lambda, S3 and related services.
- **Backend development:** Building the Spring Boot API (Java 21), integrating JWT/OAuth2, connecting RDS MySQL, setting up ElastiCache Redis.
- **Frontend development:** Building the Web UI with React 19 + Vite and Mobile app with React Native Expo.
- **AI integration:** Connecting Google Gemini for chat/agent/OCR/forecasting, OpenRouter GPT-OSS for Premium report analysis.
- **Deployment and testing:** Deploying to AWS (VPC, EC2 ASG, ALB, RDS, ElastiCache), configuring Cloudflare, running end-to-end tests.

**Technical requirements:**

- **Backend:** Java 21, Spring Boot, Spring Security (JWT + OAuth2), Spring Data JPA, Hibernate.
- **Frontend:** React 19, Vite, React Native (Expo), responsive design.
- **Database:** RDS MySQL (multi-AZ), DynamoDB (chat history), ElastiCache Redis (cache/session).
- **Infrastructure:** VPC (2 AZ), ALB, EC2 ASG (Graviton), NAT Gateway, SQS + DLQ, Lambda, S3, SNS, CloudWatch, IAM Roles.
- **Security:** Cloudflare (WAF, DDoS protection, Rate Limit, Turnstile), HTTPS, IAM policies, Security Groups.

### 5. Timeline & Milestones

- **Weeks 1–6 (20/04 – 29/05):** Learning core AWS services (IAM, VPC, EC2, RDS, S3, Lambda, API Gateway, CloudFormation, DynamoDB) through CloudJourney labs.
- **Weeks 7–8 (01/06 – 12/06):**
  - Exploring the codebase, analyzing the architecture, setting up the dev environment.
  - First deployment to EC2, configuring RDS, integrating S3/CloudFront.
  - Studying Well-Architected Framework, AWS SAM and designing the project architecture.
- **Week 9 (15/06 – 19/06):**
  - Building core features: Spring Boot backend, React frontend, database connectivity.
  - Deploying to EC2 in Private Subnet, setting up ALB and Auto Scaling Group.
- **Week 10 (22/06 – 26/06):**
  - Configuring IAM, security (JWT, OAuth2, Cloudflare WAF).
  - Deploying Spring Boot backend to EC2 ASG, setting up ALB, RDS MySQL, ElastiCache.
  - Running unit tests, integration tests, load tests and optimizing performance.
- **Week 11 (29/06 – 03/07):**
  - Polishing UI/UX for Web (React 19 + Vite) and Mobile (React Native Expo), running E2E tests.
  - Setting up CloudWatch monitoring, preparing presentation and demo.
  - Code review, writing architecture report, backing up data.
- **Week 12 (06/07 – 10/07):**
  - Post-deployment support, security hardening, AWS cost optimization.
  - Testing recovery/failover (RDS multi-AZ, ElastiCache HA).
  - Submitting the report and final presentation.

### 6. Budget Estimation

**Monthly infrastructure costs (estimated):**

- **Amazon EC2 (ASG – Graviton):** ~15.00 USD/month (t4g.small, 2 instances min).
- **Application Load Balancer:** ~16.20 USD/month.
- **Amazon RDS MySQL:** ~29.00 USD/month (db.t4g.medium, multi-AZ).
- **Amazon ElastiCache (Redis):** ~12.00 USD/month (cache.t4g.micro, 2 node HA).
- **Amazon DynamoDB:** ~1.00 USD/month (on-demand, chat history).
- **Amazon S3:** ~0.50 USD/month (reports, invoices, images).
- **AWS Lambda:** ~0.00 USD/month (free tier).
- **Amazon SQS:** ~0.00 USD/month (free tier).
- **Amazon SNS:** ~0.00 USD/month (free tier).
- **NAT Gateway:** ~32.00 USD/month (outbound traffic).
- **Amazon CloudWatch:** ~3.00 USD/month (logs, metrics, alarms).
- **Cloudflare (Free plan):** 0.00 USD/month.

**Total:** ~108.70 USD/month (~1,304.40 USD/year)

### 7. Risk Assessment

**Key risks:**

- Database connection issues: high impact but low probability, since RDS multi-AZ ensures availability.
- System overload: high impact, medium probability. Auto Scaling Group handles scaling automatically.
- Data loss: high impact but low probability thanks to RDS multi-AZ with automated backups.
- DDoS/Bot attacks: medium impact and medium probability, handled by Cloudflare WAF, Rate Limit and Turnstile.
- AWS cost overrun: medium impact and medium probability, mitigated with CloudWatch billing alarms for early warning.

**Mitigation:**

- Database: RDS multi-AZ failover, ElastiCache HA.
- Performance: Auto Scaling Group, ElastiCache Redis for caching, SQS to offload heavy tasks from the main flow.
- Security: Cloudflare WAF + Turnstile, JWT + OAuth2, IAM least privilege, Security Groups.
- Cost: CloudWatch billing alarm, Reserved Instances, Lambda optimization.

**Contingency plans:**

- Auto failover between 2 AZs for both RDS MySQL and ElastiCache Redis.
- Dead-Letter Queue on SQS for retrying or debugging failed jobs.
- CloudWatch Alarms trigger automatically when performance degrades or error rates spike.

### 8. Expected Outcomes

**Technical outcomes:** A stable, production-ready personal finance system running on AWS with High Availability, supporting both Web and Mobile. AI integration (Google Gemini, OpenRouter) for financial forecasting, invoice OCR and the Nova Money assistant. Efficient async processing with SQS + Lambda for report generation and invoice rendering.

**Long-term value:** The platform scales flexibly thanks to Auto Scaling Group and multi-AZ architecture. There's room to grow with Premium features (deep report analysis via OpenRouter GPT-OSS), additional payment gateways, and international expansion.
