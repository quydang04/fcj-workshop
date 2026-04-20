---
title: "Worklog Tuần 1"
date: 2026-04-20
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:
- Làm quen với chương trình thực tập First Cloud Journey và các thành viên trong nhóm.
- Thiết lập môi trường AWS và nắm vững các dịch vụ AWS nền tảng (IAM & VPC).

### Các công việc cần triển khai trong tuần này:

| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|------|-----------|---------------|------------------|---------------------|
| 2 | - Đọc toàn bộ lộ trình học 3 tháng | 20/04/2026 | 20/04/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Cài đặt AWS CLI & cấu hình môi trường |  |  |  |
|  | - Tạo tài khoản AWS (nếu chưa có) |  |  |  |
|  | - Bật MFA cho tài khoản root |  |  |  |
|  | - Thực hành: Lab 000001 – Tạo tài khoản AWS đầu tiên |  |  |  |
| 3 | - Tìm hiểu IAM: User, Group, Policy | 21/04/2026 | 21/04/2026 | [https://000002.awsstudygroup.com](https://000002.awsstudygroup.com) |
|  | - Tạo Admin Group & Admin User |  |  |  |
|  | - Hiểu nguyên tắc Least Privilege |  |  |  |
|  | - Thực hành: Lab 000002 – Quản lý truy cập với AWS IAM (Phần 1.1–2.3) |  |  |  |
| 4 | - Tìm hiểu IAM Role vs User | 22/04/2026 | 22/04/2026 | [https://000002.awsstudygroup.com](https://000002.awsstudygroup.com) |
|  | - Tạo Admin Role, OperatorUser |  |  |  |
|  | - Thực hành Switch Role trên console |  |  |  |
|  | - Thực hành: Lab 000002 (Phần 3.1–5: Role, Switch Role, Dọn dẹp) |  |  |  |
| 5 | - Tìm hiểu Amazon VPC: Subnet public/private, Route Table, IGW, NAT GW | 23/04/2026 | 23/04/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Tìm hiểu Security Group vs Network ACL |  |  |  |
|  | - Thực hành: Lab 000003 – Amazon VPC (Phần 1.1–3.6: Tạo VPC từ đầu) |  |  |  |
| 6 | - Triển khai EC2 vào VPC, kiểm tra kết nối | 24/04/2026 | 24/04/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Cấu hình NAT Gateway, Reachability Analyzer |  |  |  |
|  | - Sử dụng Session Manager (truy cập không cần SSH) |  |  |  |
|  | - Thiết lập CloudWatch Monitoring trên EC2 |  |  |  |
|  | - Thực hành: Lab 000003 (Phần 4.1–4.7) |  |  |  |
|  | - Dọn dẹp tài nguyên |  |  |  |

### Kết quả đạt được tuần 1:
- Đã tạo và bảo mật tài khoản AWS thành công với MFA được bật trên tài khoản root.
- Hiểu chiến lược AWS Free Tier và quản lý chi phí để tránh phát sinh phí ngoài ý muốn.
- Nắm vững các khái niệm cốt lõi của IAM bao gồm:
  + Users, Groups và gán Policy
  + Nguyên tắc Least Privilege (Đặc quyền tối thiểu)
  + IAM Roles và quy trình Switch Role
  + Thiết lập Admin Group / Admin User / OperatorUser
- Xây dựng hoàn chỉnh Amazon VPC từ đầu bao gồm:
  + Public và private subnets trên nhiều availability zones
  + Internet Gateway và NAT Gateway
  + Cấu hình Route Tables
  + Security Groups và Network ACLs
- Triển khai thành công EC2 instances vào VPC và kiểm tra kết nối bằng Session Manager (không cần SSH key).
- Cấu hình CloudWatch basic monitoring trên EC2 instances.
- Thực hành dọn dẹp tài nguyên để kiểm soát chi phí.
