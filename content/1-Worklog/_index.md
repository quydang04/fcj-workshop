---
title: "Worklog"
date: 2026-04-20
weight: 1
chapter: false
pre: "<b>1. </b>"
---

# Worklog

**AWS Learning Journey – Võ Đặng Phú Quý**  
**Program:** Workforce Bootcamp – First Cloud AI Journey  
**Period:** 20/04/2026 – 01/07/2026 | Monday – Friday | 5–6 hours/day  
**Reference:** [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com)

> **Legend:** ✅ Video available in playlist &nbsp;|&nbsp; ❌ Docs only (click lab link) &nbsp;|&nbsp; ⚠️ Mixed / Cleanup required

---

## Lịch học AWS | AWS Schedule

### 🗓️ Tuần chuẩn bị (Prep Week) – 20/04 → 24/04/2026

| Ngày / Date | Thứ / Day | Nội dung học / Learning Content | Lab | Link Lab | Ghi chú / Notes |
|-------------|-----------|----------------------------------|-----|----------|-----------------|
| 20/04/2026 | Thứ 2 / Mon | **Orientation & Chuẩn bị / Setup**<br/>• Đọc lộ trình 3 tháng / Read 3-month roadmap<br/>• Cài AWS CLI / Install AWS CLI<br/>• Đọc Free Tier docs<br/>• Tạo tài khoản AWS / Create AWS account<br/>• Bật MFA root account | Lab 000001 – Creating Your First AWS Account | [000001.awsstudygroup.com](https://000001.awsstudygroup.com) | ✅ Playlist Lab01 (#11-14)<br/>📌 Ngày đầu tiên chính thức / First official day |
| 21/04/2026 | Thứ 3 / Tue | **IAM – User/Group/Policy**<br/>• IAM User, Group, Policy<br/>• Tạo Admin Group & Admin User<br/>• Nguyên tắc Least Privilege<br/>• Đăng nhập IAM User (không dùng root) | Lab 000002 – Access Management with AWS IAM | [000002.awsstudygroup.com](https://000002.awsstudygroup.com) | ❌ Docs only<br/>Mục 1.1–2.3 |
| 22/04/2026 | Thứ 4 / Wed | **IAM – Role + Switch Role**<br/>• IAM Role vs User<br/>• Tạo Admin Role, OperatorUser<br/>• Switch Role trên console<br/>• Clean up IAM resources | Lab 000002 – IAM (tiếp / continued) | [000002.awsstudygroup.com](https://000002.awsstudygroup.com) | ❌ Docs only<br/>Mục 3.1–5 |
| 23/04/2026 | Thứ 5 / Thu | **Amazon VPC – Theory + Practice**<br/>• Subnet public/private, Route Table, IGW, NAT GW<br/>• Security Group vs Network ACL<br/>• Tạo VPC từ đầu / Create VPC from scratch<br/>• Enable VPC Flow Logs | Lab 000003 – Amazon VPC & Site-to-Site VPN | [000003.awsstudygroup.com](https://000003.awsstudygroup.com) | ✅ Playlist Lab03 (#28-36) |
| 24/04/2026 | Thứ 6 / Fri | **Amazon VPC – Deploy EC2 + Session Manager**<br/>• Deploy EC2 vào VPC / Deploy EC2 into VPC<br/>• NAT Gateway, Reachability Analyzer<br/>• Session Manager (SSH-less)<br/>• CloudWatch Monitoring trên EC2<br/>⚠️ Dọn tài nguyên cuối ngày | Lab 000003 – VPC (tiếp / continued) | [000003.awsstudygroup.com](https://000003.awsstudygroup.com) | ✅ Playlist Lab03 (#37-44)<br/>⚠️ Cleanup cuối ngày |

---

### 🗓️ Tuần 1 (Week 1) – 27/04 → 29/04/2026 *(30/04 & 01/05 nghỉ lễ / public holidays)*

| Ngày / Date | Thứ / Day | Nội dung học / Learning Content | Lab | Link Lab | Ghi chú / Notes |
|-------------|-----------|----------------------------------|-----|----------|-----------------|
| 27/04/2026 | Thứ 2 / Mon | **Kick-off chính thức + Review IAM & VPC**<br/>• Ôn IAM: User, Group, Role, Policy<br/>• Ôn VPC: Subnet, RT, IGW, SG<br/>• Billing Alarm $5<br/>• Chiến lược $200 credit | Lab 000001 + 000002 + 000003 – Review | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | ✅ Ôn Lab01 + Lab03 (playlist)<br/>❌ Lab002: docs |
| 28/04/2026 | Thứ 3 / Tue | **IAM nâng cao – Roles for EC2**<br/>• Instance Profile<br/>• Truy cập S3/DynamoDB từ EC2 không cần access key<br/>• IAM Cost Governance: restrict region, instance type<br/>• IAM Permission Boundaries overview | Lab 000048 – IAM Roles for EC2 | [000048.awsstudygroup.com](https://000048.awsstudygroup.com) | ✅ Playlist Lab48 (#210-216) |
| 29/04/2026 | Thứ 4 / Wed | **Amazon EC2 – Launch & Connect**<br/>• Tạo VPC + Security Group cho Linux & Windows<br/>• Launch EC2 Amazon Linux 2023 + Windows Server 2025<br/>• Kết nối SSH (Linux) và RDP (Windows)<br/>• Key Pair, Instance Type, AMI | Lab 000004 – Introduction to Amazon EC2 | [000004.awsstudygroup.com](https://000004.awsstudygroup.com) | ❌ Docs only<br/>Mục 2.1–4.2 |
| **30/04/2026** | **Thứ 5** | 🎌 **NGHỈ LỄ / HOLIDAY** | – | – | **Giải phóng miền Nam – Thống nhất đất nước** |
| **01/05/2026** | **Thứ 6** | 🎌 **NGHỈ LỄ / HOLIDAY** | – | – | **Quốc tế Lao động / International Labour Day** |

---

### 🗓️ Tuần 2 (Week 2) – 04/05 → 08/05/2026

| Ngày / Date | Thứ / Day | Nội dung học / Learning Content | Lab | Link Lab | Ghi chú / Notes |
|-------------|-----------|----------------------------------|-----|----------|-----------------|
| 04/05/2026 | Thứ 2 / Mon | **Amazon EC2 – Basic Operations**<br/>• Thay đổi Instance Type (resize)<br/>• Tạo và quản lý EBS Snapshots<br/>• Tạo Custom AMI + Launch từ Custom AMI<br/>• Khôi phục access Linux & Windows | Lab 000004 – EC2 (tiếp / continued) | [000004.awsstudygroup.com](https://000004.awsstudygroup.com) | ❌ Docs only<br/>Mục 5.1–5.6 |
| 05/05/2026 | Thứ 3 / Tue | **Amazon EC2 – Deploy Applications**<br/>• Cài LAMP Server & Node.js trên Amazon Linux 2023<br/>• Deploy Node.js app lên EC2<br/>• AWS CLI cơ bản: ec2, s3, iam<br/>• AWS Budgets: tạo budget alert | Lab 000004 (Deploy) + Lab 000011 (CLI) + Lab 000007 (Budgets) | [000011.awsstudygroup.com](https://000011.awsstudygroup.com) | ❌ Lab04, Lab11: docs<br/>✅ Lab07 Budgets playlist (#15-20)<br/>⚠️ Dọn EC2 cuối ngày |
| 06/05/2026 | Thứ 4 / Wed | **Amazon RDS – Managed Database**<br/>• VPC + SG riêng cho RDS, DB Subnet Group<br/>• Launch RDS MySQL instance<br/>• Deploy app kết nối RDS<br/>• Backup & Restore RDS snapshot | Lab 000005 – Amazon RDS | [000005.awsstudygroup.com](https://000005.awsstudygroup.com) | ✅ Playlist Lab05 (#220-228) |
| 07/05/2026 | Thứ 5 / Thu | **Amazon S3 – Static Website Hosting**<br/>• Tạo S3 bucket, cấu hình Public Access<br/>• Upload static website HTML/CSS<br/>• Bucket Policy, Versioning<br/>• Pre-signed URLs cơ bản<br/>⚠️ Dọn tài nguyên cuối tuần | Lab 000057 – Static Website Hosting with S3 | [000057.awsstudygroup.com](https://000057.awsstudygroup.com) | ✅ Playlist Lab57 (#90-102 / #137-149)<br/>⚠️ Cleanup cuối tuần |
| 08/05/2026 | Thứ 6 / Fri | **Amazon CloudWatch – Monitoring & Alerting**<br/>• Metrics, Dashboards<br/>• Alarm CPU >80% → SNS email<br/>• Log Groups + Log Insights<br/>• CloudWatch Agent trên EC2 | Lab 000008 – Monitoring with Amazon CloudWatch | [000008.awsstudygroup.com](https://000008.awsstudygroup.com) | ❌ Docs only |

---

### 🗓️ Tuần 3 (Week 3) – 11/05 → 15/05/2026

| Ngày / Date | Thứ / Day | Nội dung học / Learning Content | Lab | Link Lab | Ghi chú / Notes |
|-------------|-----------|----------------------------------|-----|----------|-----------------|
| 11/05/2026 | Thứ 2 / Mon | **EC2 Auto Scaling + Application Load Balancer**<br/>• Launch Template, Auto Scaling Group<br/>• Scaling Policies: Target Tracking<br/>• ALB + Listener Rules<br/>• Test scale-out/scale-in, Health check | Lab 000006 – Scaling Apps with EC2 Auto Scaling | [000006.awsstudygroup.com](https://000006.awsstudygroup.com) | ❌ Docs only |
| 12/05/2026 | Thứ 3 / Tue | **Amazon Route 53 – DNS Management**<br/>• Hosted Zone, Record types (A, CNAME, Alias)<br/>• Routing policies cơ bản<br/>• Hybrid DNS với VPC | Lab 000010 – Hybrid DNS with Amazon Route 53 | [000010.awsstudygroup.com](https://000010.awsstudygroup.com) | ✅ Playlist Lab10 (#45-55) |
| 13/05/2026 | Thứ 4 / Wed | **Amazon DynamoDB – NoSQL Basics**<br/>• Tạo Table, Partition Key, Sort Key<br/>• CRUD operations (console + CLI)<br/>• Global Secondary Index (GSI)<br/>• On-demand vs Provisioned capacity<br/>⚠️ Dọn tài nguyên | Lab 000060 – NoSQL with Amazon DynamoDB | [000060.awsstudygroup.com](https://000060.awsstudygroup.com) | ✅ Playlist Lab60 (#273-275)<br/>⚠️ Cleanup |
| 14/05/2026 | Thứ 5 / Thu | **Amazon CloudFront – CDN & Edge Delivery**<br/>• Distribution, Origin, Behaviors<br/>• CloudFront + S3 Static Website<br/>• HTTPS với ACM Certificate<br/>• Cache invalidation | Lab 000094 – Content Delivery with CloudFront | [000094.awsstudygroup.com](https://000094.awsstudygroup.com) | ❌ Docs only |
| 15/05/2026 | Thứ 6 / Fri | **Highly Available Web Application**<br/>• Multi-AZ: ALB + EC2 + RDS<br/>• Target Group, Listener Rules<br/>• RDS Multi-AZ deployment<br/>• Health check & failover test | Lab 000101 – Building Highly Available Web Apps | [000101.awsstudygroup.com](https://000101.awsstudygroup.com) | ❌ Docs only |

---

### 🗓️ Tuần 4 (Week 4) – 18/05 → 22/05/2026

| Ngày / Date | Thứ / Day | Nội dung học / Learning Content | Lab | Link Lab | Ghi chú / Notes |
|-------------|-----------|----------------------------------|-----|----------|-----------------|
| 18/05/2026 | Thứ 2 / Mon | **🏗️ MINI PROJECT THÁNG 1 – Phần 1**<br/>Tự dựng 3-tier architecture:<br/>• VPC (public+private subnet, 2 AZ)<br/>• ALB → EC2 chạy Node.js<br/>• RDS MySQL backend<br/>• Ghi lại điểm stuck | Tổng hợp: Lab 000003 + 000004 + 000005 + 000101 | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 🏗️ Mini Project Tháng 1 |
| 19/05/2026 | Thứ 3 / Tue | **🏗️ MINI PROJECT THÁNG 1 – Phần 2**<br/>• S3 + CloudFront cho static assets<br/>• Route 53 trỏ vào ALB<br/>• CloudWatch Dashboard<br/>• EC2 Auto Scaling<br/>⚠️ Dọn TOÀN BỘ tài nguyên | Tổng hợp: Lab 000057 + 000094 + 000010 + 000006 | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 🏗️ Mini Project<br/>⚠️ CRITICAL CLEANUP – Billing = $0 |
| 20/05/2026 | Thứ 4 / Wed | **AWS Lambda – Serverless Basics**<br/>• Function, Runtime, Handler<br/>• Triggers: S3 event, API Gateway, CloudWatch Events<br/>• Environment variables, Layers<br/>• Lambda + S3: xử lý file khi upload<br/>• Cold start & optimization | Lab 000022 – Serverless Automation with AWS Lambda | [000022.awsstudygroup.com](https://000022.awsstudygroup.com) | ✅ Playlist Lab22 (#161-170)<br/>📦 Bắt đầu Tháng 2 |
| 21/05/2026 | Thứ 5 / Thu | **AWS CloudFormation – Infrastructure as Code**<br/>• Template YAML: Parameters, Resources, Outputs<br/>• Deploy Stack: VPC + EC2 bằng IaC<br/>• Update Stack, Change Sets, Rollback<br/>• Drift Detection, Nested Stacks | Lab 000037 – IaC with AWS CloudFormation | [000037.awsstudygroup.com](https://000037.awsstudygroup.com) | ❌ Docs only |
| 22/05/2026 | Thứ 6 / Fri | **AWS Systems Manager**<br/>• Session Manager: EC2 không cần SSH key<br/>• Parameter Store: config & secrets<br/>• Run Command: lệnh hàng loạt EC2<br/>• Patch Manager, Inventory | Lab 000031 – SSM + Lab 000058 – Session Manager | [000031.awsstudygroup.com](https://000031.awsstudygroup.com) | ❌ Lab31 + Lab58: docs only |

---

### 🗓️ Tuần 5 (Week 5) – 25/05 → 29/05/2026

| Ngày / Date | Thứ / Day | Nội dung học / Learning Content | Lab | Link Lab | Ghi chú / Notes |
|-------------|-----------|----------------------------------|-----|----------|-----------------|
| 25/05/2026 | Thứ 2 / Mon | **CI/CD – AWS CodePipeline Part 1**<br/>• CodeCommit: Git repo trên AWS<br/>• CodeBuild: build & unit test<br/>• CodeDeploy: deploy lên EC2<br/>• Pipeline end-to-end | Lab 000017 – CI/CD Pipeline with AWS CodePipeline | [000017.awsstudygroup.com](https://000017.awsstudygroup.com) | ❌ Docs only |
| 26/05/2026 | Thứ 3 / Tue | **CI/CD – CodePipeline Part 2 + Review**<br/>• Blue/Green deployment với CodeDeploy<br/>• Manual Approval stage<br/>• Unit test stage trong pipeline<br/>• Rollback khi deploy fail<br/>⚠️ Dọn tài nguyên | Lab 000023 – Automated Deployments with CodePipeline | [000023.awsstudygroup.com](https://000023.awsstudygroup.com) | ❌ Docs only<br/>⚠️ Cleanup cuối tuần |
| 27/05/2026 | Thứ 4 / Wed | **AWS WAF – Web Application Firewall**<br/>• Web ACL, Rules, Rule Groups<br/>• SQL Injection, XSS protection<br/>• Rate-limiting rules<br/>• AWS Managed Rule Groups<br/>• Geo restriction | Lab 000026 – Application Protection with AWS WAF | [000026.awsstudygroup.com](https://000026.awsstudygroup.com) | ❌ Docs only |
| 28/05/2026 | Thứ 5 / Thu | **AWS KMS + Secrets Manager**<br/>• Tạo KMS key (symmetric)<br/>• Encrypt S3 + RDS với KMS<br/>• Lưu DB password vào Secrets Manager<br/>• Rotate secret tự động<br/>• Lambda đọc secret từ Secrets Manager | Lab 000033 – KMS + Lab 000096 – Secrets Manager | [000033.awsstudygroup.com](https://000033.awsstudygroup.com) | ✅ Playlist Lab33 (#191-201)<br/>❌ Lab96: docs only |
| 29/05/2026 | Thứ 6 / Fri | **AWS GuardDuty + Security Hub + VPC Endpoints**<br/>• GuardDuty: threat detection AI, Findings<br/>• Security Hub: unified security posture<br/>• VPC Endpoint cho S3 (private access)<br/>• IAM Permission Boundaries | Lab 000098 (GuardDuty) + Lab 000018 (Security Hub) + Lab 000111 (VPC Endpoints) | [000018.awsstudygroup.com](https://000018.awsstudygroup.com) | ✅ Playlist Lab18 (#158-160)<br/>❌ Lab98 + Lab111: docs only |

---

### 🗓️ Tuần 6 (Week 6) – 01/06 → 05/06/2026

| Ngày / Date | Thứ / Day | Nội dung học / Learning Content | Lab | Link Lab | Ghi chú / Notes |
|-------------|-----------|----------------------------------|-----|----------|-----------------|
| 01/06/2026 | Thứ 2 / Mon | **Amazon Cognito – User Authentication**<br/>• User Pool: đăng ký / đăng nhập<br/>• App Client, Hosted UI<br/>• JWT Token flow (Access, ID, Refresh)<br/>• Identity Pool: federated identity<br/>• Cognito Authorizer → API Gateway | Lab 000141 – Cross-Domain Auth with Amazon Cognito | [000141.awsstudygroup.com](https://000141.awsstudygroup.com) | ❌ Docs only |
| 02/06/2026 | Thứ 3 / Tue | **S3 Security Best Practices + Review Tuần 6**<br/>• Block Public Access, Bucket Policies & ACL<br/>• S3 Object Lock, MFA Delete<br/>• Pre-signed URLs (upload & download)<br/>• S3 Access Logs<br/>⚠️ Dọn tài nguyên | Lab 000069 – S3 Security Best Practices | [000069.awsstudygroup.com](https://000069.awsstudygroup.com) | ❌ Docs only<br/>⚠️ Cleanup |
| 03/06/2026 | Thứ 4 / Wed | **Amazon SQS + SNS – Messaging Systems**<br/>• SQS Standard vs FIFO Queue<br/>• Visibility Timeout, Dead Letter Queue<br/>• SNS Topics, Subscriptions<br/>• Fan-out pattern: SNS → nhiều SQS<br/>• SQS trigger Lambda | Lab 000077 – Messaging with SQS + SNS | [000077.awsstudygroup.com](https://000077.awsstudygroup.com) | ❌ Docs only |
| 04/06/2026 | Thứ 5 / Thu | **AWS Backup – Data Protection**<br/>• Backup Plan, Backup Vault<br/>• Backup EC2, RDS, EBS<br/>• Cross-region backup, Restore<br/>• RPO/RTO concepts | Lab 000013 – Data Protection with AWS Backup | [000013.awsstudygroup.com](https://000013.awsstudygroup.com) | ✅ Playlist Lab13 (#81-85 / #107-112) |
| 05/06/2026 | Thứ 6 / Fri | **VPC Peering**<br/>• Peering connection giữa 2 VPC<br/>• Route Table update cả 2 phía<br/>• Security Group cross-VPC<br/>• Transitive peering không hoạt động<br/>• Test connectivity giữa 2 VPC | Lab 000019 – Network Integration with VPC Peering | [000019.awsstudygroup.com](https://000019.awsstudygroup.com) | ✅ Playlist Lab19 (#56-64) |

---

### 🗓️ Tuần 7 (Week 7) – 08/06 → 12/06/2026

| Ngày / Date | Thứ / Day | Nội dung học / Learning Content | Lab | Link Lab | Ghi chú / Notes |
|-------------|-----------|----------------------------------|-----|----------|-----------------|
| 08/06/2026 | Thứ 2 / Mon | **AWS Transit Gateway**<br/>• Hub-and-spoke topology<br/>• Attach nhiều VPC vào TGW<br/>• TGW Route Tables<br/>• So sánh TGW vs VPC Peering<br/>⚠️ Xóa TGW NGAY sau lab (tính phí theo giờ) | Lab 000020 – Centralized Network with Transit Gateway | [000020.awsstudygroup.com](https://000020.awsstudygroup.com) | ✅ Playlist Lab20 (#65-71)<br/>⚠️ XÓA TGW NGAY – tốn phí theo giờ |
| 09/06/2026 | Thứ 3 / Tue | **Review Networking + Buffer**<br/>• Vẽ lại: VPC Peering vs Transit Gateway<br/>• Ôn tổng hợp tuần 7<br/>• Dọn sạch tài nguyên<br/>• Đọc qua Docker docs cơ bản | Review + Chuẩn bị Docker | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | ⚠️ Cleanup đặc biệt: TGW → Peering → RT → EC2 |
| 10/06/2026 | Thứ 4 / Wed | **Docker cơ bản + Amazon ECR**<br/>• Container vs VM<br/>• Dockerfile: FROM, RUN, COPY, EXPOSE, CMD<br/>• Build image, tag, run container<br/>• Docker Compose cơ bản<br/>• Push/Pull image lên Amazon ECR | Lab 000015 – Containerization with Docker | [000015.awsstudygroup.com](https://000015.awsstudygroup.com) | ❌ Docs only |
| 11/06/2026 | Thứ 5 / Thu | **Amazon ECS – Container Orchestration**<br/>• Cluster, Task Definition, Service<br/>• Launch type: EC2 vs Fargate<br/>• ECS + ECR integration<br/>• ALB với ECS Service<br/>• Rolling update, Service Auto Scaling | Lab 000016 – Container Orchestration with Amazon ECS | [000016.awsstudygroup.com](https://000016.awsstudygroup.com) | ❌ Docs only |
| 12/06/2026 | Thứ 6 / Fri | **ECS + Fargate Workshop**<br/>• Serverless containers (không quản lý EC2)<br/>• Fargate task CPU/memory sizing<br/>• Service Auto Scaling với CloudWatch<br/>• CloudWatch Container Insights<br/>• Cost: Fargate vs EC2 launch type | Lab 000067 – ECS + AWS Fargate Workshop | [000067.awsstudygroup.com](https://000067.awsstudygroup.com) | ❌ Docs only |

---

### 🗓️ Tuần 8 (Week 8) – 15/06 → 19/06/2026

| Ngày / Date | Thứ / Day | Nội dung học / Learning Content | Lab | Link Lab | Ghi chú / Notes |
|-------------|-----------|----------------------------------|-----|----------|-----------------|
| 15/06/2026 | Thứ 2 / Mon | **CI/CD cho ECS Applications**<br/>• CodePipeline: GitHub → CodeBuild → ECR → ECS<br/>• Buildspec.yml cho Docker image<br/>• Blue/Green deployment với ECS + CodeDeploy<br/>• Environment variables trong ECS task | Lab 000152 – DevOps with AWS CodePipeline (ECS) | [000152.awsstudygroup.com](https://000152.awsstudygroup.com) | ❌ Docs only |
| 16/06/2026 | Thứ 3 / Tue | **🏗️ MINI PROJECT THÁNG 2**<br/>Tự dựng: Node.js → Docker → ECR → ECS Fargate<br/>• CI/CD pipeline tự động (CodePipeline)<br/>• WAF bảo vệ ALB<br/>• Secrets Manager cho DB credentials<br/>• CloudWatch Container Insights<br/>⚠️ Dọn tài nguyên, tổng kết tháng 2 | Tổng hợp: Lab 000015+000016+000067+000152+000026+000096 | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 🏗️ Mini Project Tháng 2<br/>⚠️ Cleanup bắt buộc |
| 17/06/2026 | Thứ 4 / Wed | **Review Tháng 2 – Tổng kết + Buffer**<br/>• Vẽ lại kiến trúc Mini Project Tháng 2<br/>• Ghi lại 10 điều quan trọng nhất tháng 2<br/>• Kiểm tra billing – tổng cost 8 tuần<br/>• Ôn lại: Lambda, CloudFormation, SSM, CI/CD | Review Tháng 2 | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 📝 Review Tháng 2 |
| 18/06/2026 | Thứ 5 / Thu | **Review Security – WAF, KMS, GuardDuty, Cognito**<br/>• Ôn lại WAF rules và test SQL injection<br/>• KMS key management và encryption<br/>• GuardDuty findings review<br/>• Cognito JWT flow deep dive<br/>• S3 Security best practices recap | Review Security (Tuần 6) | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 📝 Review Security |
| 19/06/2026 | Thứ 6 / Fri | **Review Containers – Docker, ECS, Fargate, CI/CD**<br/>• Ôn Docker: Dockerfile, build, push ECR<br/>• ECS Fargate: task definition, service, ALB<br/>• CI/CD pipeline cho ECS (Blue/Green)<br/>• So sánh ECS vs Lambda | Review Containers (Tuần 8) | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 📝 Review Containers |

---

### 🗓️ Tuần 9 (Week 9) – 22/06 → 26/06/2026

| Ngày / Date | Thứ / Day | Nội dung học / Learning Content | Lab | Link Lab | Ghi chú / Notes |
|-------------|-----------|----------------------------------|-----|----------|-----------------|
| 22/06/2026 | Thứ 2 / Mon | **Buffer – Catch-up + AWS Well-Architected**<br/>• Hoàn thiện bất kỳ lab còn dang dở<br/>• Đọc AWS Well-Architected Framework (5 pillars)<br/>• Ôn lại các điểm yếu cá nhân<br/>• Chuẩn bị cho Tháng 3: Serverless + Capstone | Buffer Day – Catch-up | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 📝 Buffer / Catch-up |
| 23/06/2026 | Thứ 3 / Tue | **Chuẩn bị Capstone + AWS SAM Deep Dive**<br/>• Ôn lại kiến trúc Cloud File Storage hiện tại<br/>• Lên kế hoạch migrate: MongoDB→DynamoDB, R2→S3<br/>• AWS SAM advanced: nested stacks, layers<br/>• Thiết kế DynamoDB table schema<br/>• Thiết kế S3 folder structure | Chuẩn bị Capstone | [000060.awsstudygroup.com](https://000060.awsstudygroup.com) | 🚀 Chuẩn bị Capstone |
| 24/06/2026 | Thứ 4 / Wed | **📦 Tháng 3 – Serverless Book Store: Backend + SAM**<br/>• Lambda + DynamoDB CRUD (Lab 000078)<br/>• API Gateway REST API, CORS<br/>• Frontend React gọi API GW (Lab 000079)<br/>• AWS SAM: sam build + sam deploy (Lab 000080) | Lab 000078 + 000079 + 000080 | [000078.awsstudygroup.com](https://000078.awsstudygroup.com) | ❌ Lab78/79/80: docs only<br/>📦 Bắt đầu Tháng 3 |
| 25/06/2026 | Thứ 5 / Thu | **Serverless Book Store – Cognito + Custom Domain + SSL**<br/>• User Pool, App Client, Hosted UI (Lab 000081)<br/>• JWT verify trong Lambda + API GW Cognito Authorizer<br/>• ACM Certificate + API GW custom domain (Lab 000082)<br/>• CloudFront + Route 53 Alias + HTTPS end-to-end | Lab 000081 – Cognito Auth + Lab 000082 – Custom Domain & SSL | [000081.awsstudygroup.com](https://000081.awsstudygroup.com) | ❌ Lab81/82: docs only |
| 26/06/2026 | Thứ 6 / Fri | **Serverless Book Store – Events + CI/CD + Monitoring**<br/>• SQS order queue + SNS + DLQ (Lab 000083)<br/>• CodePipeline + SAM deploy + Lambda Canary (Lab 000084)<br/>• X-Ray trong Lambda + API GW (Lab 000085)<br/>• GraphQL AppSync: SDL, Resolvers, Subscriptions (Lab 000086) | Lab 000083+000084+000085+000086 | [000083.awsstudygroup.com](https://000083.awsstudygroup.com) | ❌ Lab83/84/85/86: docs only |

---

### 🗓️ Tuần 10 (Week 10) – 29/06 → 01/07/2026 *(Tuần cuối / Final Week)*

| Ngày / Date | Thứ / Day | Nội dung học / Learning Content | Lab | Link Lab | Ghi chú / Notes |
|-------------|-----------|----------------------------------|-----|----------|-----------------|
| 29/06/2026 | Thứ 2 / Mon | **Document Management System – Full Build**<br/>• Lambda + DynamoDB CRUD + Amplify Storage (Lab 000133–134)<br/>• API Gateway + React + SAM deploy + CloudFront (Lab 000135–137)<br/>• Search + DevOps CI/CD + X-Ray tracing (Lab 000138–140)<br/>⚠️ Dọn tài nguyên cuối ngày | Lab 000133–140 (DMS full series) | [000133.awsstudygroup.com](https://000133.awsstudygroup.com) | ❌ Lab133-140: docs only<br/>⚠️ Cleanup |
| 30/06/2026 | Thứ 3 / Tue | **🚀 CAPSTONE – Thiết kế + Build Backend**<br/>Migrate Cloud File Storage lên AWS:<br/>• MongoDB → DynamoDB \| Cloudflare R2 → Amazon S3<br/>• Lambda CRUD + S3 Pre-signed URLs (upload/download)<br/>• API Gateway REST + Cognito Authorizer + Share token<br/>• Vẽ Architecture Diagram trước khi code | Capstone: Design + Backend | [000080.awsstudygroup.com](https://000080.awsstudygroup.com) | 🚀 CAPSTONE START |
| 01/07/2026 | Thứ 4 / Wed | **🚀 CAPSTONE – Frontend + Security + Monitoring + FINAL CLEANUP**<br/>• Frontend gọi API GW, CloudFront + CodePipeline CI/CD<br/>• WAF + Secrets Manager + GuardDuty + X-Ray<br/>• CloudWatch Dashboard toàn hệ thống<br/>• Cost estimate + README + API docs + push GitHub<br/>⚠️ XÓA TOÀN BỘ tài nguyên (Billing = $0)<br/>• Update LinkedIn & CV | Capstone: Frontend + Security + Monitoring + Final Cleanup | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) | 🚀 CAPSTONE FINAL<br/>⚠️ CRITICAL CLEANUP<br/>Billing = $0 sau 24h |

---

## Ghi chú & Ngày nghỉ | Notes & Holidays

### 🗓️ Thông tin lịch học / Schedule Information

| Thông tin | Chi tiết |
|-----------|---------|
| **Bắt đầu / Start** | 20/04/2026 (Thứ 2 / Monday) |
| **Kết thúc / End** | 01/07/2026 (Thứ 4 / Wednesday) |
| **Tổng ngày học / Total days** | 51 ngày (Thứ 2–Thứ 6, không tính T7/CN/lễ) |
| **Thời lượng/ngày / Hours per day** | 5–6 giờ/ngày |
| **Tổng labs thực hành / Total labs** | ~40 labs |
| **Mục tiêu chứng chỉ / Target cert** | AWS Solutions Architect Associate (SAA-C03) |

### 🎌 Ngày nghỉ lễ / Public Holidays

| Ngày / Date | Lễ / Holiday |
|-------------|-------------|
| 30/04/2026 (Thứ 5 / Thu) | Giải phóng miền Nam – Thống nhất đất nước / Reunification Day |
| 01/05/2026 (Thứ 6 / Fri) | Quốc tế Lao động / International Labour Day |

### ⚠️ Lưu ý chi phí AWS / AWS Cost Alerts

| Dịch vụ / Service | Lưu ý / Alert |
|-------------------|---------------|
| **Transit Gateway** | ⚠️ XÓA NGAY sau lab – ~$0.05/hr/attachment |
| **NAT Gateway** | ⚠️ Xóa cuối ngày – ~$0.045/hr |
| **EC2 Instances** | ⚠️ Stop (không Terminate) sau lab nếu dùng tiếp |
| **RDS Instances** | ⚠️ Stop hoặc Delete sau lab – tính phí kể cả khi stopped (sau 7 ngày) |
| **Elastic IP** | ⚠️ Release khi không dùng – $0.005/hr khi không gắn EC2 |
| **Cleanup cuối tuần** | ✅ Kiểm tra Billing Dashboard = $0 mỗi cuối tuần |

### ▶️ Playlist YouTube

**Tên playlist:** First Cloud Journey Bootcamp 2025 – AWS Study Group  
**Tổng video:** 296 videos

| Labs có video ✅ | Video Numbers |
|-----------------|---------------|
| Lab01 | #11-14 |
| Lab03 | #28-44 |
| Lab05 | #220-228 |
| Lab07 | #15-20 |
| Lab10 | #45-55 |
| Lab13 | #81-85, #107-112 |
| Lab18 | #158-160 |
| Lab19 | #56-64 |
| Lab20 | #65-71 |
| Lab22 | #161-170 |
| Lab33 | #191-201 |
| Lab48 | #210-216 |
| Lab57 | #90-102, #137-149 |
| Lab60 | #273-275 |

### 🔗 Link quan trọng / Important Links

| Tài nguyên / Resource | Link |
|-----------------------|------|
| CloudJourney | [cloudjourney.awsstudygroup.com](https://cloudjourney.awsstudygroup.com) |
| AWS Console | [console.aws.amazon.com](https://console.aws.amazon.com) |
| Cost Explorer | [console.aws.amazon.com/cost-management](https://console.aws.amazon.com/cost-management) |
| Billing Dashboard | [console.aws.amazon.com/billing](https://console.aws.amazon.com/billing) |
| AWS Free Tier | [aws.amazon.com/free](https://aws.amazon.com/free) |
| SAA-C03 Exam Guide | [aws.amazon.com/certification/certified-solutions-architect-associate](https://aws.amazon.com/certification/certified-solutions-architect-associate) |
| AWS CLI Install | [docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) |

### 🚀 Capstone Project

**Mô tả / Description:** Migrate Cloud File Storage (MongoDB + R2 + JWT) → AWS (DynamoDB + S3 + Lambda + API GW + Cognito + CloudFront)  
**Thời gian / Timeline:** Tuần 9–10 (22/06 – 01/07/2026)
