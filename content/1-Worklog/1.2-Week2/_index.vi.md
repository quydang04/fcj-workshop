---
title: "Worklog Tuần 2"
date: 2026-04-20
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

> **Lưu ý:** 30/04 (Ngày Giải phóng) và 01/05 (Ngày Quốc tế Lao động) là ngày nghỉ lễ — tuần này chỉ có 3 ngày làm việc.

### Mục tiêu tuần 2:
- Ôn tập và củng cố kiến thức IAM & VPC từ Tuần 1.
- Tìm hiểu sâu về IAM Roles cho EC2 và các thao tác cơ bản trên Amazon EC2.

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|------|-----------|---------------|------------------|---------------------|
| 2 | - Ôn tập IAM: User, Group, Role, Policy | 27/04/2026 | 27/04/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Ôn tập VPC: Subnet, Route Table, IGW, Security Group |  |  |  |
|  | - Thiết lập Billing Alarm ($5) và chiến lược credit |  |  |  |
|  | - Thực hành: Lab 000001 + 000002 + 000003 – Ôn tập |  |  |  |
| 3 | - Tìm hiểu IAM Roles cho EC2 (Instance Profile) | 28/04/2026 | 28/04/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Truy cập S3/DynamoDB từ EC2 không cần access keys |  |  |  |
|  | - IAM Cost Governance: giới hạn region & instance type |  |  |  |
|  | - Tổng quan IAM Permission Boundaries |  |  |  |
|  | - Thực hành: Lab 000048 – IAM Roles cho EC2 |  |  |  |
| 4 | - Tạo VPC + Security Groups cho Linux & Windows EC2 | 29/04/2026 | 29/04/2026 | [https://000004.awsstudygroup.com](https://000004.awsstudygroup.com) |
|  | - Khởi tạo Amazon Linux 2023 & Windows Server 2025 |  |  |  |
|  | - Kết nối qua SSH (Linux) và RDP (Windows) |  |  |  |
|  | - Tìm hiểu Key Pair, Instance Types, AMI |  |  |  |
|  | - Thực hành: Lab 000004 – Giới thiệu Amazon EC2 |  |  |  |

### Kết quả đạt được tuần 2:
- Củng cố hiểu biết về kiến trúc IAM và VPC thông qua thực hành ôn tập.
- Cấu hình Billing Alarm và nắm được chiến lược quản lý $200 credit để kiểm soát chi phí.
- Nắm vững IAM Roles cho EC2 thông qua Instance Profiles:
  + Gắn roles vào EC2 để truy cập S3 và DynamoDB mà không cần static access keys
  + Cấu hình IAM policies để giới hạn theo region và instance type
- Khởi tạo thành công cả EC2 instances Linux (Amazon Linux 2023) và Windows (Server 2025):
  + Kết nối tới Linux qua SSH sử dụng Key Pair
  + Kết nối tới Windows qua RDP
- Hiểu mối quan hệ giữa AMI, Instance Type, Key Pair và Security Groups.
