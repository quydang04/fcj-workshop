---
title: "Nhật ký tuần 10 - Bảo mật, Testing & Tích hợp các dịch vụ AWS"
date: 2026-04-20
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

## Tuần 10 - Bảo mật, Testing & Tích hợp các dịch vụ AWS

### Chủ đề tuần
Hoàn thiện bảo mật, tích hợp các dịch vụ AWS còn lại và chạy test cho Money Manager

### Mục tiêu tuần
- Cấu hình bảo mật toàn diện cho hệ thống (IAM, Cloudflare, JWT/OAuth2).
- Tích hợp các dịch vụ async (SQS, Lambda) và chạy test đầy đủ.

### Lịch công việc

| Ngày | Thứ | Nội dung công việc | Lab / Dự án |
|------|-----|--------------------|-------------|
| 22/06/2026 | Thứ 2 | Cấu hình IAM Roles & Policies cho EC2 Web-API, Lambda, S3 trong dự án Money Manager.<br>Rà soát và hoàn thiện bảo mật ứng dụng: JWT authentication, Google OAuth2 trên Spring Boot.<br>Setup Cloudflare WAF, Rate Limit và Turnstile chống bot cho domain. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |
| 23/06/2026 | Thứ 3 | Triển khai luồng async: cấu hình SQS + Dead-Letter Queue cho các background job.<br>Setup EC2 Worker consume message từ SQS, gọi Lambda tạo báo cáo Excel và render hóa đơn PDF.<br>Cấu hình S3 bucket để lưu file output (reports, invoices). | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |
| 24/06/2026 | Thứ 4 | Viết unit test và integration test cho các API nghiệp vụ chính (thu chi, ngân sách, hũ tiết kiệm).<br>Kiểm thử luồng async end-to-end: SQS -> EC2 Worker -> Lambda -> S3.<br>Chạy load test và tối ưu performance: connection pool, cache hit rate, query optimization. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |
| 25/06/2026 | Thứ 5 | Chuẩn bị tài liệu kiến trúc hệ thống Money Manager trên AWS.<br>Mô tả chi tiết các luồng xử lý: nghiệp vụ chính, AI chat (DynamoDB), async (SQS/Lambda), notification (SNS).<br>Bắt đầu xây dựng slide thuyết trình. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |
| 26/06/2026 | Thứ 6 | Kiểm tra tích hợp PayOS (thanh toán QR) và Brevo SMTP (gửi email OTP, báo cáo) qua NAT Gateway.<br>Tối ưu chi phí AWS: review RDS MySQL, ElastiCache, EC2 ASG, Lambda usage.<br>Tổng kết tiến độ và lên kế hoạch cho tuần cuối. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |

### Kết quả kỳ vọng
- Bảo mật hệ thống hoàn thiện: IAM, Cloudflare WAF, JWT/OAuth2.
- Luồng async hoạt động: SQS -> EC2 Worker -> Lambda -> S3.
- Test coverage đủ cho các API chính và luồng xử lý quan trọng.

### Tham chiếu tuần 10
- [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) — Money Manager (Spring Boot + React 19 + React Native Expo)
- Dịch vụ AWS: IAM, SQS + DLQ, Lambda, S3, SNS, CloudWatch
- Dịch vụ bên ngoài: Cloudflare WAF, PayOS, Brevo SMTP
