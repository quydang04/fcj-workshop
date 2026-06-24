---
title: "Nhật ký tuần 9 - Phát triển Money Manager & Deploy lên AWS"
date: 2026-04-20
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

## Tuần 9 - Phát triển Money Manager & Deploy lên AWS

### Chủ đề tuần
Phát triển các chức năng chính của Money Manager và triển khai lên AWS theo kiến trúc đã thiết kế

### Mục tiêu tuần
- Phát triển các feature chính của Money Manager (backend + frontend).
- Deploy lên AWS theo kiến trúc multi-AZ đã thiết kế ở tuần 8.

### Lịch công việc

| Ngày | Thứ | Nội dung công việc | Lab / Dự án |
|------|-----|--------------------|-------------|
| 15/06/2026 | Thứ 2 | Review lại source code và xác định thứ tự ưu tiên triển khai các module.<br>Đảm bảo môi trường dev ổn định (Spring Boot backend, React frontend).<br>Rà soát lại quy trình build & deploy trước khi bắt đầu code feature mới. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |
| 16/06/2026 | Thứ 3 | Phát triển các API nghiệp vụ chính: quản lý thu chi, ngân sách, hũ tiết kiệm.<br>Kiểm tra lại entity mappings, quan hệ giữa các bảng và luồng truy cập dữ liệu.<br>Test local và đảm bảo các API hoạt động đúng với MySQL. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |
| 17/06/2026 | Thứ 4 | Hoàn thiện chức năng authentication: JWT token + Google OAuth2.<br>Phát triển các API cho phân quyền theo gói đăng ký (Free/Premium).<br>Cập nhật tài liệu kỹ thuật và API documentation. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |
| 18/06/2026 | Thứ 5 | Deploy backend Spring Boot lên EC2 trong Private Subnet.<br>Cấu hình ALB trong Public Subnet để route traffic đến EC2.<br>Setup Auto Scaling Group cho EC2 Web-API để tự động scale theo tải. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |
| 19/06/2026 | Thứ 6 | Cấu hình Aurora MySQL thay thế RDS MySQL đơn lẻ, setup multi-AZ.<br>Thiết lập RDS Proxy để quản lý connection pool.<br>Cấu hình ElastiCache Redis cho cache và session, kiểm thử kết nối từ EC2. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |

### Kết quả kỳ vọng
- Có các API nghiệp vụ chính hoạt động (quản lý thu chi, authentication, phân quyền).
- Backend đã deploy trên EC2 với ALB + Auto Scaling Group.
- Aurora MySQL và ElastiCache Redis đã cấu hình và kết nối thành công.

### Tham chiếu tuần 9
- [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) — Money Manager (Spring Boot + React 19 + React Native Expo)
- Dịch vụ AWS: EC2 ASG, ALB, Aurora MySQL, RDS Proxy, ElastiCache Redis
