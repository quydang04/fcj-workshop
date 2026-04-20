---
title: "Worklog Tuần 4"
date: 2026-04-20
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:
- Tìm hiểu EC2 Auto Scaling, Application Load Balancer, Route 53 DNS, DynamoDB, CloudFront, và kiến trúc High Availability.

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|------|-----------|---------------|------------------|---------------------|
| 2 | - Tạo Launch Template và Auto Scaling Group | 11/05/2026 | 11/05/2026 | [https://000006.awsstudygroup.com](https://000006.awsstudygroup.com) |
|  | - Cấu hình Target Tracking Scaling Policy |  |  |  |
|  | - Thiết lập ALB + Listener Rules |  |  |  |
|  | - Kiểm tra scale-out/scale-in và health checks |  |  |  |
|  | - Thực hành: Lab 000006 – Mở rộng ứng dụng với EC2 Auto Scaling |  |  |  |
| 3 | - Tìm hiểu Route 53: Hosted Zone, Record Types (A, CNAME, Alias) | 12/05/2026 | 12/05/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Cấu hình các Routing Policies cơ bản |  |  |  |
|  | - Thiết lập Hybrid DNS với VPC |  |  |  |
|  | - Thực hành: Lab 000010 – Hybrid DNS với Amazon Route 53 |  |  |  |
| 4 | - Tạo DynamoDB Table với Partition Key & Sort Key | 13/05/2026 | 13/05/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Thực hiện các thao tác CRUD (console + CLI) |  |  |  |
|  | - Cấu hình Global Secondary Index (GSI) |  |  |  |
|  | - So sánh On-demand vs Provisioned capacity |  |  |  |
|  | - So sánh DynamoDB vs RDS |  |  |  |
|  | - Thực hành: Lab 000060 – NoSQL với Amazon DynamoDB |  |  |  |
|  | - Dọn dẹp tài nguyên |  |  |  |
| 5 | - Tìm hiểu CloudFront: Distribution, Origin, Behaviors | 14/05/2026 | 14/05/2026 | [https://000094.awsstudygroup.com](https://000094.awsstudygroup.com) |
|  | - Tích hợp CloudFront với S3 Static Website |  |  |  |
|  | - Cấu hình HTTPS với ACM Certificate |  |  |  |
|  | - Thực hiện cache invalidation |  |  |  |
|  | - Thực hành: Lab 000094 – Phân phối nội dung với CloudFront |  |  |  |
| 6 | - Thiết kế kiến trúc Multi-AZ: ALB + EC2 + RDS | 15/05/2026 | 15/05/2026 | [https://000101.awsstudygroup.com](https://000101.awsstudygroup.com) |
|  | - Cấu hình Target Groups và Listener Rules |  |  |  |
|  | - Triển khai RDS Multi-AZ |  |  |  |
|  | - Kiểm tra health check & failover |  |  |  |
|  | - Thực hành: Lab 000101 – Xây dựng ứng dụng web High Availability |  |  |  |

### Kết quả đạt được tuần 4:
- Triển khai EC2 Auto Scaling với:
  + Cấu hình Launch Template
  + Auto Scaling Group với Target Tracking policy
  + Application Load Balancer với Listener Rules
  + Xác minh hành vi scale-out và scale-in dưới tải
- Cấu hình Amazon Route 53 với Hosted Zones, nhiều loại record, và routing policies.
- Nắm vững các khái niệm cơ bản của Amazon DynamoDB:
  + Thiết kế bảng với Partition Key và Sort Key
  + Các thao tác CRUD qua cả console và CLI
  + Global Secondary Index (GSI) cho truy vấn linh hoạt
  + Hiểu mô hình giá On-demand vs Provisioned
- Triển khai Amazon CloudFront làm lớp CDN trên S3:
  + Cấu hình HTTPS sử dụng ACM Certificate
  + Quản lý cache behaviors và thực hiện invalidation
- Xây dựng hoàn chỉnh kiến trúc web 3 tầng High Availability:
  + Triển khai Multi-AZ ALB → EC2 → RDS Multi-AZ
  + Xác minh hành vi failover và health check
