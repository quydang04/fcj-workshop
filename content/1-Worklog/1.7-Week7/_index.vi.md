---
title: "Nhật ký tuần 7 - Khởi động dự án Money Manager & Phân tích kiến trúc"
date: 2026-04-20
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

## Tuần 7 - Khởi động dự án Money Manager & Phân tích kiến trúc

### Chủ đề tuần
Khởi động dự án cuối kỳ Money Manager — tìm hiểu source code, setup môi trường và deploy thử lên AWS

### Mục tiêu tuần
- Nắm được cấu trúc source code và kiến trúc của dự án Money Manager.
- Setup môi trường dev local và bắt đầu deploy thử các thành phần lên AWS.

### Lịch công việc

| Ngày | Thứ | Nội dung công việc | Lab / Dự án |
|------|-----|--------------------|-------------|
| 01/06/2026 | Thứ 2 | Đọc tài liệu dự án Money Manager, phân tích cấu trúc thư mục và các module chính (backend Spring Boot, frontend React, mobile React Native).<br>Setup môi trường dev: JDK 21, Maven, Node.js, Docker.<br>Chạy thử backend Spring Boot và frontend React local, hiểu luồng build & deploy. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |
| 02/06/2026 | Thứ 3 | Phân tích kiến trúc phân lớp Controller -> Service -> Repository của backend Spring Boot.<br>Tìm hiểu database schema, entity classes và cấu hình Spring Data JPA/Hibernate.<br>Hiểu cách backend kết nối với MySQL và cấu hình connection pool. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |
| 03/06/2026 | Thứ 4 | Nghiên cứu các chức năng chính: đăng nhập (JWT + Google OAuth2), quản lý thu chi, ngân sách, hũ tiết kiệm.<br>Tìm hiểu cách backend giao tiếp với database và các API endpoints.<br>Bắt đầu viết ghi chú kỹ thuật và tài liệu kiến trúc. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |
| 04/06/2026 | Thứ 5 | Deploy thử backend Spring Boot lên AWS EC2.<br>Cấu hình RDS MySQL và kết nối ứng dụng.<br>Kiểm thử các API cơ bản và xử lý lỗi ban đầu. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |
| 05/06/2026 | Thứ 6 | Tích hợp S3 để lưu trữ file (ảnh hóa đơn, báo cáo).<br>Tìm hiểu cách setup CloudFront cho phân phối static assets.<br>Kiểm thử hệ thống và rà soát performance. | [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) |

### Kết quả kỳ vọng
- Hiểu rõ kiến trúc Spring Boot và các luồng nghiệp vụ chính của Money Manager.
- Có môi trường local chạy được và deploy thử thành công lên EC2.
- Có nền tảng kỹ thuật cho các tuần phát triển tiếp theo.

### Tham chiếu tuần 7
- [Project cuối kỳ](https://github.com/vinhpham2808/J2EE) — Money Manager (Spring Boot + React 19 + React Native Expo)
- Dịch vụ AWS: EC2, RDS MySQL, S3, CloudFront
