---
title: "Week 11 Worklog - Finishing Money Manager & Submission Prep"
date: 2026-04-20
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

## Week 11 - Finishing Money Manager & Submission Prep

### Weekly Focus
Polishing the Money Manager product, optimizing UI/UX, setting up monitoring and preparing for submission

### Objectives
- Polish UI/UX for both Web and Mobile, run E2E tests.
- Set up monitoring, prepare documentation and demo for submission.

### Work Schedule

| Date | Day | Work Items | Lab / Project |
|------|-----|------------|---------------|
| 29/06/2026 | Monday | Review and optimize the UI/UX on React 19 + Vite (Web) and React Native Expo (Mobile).<br>Test cross-platform compatibility and responsive design for both Web and Mobile.<br>Run E2E tests on core features: sign up/login, income/expense tracking, Nova Money AI chat. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 30/06/2026 | Tuesday | Finalize the deployment docs and setup guide for the Money Manager system.<br>Configure Amazon CloudWatch: Logs, Metrics, Alarms for ALB, EC2, RDS, Lambda, SQS.<br>Prepare rollback scripts and verify High Availability across 2 Availability Zones. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 01/07/2026 | Wednesday | Prepare the presentation and demo script for Money Manager.<br>Rehearse the demo: income/expense tracking, financial forecasting, Nova Money assistant, invoice OCR.<br>Complete the README and project documentation. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 02/07/2026 | Thursday | Final feature check and full code review across the Spring Boot backend and React frontend.<br>Write the detailed report: VPC multi-AZ architecture, ALB -> EC2 -> RDS/ElastiCache/DynamoDB flows.<br>Create the final repository and push the latest code. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 03/07/2026 | Friday | Verify the async flow: SQS -> EC2 Worker -> Lambda (Report/Invoice) -> S3.<br>Test the notification flow: Amazon SNS email alerts for budget exceeded and subscription expiry.<br>Back up RDS MySQL data, snapshot the environment and share the repository link with the instructor. | [Final Project](https://github.com/vinhpham2808/J2EE) |

### Expected Outcomes
- UI/UX polished, E2E tests passing for all core features.
- CloudWatch monitoring live, rollback scripts ready.
- Documentation, presentation slides and demo fully prepared.

### Week 11 References
- [Final Project](https://github.com/vinhpham2808/J2EE) — Money Manager (Spring Boot + React 19 + React Native Expo)
- AWS services: CloudWatch, SNS, SQS, Lambda, S3, RDS MySQL backup/snapshot
