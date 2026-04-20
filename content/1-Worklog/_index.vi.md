---
title: "Worklog"
date: 2026-04-20
weight: 1
chapter: false
pre: "<b>1. </b>"
---

# Worklog

**Lộ trình học AWS – Võ Đặng Phú Quý**  
**Chương trình:** Workforce Bootcamp – First Cloud AI Journey  
**Thời gian:** 20/04/2026 – 01/07/2026 | Thứ 2 – Thứ 6 | 5–6 giờ/ngày  
**Tham khảo:** [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com)

> **Chú thích:** ✅ Có video trong playlist &nbsp;|&nbsp; ❌ Chỉ có tài liệu (click link lab) &nbsp;|&nbsp; ⚠️ Hỗn hợp / Cần dọn tài nguyên

---

*Xem nội dung đầy đủ (song ngữ) tại phiên bản tiếng Anh / See full bilingual content in English version.*

## Lịch học AWS

### 🗓️ Tuần chuẩn bị – 20/04 → 24/04/2026

| Ngày | Thứ | Nội dung học (5–6h) | Lab | Link Lab | Ghi chú |
|------|-----|----------------------|-----|----------|---------|
| 20/04/2026 | Thứ 2 | **Orientation & Chuẩn bị**<br/>• Đọc lộ trình 3 tháng<br/>• Cài AWS CLI, cấu hình môi trường<br/>• Đọc tài liệu Free Tier<br/>• Tạo tài khoản AWS<br/>• Bật MFA cho root account | Lab 000001 – Tạo tài khoản AWS đầu tiên | [000001.awsstudygroup.com](https://000001.awsstudygroup.com) | ✅ Playlist Lab01 (#11-14)<br/>📌 Ngày đầu tiên chính thức |
| 21/04/2026 | Thứ 3 | **IAM – User/Group/Policy**<br/>• IAM User, Group, Policy<br/>• Tạo Admin Group & Admin User<br/>• Nguyên tắc Least Privilege<br/>• Đăng nhập bằng IAM User | Lab 000002 – Quản lý truy cập với AWS IAM | [000002.awsstudygroup.com](https://000002.awsstudygroup.com) | ❌ Chỉ có tài liệu<br/>Mục 1.1–2.3 |
| 22/04/2026 | Thứ 4 | **IAM – Role + Switch Role**<br/>• IAM Role vs User<br/>• Tạo Admin Role, OperatorUser<br/>• Switch Role thực tế<br/>• Clean up IAM resources | Lab 000002 – IAM (tiếp) | [000002.awsstudygroup.com](https://000002.awsstudygroup.com) | ❌ Chỉ có tài liệu<br/>Mục 3.1–5 |
| 23/04/2026 | Thứ 5 | **Amazon VPC – Lý thuyết + Tạo thực tế**<br/>• Subnet public/private, Route Table, IGW, NAT GW<br/>• Security Group vs Network ACL<br/>• Tạo VPC từ đầu<br/>• Enable VPC Flow Logs | Lab 000003 – Amazon VPC & Site-to-Site VPN | [000003.awsstudygroup.com](https://000003.awsstudygroup.com) | ✅ Playlist Lab03 (#28-36) |
| 24/04/2026 | Thứ 6 | **Amazon VPC – Deploy EC2 + Session Manager**<br/>• Deploy EC2 vào VPC, test connection<br/>• NAT Gateway, Reachability Analyzer<br/>• Session Manager (SSH-less)<br/>• CloudWatch Monitoring<br/>⚠️ Dọn tài nguyên cuối ngày | Lab 000003 – VPC (tiếp) | [000003.awsstudygroup.com](https://000003.awsstudygroup.com) | ✅ Playlist Lab03 (#37-44)<br/>⚠️ Cleanup cuối ngày |

---

### 🗓️ Tuần 1 – 27/04 → 29/04/2026 *(30/04 & 01/05 nghỉ lễ)*

| Ngày | Thứ | Nội dung học (5–6h) | Lab | Link Lab | Ghi chú |
|------|-----|----------------------|-----|----------|---------|
| 27/04/2026 | Thứ 2 | **Kick-off chính thức + Review IAM & VPC**<br/>• Ôn lại IAM: User, Group, Role, Policy<br/>• Ôn lại VPC: Subnet, RT, IGW, SG<br/>• Billing Alarm $5<br/>• Chiến lược $200 credit | Lab 000001 + 000002 + 000003 – Review | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | ✅ Ôn Lab01 + Lab03<br/>❌ Lab002: tài liệu |
| 28/04/2026 | Thứ 3 | **IAM nâng cao – Roles for EC2**<br/>• Instance Profile<br/>• Truy cập S3/DynamoDB từ EC2 không cần access key<br/>• IAM Cost Governance<br/>• IAM Permission Boundaries | Lab 000048 – IAM Roles for EC2 | [000048.awsstudygroup.com](https://000048.awsstudygroup.com) | ✅ Playlist Lab48 (#210-216) |
| 29/04/2026 | Thứ 4 | **Amazon EC2 – Launch & Connect**<br/>• Tạo VPC + Security Group<br/>• Launch EC2 Amazon Linux 2023 + Windows Server 2025<br/>• SSH (Linux) và RDP (Windows)<br/>• Key Pair, Instance Type, AMI | Lab 000004 – Giới thiệu Amazon EC2 | [000004.awsstudygroup.com](https://000004.awsstudygroup.com) | ❌ Chỉ có tài liệu<br/>Mục 2.1–4.2 |
| **30/04/2026** | **Thứ 5** | 🎌 **NGHỈ LỄ** | – | – | **Giải phóng miền Nam – Thống nhất đất nước** |
| **01/05/2026** | **Thứ 6** | 🎌 **NGHỈ LỄ** | – | – | **Quốc tế Lao động** |

---

### 🗓️ Tuần 2 – 04/05 → 08/05/2026

| Ngày | Thứ | Nội dung học (5–6h) | Lab | Link Lab | Ghi chú |
|------|-----|----------------------|-----|----------|---------|
| 04/05/2026 | Thứ 2 | **Amazon EC2 – Các thao tác cơ bản**<br/>• Thay đổi Instance Type<br/>• EBS Snapshots<br/>• Custom AMI<br/>• Khôi phục access | Lab 000004 – EC2 (tiếp) | [000004.awsstudygroup.com](https://000004.awsstudygroup.com) | ❌ Chỉ có tài liệu |
| 05/05/2026 | Thứ 3 | **Amazon EC2 – Deploy ứng dụng**<br/>• LAMP Server & Node.js<br/>• Deploy Node.js app<br/>• AWS CLI cơ bản<br/>• AWS Budgets | Lab 000004 + 000011 + 000007 | [000011.awsstudygroup.com](https://000011.awsstudygroup.com) | ❌ Lab04, Lab11: tài liệu<br/>✅ Lab07 Budgets (#15-20)<br/>⚠️ Dọn EC2 cuối ngày |
| 06/05/2026 | Thứ 4 | **Amazon RDS – Cơ sở dữ liệu Managed**<br/>• VPC + SG riêng cho RDS<br/>• Launch RDS MySQL<br/>• Deploy app kết nối RDS<br/>• Backup & Restore | Lab 000005 – Amazon RDS | [000005.awsstudygroup.com](https://000005.awsstudygroup.com) | ✅ Playlist Lab05 (#220-228) |
| 07/05/2026 | Thứ 5 | **Amazon S3 – Static Website Hosting**<br/>• Tạo S3 bucket<br/>• Upload static website<br/>• Bucket Policy, Versioning<br/>• Pre-signed URLs<br/>⚠️ Dọn tài nguyên cuối tuần | Lab 000057 – Static Website Hosting với S3 | [000057.awsstudygroup.com](https://000057.awsstudygroup.com) | ✅ Playlist Lab57<br/>⚠️ Cleanup cuối tuần |
| 08/05/2026 | Thứ 6 | **Amazon CloudWatch – Monitoring & Alerting**<br/>• Metrics, Dashboards<br/>• Alarm CPU >80%<br/>• Log Groups + Log Insights<br/>• CloudWatch Agent | Lab 000008 – Giám sát với CloudWatch | [000008.awsstudygroup.com](https://000008.awsstudygroup.com) | ❌ Chỉ có tài liệu |

---

### 🗓️ Tuần 3 – 11/05 → 15/05/2026

| Ngày | Thứ | Nội dung học (5–6h) | Lab | Link Lab | Ghi chú |
|------|-----|----------------------|-----|----------|---------|
| 11/05/2026 | Thứ 2 | **EC2 Auto Scaling + Application Load Balancer**<br/>• Launch Template, ASG<br/>• Target Tracking Policy<br/>• ALB + Listener Rules<br/>• Test scale & health check | Lab 000006 – EC2 Auto Scaling | [000006.awsstudygroup.com](https://000006.awsstudygroup.com) | ❌ Chỉ có tài liệu |
| 12/05/2026 | Thứ 3 | **Amazon Route 53 – Quản lý DNS**<br/>• Hosted Zone, Record types<br/>• Routing policies cơ bản<br/>• Hybrid DNS với VPC | Lab 000010 – Hybrid DNS với Route 53 | [000010.awsstudygroup.com](https://000010.awsstudygroup.com) | ✅ Playlist Lab10 (#45-55) |
| 13/05/2026 | Thứ 4 | **Amazon DynamoDB – NoSQL cơ bản**<br/>• Tạo Table, PK, SK<br/>• CRUD (console + CLI)<br/>• Global Secondary Index<br/>• On-demand vs Provisioned<br/>⚠️ Dọn tài nguyên | Lab 000060 – NoSQL với DynamoDB | [000060.awsstudygroup.com](https://000060.awsstudygroup.com) | ✅ Playlist Lab60 (#273-275)<br/>⚠️ Cleanup |
| 14/05/2026 | Thứ 5 | **Amazon CloudFront – CDN**<br/>• Distribution, Origin, Behaviors<br/>• CloudFront + S3<br/>• HTTPS với ACM<br/>• Cache invalidation | Lab 000094 – Content Delivery với CloudFront | [000094.awsstudygroup.com](https://000094.awsstudygroup.com) | ❌ Chỉ có tài liệu |
| 15/05/2026 | Thứ 6 | **Highly Available Web Application**<br/>• Multi-AZ: ALB + EC2 + RDS<br/>• RDS Multi-AZ deployment<br/>• Health check & failover test | Lab 000101 – Xây dựng ứng dụng Web HA | [000101.awsstudygroup.com](https://000101.awsstudygroup.com) | ❌ Chỉ có tài liệu |

---

### 🗓️ Tuần 4 – 18/05 → 22/05/2026

| Ngày | Thứ | Nội dung học (5–6h) | Lab | Link Lab | Ghi chú |
|------|-----|----------------------|-----|----------|---------|
| 18/05/2026 | Thứ 2 | **🏗️ MINI PROJECT THÁNG 1 – Phần 1**<br/>Tự dựng 3-tier architecture:<br/>• VPC (public+private, 2 AZ)<br/>• ALB → EC2 Node.js<br/>• RDS MySQL | Tổng hợp: 000003+000004+000005+000101 | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 🏗️ Mini Project Tháng 1 |
| 19/05/2026 | Thứ 3 | **🏗️ MINI PROJECT THÁNG 1 – Phần 2**<br/>• S3 + CloudFront + Route 53<br/>• CloudWatch Dashboard<br/>• EC2 Auto Scaling<br/>⚠️ Dọn TOÀN BỘ tài nguyên | Tổng hợp: 000057+000094+000010+000006 | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 🏗️ Mini Project<br/>⚠️ CRITICAL CLEANUP |
| 20/05/2026 | Thứ 4 | **AWS Lambda – Serverless cơ bản**<br/>• Function, Runtime, Handler<br/>• S3 event, API GW triggers<br/>• Environment variables, Layers<br/>• Cold start & optimization | Lab 000022 – Lambda Serverless | [000022.awsstudygroup.com](https://000022.awsstudygroup.com) | ✅ Playlist Lab22 (#161-170)<br/>📦 Bắt đầu Tháng 2 |
| 21/05/2026 | Thứ 5 | **AWS CloudFormation – IaC**<br/>• Template YAML: Parameters, Resources, Outputs<br/>• Deploy VPC+EC2 stack<br/>• Update Stack, Rollback<br/>• Drift Detection | Lab 000037 – CloudFormation IaC | [000037.awsstudygroup.com](https://000037.awsstudygroup.com) | ❌ Chỉ có tài liệu |
| 22/05/2026 | Thứ 6 | **AWS Systems Manager**<br/>• Session Manager (không cần SSH)<br/>• Parameter Store: config & secrets<br/>• Run Command<br/>• Patch Manager | Lab 000031 SSM + Lab 000058 Session Manager | [000031.awsstudygroup.com](https://000031.awsstudygroup.com) | ❌ Lab31 + Lab58: tài liệu |

---

### 🗓️ Tuần 5 – 25/05 → 29/05/2026

| Ngày | Thứ | Nội dung học (5–6h) | Lab | Link Lab | Ghi chú |
|------|-----|----------------------|-----|----------|---------|
| 25/05/2026 | Thứ 2 | **CI/CD – AWS CodePipeline Phần 1**<br/>• CodeCommit, CodeBuild, CodeDeploy<br/>• Pipeline end-to-end<br/>• Trigger khi push code | Lab 000017 – CI/CD Pipeline | [000017.awsstudygroup.com](https://000017.awsstudygroup.com) | ❌ Chỉ có tài liệu |
| 26/05/2026 | Thứ 3 | **CI/CD – CodePipeline Phần 2**<br/>• Blue/Green deployment<br/>• Manual Approval stage<br/>• Rollback khi fail<br/>⚠️ Dọn tài nguyên | Lab 000023 – Automated Deployments | [000023.awsstudygroup.com](https://000023.awsstudygroup.com) | ❌ Chỉ có tài liệu<br/>⚠️ Cleanup |
| 27/05/2026 | Thứ 4 | **AWS WAF – Web Application Firewall**<br/>• Web ACL, Rules, Rule Groups<br/>• SQL Injection, XSS protection<br/>• Rate-limiting<br/>• AWS Managed Rules | Lab 000026 – AWS WAF | [000026.awsstudygroup.com](https://000026.awsstudygroup.com) | ❌ Chỉ có tài liệu |
| 28/05/2026 | Thứ 5 | **AWS KMS + Secrets Manager**<br/>• KMS key (symmetric)<br/>• Encrypt S3 + RDS<br/>• Secrets Manager: DB password<br/>• Auto rotation<br/>• Lambda đọc secret | Lab 000033 KMS + Lab 000096 Secrets Manager | [000033.awsstudygroup.com](https://000033.awsstudygroup.com) | ✅ Playlist Lab33 (#191-201)<br/>❌ Lab96: tài liệu |
| 29/05/2026 | Thứ 6 | **AWS GuardDuty + Security Hub + VPC Endpoints**<br/>• GuardDuty: threat detection<br/>• Security Hub: posture management<br/>• VPC Endpoint cho S3<br/>• IAM Permission Boundaries | Lab 000098 + 000018 + 000111 | [000018.awsstudygroup.com](https://000018.awsstudygroup.com) | ✅ Playlist Lab18 (#158-160)<br/>❌ Lab98 + Lab111: tài liệu |

---

### 🗓️ Tuần 6 – 01/06 → 05/06/2026

| Ngày | Thứ | Nội dung học (5–6h) | Lab | Link Lab | Ghi chú |
|------|-----|----------------------|-----|----------|---------|
| 01/06/2026 | Thứ 2 | **Amazon Cognito – Xác thực người dùng**<br/>• User Pool: đăng ký / đăng nhập<br/>• App Client, Hosted UI<br/>• JWT Token flow<br/>• Cognito Authorizer → API GW | Lab 000141 – Cognito Auth | [000141.awsstudygroup.com](https://000141.awsstudygroup.com) | ❌ Chỉ có tài liệu |
| 02/06/2026 | Thứ 3 | **S3 Security Best Practices**<br/>• Block Public Access, Bucket Policies<br/>• S3 Object Lock, MFA Delete<br/>• Pre-signed URLs<br/>• Access Logs<br/>⚠️ Dọn tài nguyên | Lab 000069 – S3 Security | [000069.awsstudygroup.com](https://000069.awsstudygroup.com) | ❌ Chỉ có tài liệu<br/>⚠️ Cleanup |
| 03/06/2026 | Thứ 4 | **Amazon SQS + SNS – Messaging**<br/>• SQS Standard vs FIFO<br/>• DLQ configuration<br/>• SNS Topics, Subscriptions<br/>• Fan-out pattern<br/>• SQS trigger Lambda | Lab 000077 – SQS + SNS | [000077.awsstudygroup.com](https://000077.awsstudygroup.com) | ❌ Chỉ có tài liệu |
| 04/06/2026 | Thứ 5 | **AWS Backup – Bảo vệ dữ liệu**<br/>• Backup Plan, Vault<br/>• Backup EC2, RDS, EBS<br/>• Cross-region backup, Restore<br/>• RPO/RTO | Lab 000013 – AWS Backup | [000013.awsstudygroup.com](https://000013.awsstudygroup.com) | ✅ Playlist Lab13 (#81-85 / #107-112) |
| 05/06/2026 | Thứ 6 | **VPC Peering**<br/>• Peering connection giữa 2 VPC<br/>• Route Table update cả 2 phía<br/>• Security Group cross-VPC<br/>• Test connectivity | Lab 000019 – VPC Peering | [000019.awsstudygroup.com](https://000019.awsstudygroup.com) | ✅ Playlist Lab19 (#56-64) |

---

### 🗓️ Tuần 7 – 08/06 → 12/06/2026

| Ngày | Thứ | Nội dung học (5–6h) | Lab | Link Lab | Ghi chú |
|------|-----|----------------------|-----|----------|---------|
| 08/06/2026 | Thứ 2 | **AWS Transit Gateway**<br/>• Hub-and-spoke topology<br/>• Attach nhiều VPC vào TGW<br/>• TGW Route Tables<br/>⚠️ Xóa TGW NGAY sau lab | Lab 000020 – Transit Gateway | [000020.awsstudygroup.com](https://000020.awsstudygroup.com) | ✅ Playlist Lab20 (#65-71)<br/>⚠️ XÓA TGW NGAY |
| 09/06/2026 | Thứ 3 | **Review Networking + Buffer**<br/>• VPC Peering vs Transit Gateway<br/>• Ôn tổng hợp tuần 7<br/>• Dọn sạch tài nguyên<br/>• Đọc Docker docs cơ bản | Review + Chuẩn bị Docker | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | ⚠️ Cleanup đặc biệt |
| 10/06/2026 | Thứ 4 | **Docker cơ bản + Amazon ECR**<br/>• Container vs VM<br/>• Dockerfile: FROM, RUN, COPY, EXPOSE, CMD<br/>• Build/tag/run container<br/>• Docker Compose<br/>• Push/Pull lên ECR | Lab 000015 – Docker | [000015.awsstudygroup.com](https://000015.awsstudygroup.com) | ❌ Chỉ có tài liệu |
| 11/06/2026 | Thứ 5 | **Amazon ECS – Container Orchestration**<br/>• Cluster, Task Definition, Service<br/>• EC2 vs Fargate launch type<br/>• ALB với ECS Service<br/>• Rolling update | Lab 000016 – Amazon ECS | [000016.awsstudygroup.com](https://000016.awsstudygroup.com) | ❌ Chỉ có tài liệu |
| 12/06/2026 | Thứ 6 | **ECS + Fargate Workshop**<br/>• Serverless containers<br/>• Fargate task sizing<br/>• Service Auto Scaling<br/>• Container Insights<br/>• Cost Fargate vs EC2 | Lab 000067 – ECS Fargate Workshop | [000067.awsstudygroup.com](https://000067.awsstudygroup.com) | ❌ Chỉ có tài liệu |

---

### 🗓️ Tuần 8 – 15/06 → 19/06/2026

| Ngày | Thứ | Nội dung học (5–6h) | Lab | Link Lab | Ghi chú |
|------|-----|----------------------|-----|----------|---------|
| 15/06/2026 | Thứ 2 | **CI/CD cho ECS Applications**<br/>• CodePipeline: GitHub → ECR → ECS<br/>• Buildspec.yml cho Docker<br/>• Blue/Green với ECS + CodeDeploy | Lab 000152 – DevOps CodePipeline ECS | [000152.awsstudygroup.com](https://000152.awsstudygroup.com) | ❌ Chỉ có tài liệu |
| 16/06/2026 | Thứ 3 | **🏗️ MINI PROJECT THÁNG 2**<br/>Node.js → Docker → ECR → ECS Fargate<br/>• CI/CD tự động<br/>• WAF + Secrets Manager<br/>• Container Insights<br/>⚠️ Dọn tài nguyên | Tổng hợp: 000015+000016+000067+000152+000026+000096 | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 🏗️ Mini Project Tháng 2<br/>⚠️ Cleanup bắt buộc |
| 17/06/2026 | Thứ 4 | **Review Tháng 2 – Tổng kết**<br/>• Vẽ lại kiến trúc Mini Project Tháng 2<br/>• 10 điều quan trọng nhất<br/>• Kiểm tra billing 8 tuần<br/>• Ôn: Lambda, CloudFormation, SSM, CI/CD | Review Tháng 2 | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 📝 Review Tháng 2 |
| 18/06/2026 | Thứ 5 | **Review Security**<br/>• WAF + KMS + GuardDuty + Cognito<br/>• JWT flow deep dive<br/>• S3 Security recap | Review Security | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 📝 Review Security |
| 19/06/2026 | Thứ 6 | **Review Containers**<br/>• Docker, ECS, Fargate, CI/CD<br/>• ECS vs Lambda<br/>• Tự làm lại 1 scenario | Review Containers | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 📝 Review Containers |

---

### 🗓️ Tuần 9 – 22/06 → 26/06/2026

| Ngày | Thứ | Nội dung học (5–6h) | Lab | Link Lab | Ghi chú |
|------|-----|----------------------|-----|----------|---------|
| 22/06/2026 | Thứ 2 | **Buffer – Catch-up + Well-Architected**<br/>• Hoàn thiện lab còn dang dở<br/>• AWS Well-Architected Framework (5 pillars)<br/>• Chuẩn bị Tháng 3 | Buffer / Catch-up | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 📝 Buffer |
| 23/06/2026 | Thứ 3 | **Chuẩn bị Capstone + AWS SAM**<br/>• Phân tích Cloud File Storage hiện tại<br/>• DynamoDB schema design<br/>• S3 structure design<br/>• SAM template skeleton | Chuẩn bị Capstone | [000060.awsstudygroup.com](https://000060.awsstudygroup.com) | 🚀 Chuẩn bị Capstone |
| 24/06/2026 | Thứ 4 | **📦 Tháng 3 – Serverless Book Store: Backend + SAM**<br/>• Lambda + DynamoDB CRUD<br/>• API Gateway REST, CORS<br/>• Frontend React + API GW<br/>• AWS SAM: build + deploy | Lab 000078 + 000079 + 000080 | [000078.awsstudygroup.com](https://000078.awsstudygroup.com) | ❌ Lab78/79/80: tài liệu<br/>📦 Bắt đầu Tháng 3 |
| 25/06/2026 | Thứ 5 | **Serverless Book Store – Cognito + Domain + SSL**<br/>• User Pool, Hosted UI, JWT<br/>• ACM Certificate + Custom Domain<br/>• CloudFront + Route 53 + HTTPS | Lab 000081 + 000082 | [000081.awsstudygroup.com](https://000081.awsstudygroup.com) | ❌ Lab81/82: tài liệu |
| 26/06/2026 | Thứ 6 | **Serverless Book Store – Events + CI/CD**<br/>• SQS + SNS + DLQ<br/>• CodePipeline + SAM + Canary deploy<br/>• X-Ray + AppSync GraphQL | Lab 000083+000084+000085+000086 | [000083.awsstudygroup.com](https://000083.awsstudygroup.com) | ❌ Lab83-86: tài liệu |

---

### 🗓️ Tuần 10 – 29/06 → 01/07/2026 *(Tuần cuối)*

| Ngày | Thứ | Nội dung học (5–6h) | Lab | Link Lab | Ghi chú |
|------|-----|----------------------|-----|----------|---------|
| 29/06/2026 | Thứ 2 | **Document Management System – Full Build**<br/>• Lambda CRUD + DynamoDB + Amplify (Lab 000133–134)<br/>• API GW + React + SAM + CloudFront (Lab 000135–137)<br/>• Search + CI/CD + X-Ray (Lab 000138–140)<br/>⚠️ Dọn tài nguyên | Lab 000133–140 (DMS) | [000133.awsstudygroup.com](https://000133.awsstudygroup.com) | ❌ Lab133-140: tài liệu<br/>⚠️ Cleanup |
| 30/06/2026 | Thứ 3 | **🚀 CAPSTONE – Thiết kế + Build Backend**<br/>• MongoDB → DynamoDB \| R2 → S3<br/>• Lambda CRUD + S3 Pre-signed URLs<br/>• API GW + Cognito Authorizer<br/>• Architecture Diagram | Capstone: Design + Backend | [000080.awsstudygroup.com](https://000080.awsstudygroup.com) | 🚀 CAPSTONE START |
| 01/07/2026 | Thứ 4 | **🚀 CAPSTONE – Frontend + Security + Final Cleanup**<br/>• Frontend + CloudFront + CI/CD<br/>• WAF + Secrets Manager + GuardDuty + X-Ray<br/>• CloudWatch Dashboard<br/>• README + API docs + GitHub<br/>⚠️ XÓA TOÀN BỘ tài nguyên | Capstone: Final | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 🚀 CAPSTONE FINAL<br/>⚠️ CRITICAL CLEANUP<br/>Billing = $0 sau 24h |

---

## Ghi chú & Ngày nghỉ

### 🎌 Ngày nghỉ lễ

| Ngày | Lễ |
|------|----|
| 30/04/2026 (Thứ 5) | Giải phóng miền Nam – Thống nhất đất nước |
| 01/05/2026 (Thứ 6) | Quốc tế Lao động |

### ⚠️ Lưu ý chi phí AWS

| Dịch vụ | Lưu ý |
|---------|-------|
| **Transit Gateway** | ⚠️ XÓA NGAY sau lab – ~$0.05/hr/attachment |
| **NAT Gateway** | ⚠️ Xóa cuối ngày – ~$0.045/hr |
| **EC2 Instances** | ⚠️ Stop sau lab nếu dùng tiếp |
| **RDS Instances** | ⚠️ Stop hoặc Delete – tính phí kể cả khi stopped |
| **Elastic IP** | ⚠️ Release khi không dùng – $0.005/hr |
| **Cleanup cuối tuần** | ✅ Kiểm tra Billing Dashboard = $0 mỗi cuối tuần |
