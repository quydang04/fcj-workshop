---
title: "Week 7 Worklog - Money Manager Kickoff & Architecture Analysis"
date: 2026-04-20
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

## Week 7 - Money Manager Kickoff & Architecture Analysis

### Weekly Focus
Kicking off the Money Manager final project — exploring the codebase, setting up the dev environment and first AWS deployment

### Objectives
- Understand the source code structure and architecture of the Money Manager project.
- Set up the local dev environment and start deploying components to AWS.

### Work Schedule

| Date | Day | Work Items | Lab / Project |
|------|-----|------------|---------------|
| 01/06/2026 | Monday | Read through the Money Manager docs, analyze the folder structure and main modules (Spring Boot backend, React frontend, React Native mobile).<br>Set up the dev environment: JDK 21, Maven, Node.js, Docker.<br>Run the Spring Boot backend and React frontend locally, understand the build & deploy flow. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 02/06/2026 | Tuesday | Analyze the layered architecture — Controller -> Service -> Repository in Spring Boot.<br>Explore the database schema, entity classes and Spring Data JPA/Hibernate config.<br>Understand how the backend connects to MySQL and the connection pool setup. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 03/06/2026 | Wednesday | Study the core features: login (JWT + Google OAuth2), income/expense tracking, budgets, savings jars.<br>Trace how the backend communicates with the database and the API endpoints.<br>Start writing technical notes and architecture docs. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 04/06/2026 | Thursday | Deploy the Spring Boot backend to AWS EC2 for the first time.<br>Configure RDS MySQL and connect the application.<br>Test the basic APIs and fix initial issues. | [Final Project](https://github.com/vinhpham2808/J2EE) |
| 05/06/2026 | Friday | Integrate S3 for file storage (invoice images, reports).<br>Explore CloudFront setup for static asset distribution.<br>Test the system and review performance. | [Final Project](https://github.com/vinhpham2808/J2EE) |

### Expected Outcomes
- Solid understanding of the Spring Boot architecture and main business flows in Money Manager.
- Working local environment and a successful first deployment to EC2.
- Technical foundation ready for the upcoming development weeks.

### Week 7 References
- [Final Project](https://github.com/vinhpham2808/J2EE) — Money Manager (Spring Boot + React 19 + React Native Expo)
- AWS services: EC2, RDS MySQL, S3, CloudFront
