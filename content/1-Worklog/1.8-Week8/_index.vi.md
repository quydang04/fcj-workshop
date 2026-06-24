---
title: "Nhật ký tuần 8 - AWS Well-Architected & Thiết kế kiến trúc Money Manager"
date: 2026-04-20
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

## Tuần 8 - AWS Well-Architected & Thiết kế kiến trúc Money Manager

### Chủ đề tuần
Tìm hiểu AWS Well-Architected Framework, AWS SAM và áp dụng vào thiết kế kiến trúc cho Money Manager

### Mục tiêu tuần
- Nắm được 5 trụ cột của AWS Well-Architected Framework.
- Thiết kế kiến trúc AWS cho dự án Money Manager dựa trên các best practices.

### Lịch công việc

| Ngày | Thứ | Nội dung công việc | Lab / Dự án |
|------|-----|--------------------|-------------|
| 08/06/2026 | Thứ 2 | Tìm hiểu AWS Well-Architected Framework và 5 trụ cột chính.<br>Thực hành AWS SAM — deploy thử một ứng dụng serverless đơn giản.<br>Bắt đầu phác thảo kiến trúc AWS cho Money Manager (VPC, EC2, Aurora, ElastiCache). | [Well-Architected Labs](https://www.wellarchitectedlabs.com) |
| 09/06/2026 | Thứ 3 | Đi sâu vào các nguyên tắc Well-Architected và trade-offs thực tế.<br>Tiếp tục thực hành AWS SAM với luồng deploy serverless.<br>Thiết kế VPC layout: Public Subnet (ALB, NAT Gateway), Private Subnet (EC2, Aurora, ElastiCache). | [Well-Architected Labs](https://www.wellarchitectedlabs.com) |
| 10/06/2026 | Thứ 4 | Review lại các quyết định thiết kế theo góc nhìn 5 trụ cột.<br>Tìm hiểu thêm AWS SAM và các pattern triển khai serverless.<br>Thiết kế luồng async: SQS → EC2 Worker → Lambda → S3 cho xuất báo cáo và render hóa đơn. | [Well-Architected Labs](https://www.wellarchitectedlabs.com) |
| 11/06/2026 | Thứ 5 | Rà soát Reliability, Security và Cost Optimization trong kiến trúc Money Manager.<br>Thực hành đóng gói và deploy serverless bằng AWS SAM.<br>Thiết kế luồng AI chat: DynamoDB lưu conversation history cho Nova Money. | [Well-Architected Labs](https://www.wellarchitectedlabs.com) |
| 12/06/2026 | Thứ 6 | Tổng hợp 5 trụ cột và impact đến kiến trúc Money Manager.<br>Hoàn thành thực hành AWS SAM cơ bản.<br>Chốt kiến trúc đề xuất: multi-AZ, ALB + EC2 ASG, Aurora + RDS Proxy, ElastiCache HA, SQS + Lambda. | [Well-Architected Labs](https://www.wellarchitectedlabs.com) |

### Kết quả kỳ vọng
- Hiểu 5 trụ cột của AWS Well-Architected Framework và cách áp dụng.
- Có kinh nghiệm thực hành với AWS SAM.
- Chốt được kiến trúc AWS cho Money Manager: VPC multi-AZ, ALB, EC2 ASG, Aurora MySQL, ElastiCache, DynamoDB, SQS, Lambda, S3, SNS, CloudWatch.

### Tham chiếu tuần 8
- [Well-Architected Labs](https://www.wellarchitectedlabs.com)
- 5 trụ cột: Operational Excellence, Security, Reliability, Performance Efficiency, Cost Optimization
