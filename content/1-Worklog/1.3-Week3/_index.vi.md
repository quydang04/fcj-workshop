---
title: "Worklog Tuần 3"
date: 2026-04-20
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:
- Hoàn thành các thao tác nâng cao trên EC2: thay đổi kích thước, snapshots, AMI, triển khai ứng dụng.
- Tìm hiểu Amazon RDS, Amazon S3 static hosting, và giám sát CloudWatch.

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|------|-----------|---------------|------------------|---------------------|
| 2 | - Thay đổi Instance Type của EC2 | 04/05/2026 | 04/05/2026 | [https://000004.awsstudygroup.com](https://000004.awsstudygroup.com) |
|  | - Tạo và quản lý EBS Snapshots |  |  |  |
|  | - Tạo Custom AMI và khởi tạo instance từ AMI đó |  |  |  |
|  | - Khôi phục quyền truy cập vào instances Linux & Windows |  |  |  |
|  | - Thực hành: Lab 000004 (Phần 5.1–5.6) |  |  |  |
| 3 | - Cài đặt LAMP Server & Node.js trên Amazon Linux 2023 | 05/05/2026 | 05/05/2026 | [https://000004.awsstudygroup.com](https://000004.awsstudygroup.com) |
|  | - Triển khai ứng dụng Node.js trên EC2 (Linux & Windows) |  |  |  |
|  | - Tìm hiểu AWS CLI cơ bản: lệnh ec2, s3, iam |  |  |  |
|  | - Tạo AWS Budgets alert |  |  |  |
|  | - Thực hành: Lab 000004 (Deploy) + Lab 000011 + Lab 000007 |  |  |  |
|  | - Terminate EC2 instances cuối ngày |  |  |  |
| 4 | - Tạo VPC + Security Group cho RDS | 06/05/2026 | 06/05/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Khởi tạo RDS MySQL managed instance |  |  |  |
|  | - Triển khai ứng dụng kết nối tới RDS |  |  |  |
|  | - Backup & Restore RDS snapshot |  |  |  |
|  | - Thực hành: Lab 000005 – Amazon RDS |  |  |  |
| 5 | - Tạo S3 bucket và cấu hình Public Access | 07/05/2026 | 07/05/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Upload static website (HTML/CSS) |  |  |  |
|  | - Cấu hình Bucket Policy, Versioning |  |  |  |
|  | - Kiểm tra Pre-signed URLs |  |  |  |
|  | - Thực hành: Lab 000057 – Static Website Hosting với S3 |  |  |  |
|  | - Dọn dẹp tài nguyên cuối tuần |  |  |  |
| 6 | - Tìm hiểu CloudWatch Metrics, Dashboards | 08/05/2026 | 08/05/2026 | [https://000008.awsstudygroup.com](https://000008.awsstudygroup.com) |
|  | - Thiết lập Alarm: CPU >80% → gửi email qua SNS |  |  |  |
|  | - Cấu hình Log Groups + Log Insights |  |  |  |
|  | - Cài đặt CloudWatch Agent trên EC2 |  |  |  |
|  | - Thực hành: Lab 000008 – Giám sát với Amazon CloudWatch |  |  |  |

### Kết quả đạt được tuần 3:
- Nắm vững các thao tác nâng cao trên EC2:
  + Thay đổi instance type mà không mất dữ liệu
  + Tạo và khôi phục EBS Snapshots
  + Xây dựng và khởi tạo instances từ Custom AMI
  + Khôi phục quyền truy cập vào instances Linux & Windows bị khóa
- Triển khai đầy đủ LAMP stack và ứng dụng Node.js trên EC2.
- Sử dụng AWS CLI để quản lý tài nguyên EC2, S3 và IAM từ dòng lệnh.
- Thiết lập AWS Budgets với thông báo cảnh báo chi phí.
- Khởi tạo và cấu hình Amazon RDS MySQL managed instance:
  + DB Subnet Group, nhận biết Multi-AZ
  + Kết nối ứng dụng tới RDS endpoint
  + Thực hiện backup và restore snapshot
- Lưu trữ static website trên Amazon S3 với:
  + Bucket Policy cho public access
  + Bật tính năng Versioning
  + Pre-signed URLs cho truy cập bảo mật
- Cấu hình giám sát Amazon CloudWatch bao gồm CPU alarms, SNS email alerts, Log Groups, và CloudWatch Agent.
