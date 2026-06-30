---
title : "Các bước thực hiện chi tiết"
date : 2024-01-01
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

### Bước 1: Thiết lập mạng riêng VPC và máy chủ EC2

Quy trình xây dựng môi trường mạng cô lập và máy chủ tính toán cốt lõi:

- Khởi tạo một **VPC** có dải IP CIDR là `10.0.0.0/16` làm dải mạng riêng tư chính.
- Phân chia mạng con thành **Public Subnets** (nơi ALB và NAT Gateway cư trú để có thể tiếp xúc trực tiếp với Internet công cộng) và **Private Subnets** (nơi đặt máy chủ EC2 API và Worker để cô lập hoàn toàn khỏi Internet Gateway).
- Cấu hình các bảng định tuyến (**Route Tables**) tương ứng cho Public Subnet hướng ra ngoài Internet Gateway, và Private Subnet định tuyến outbound ra ngoài thông qua NAT Gateway đặt ở Public Subnet.
- Triển khai máy chủ EC2 kích thước `t3.micro` trong Private Subnet chạy hệ điều hành **Amazon Linux 2023**. Tiến hành cài đặt **Docker** và **Docker Compose** để quản lý và vận hành ứng dụng backend Spring Boot.
- Backend Spring Boot được chia tách thành hai container chạy độc lập: container `moneymanager-api` đảm nhận nhiệm vụ phản hồi các yêu cầu HTTP/REST API trên cổng `8080` (ALB sẽ nhận traffic HTTPS từ ngoài và chuyển tiếp về đây), và container `moneymanager-worker` chịu trách nhiệm tiêu thụ tin nhắn từ hàng đợi SQS và thực hiện các tác vụ nền định kỳ mà không mở bất kỳ cổng kết nối nào ra ngoài.
- Tệp cấu hình môi trường `/app/.env` được lưu trữ trực tiếp trên phân vùng ổ đĩa EBS của máy chủ EC2 để bảo mật thông tin và tiêm các biến môi trường trực tiếp vào các container khi khởi chạy.

### Bước 2: Cấu hình cơ sở dữ liệu RDS MySQL và ElastiCache Redis

Triển khai phân hệ lưu trữ dữ liệu quan hệ và bộ nhớ đệm tốc độ cao:

- Khởi tạo một cơ sở dữ liệu **RDS MySQL 8.0**, kích thước `db.t3.micro`. Cơ sở dữ liệu này được đặt trong một Subnet Group bao gồm các Private Subnet của VPC để ngăn chặn hoàn toàn khả năng tiếp cận từ bên ngoài.
- Nhóm bảo mật (**Security Group**) của RDS MySQL được thiết lập chế độ chặn hoàn toàn, chỉ cho phép các yêu cầu truy vấn TCP bắt nguồn từ nhóm bảo mật của máy chủ EC2 API trên cổng mặc định `3306`. Kết nối từ máy API sử dụng cơ chế **Hibernate JPA** để tự động cập nhật cấu trúc bảng dữ liệu (schema) dựa trên các thực thể Java (Entity classes).
- Khởi tạo cụm bộ nhớ đệm **ElastiCache Redis** kích thước node `cache.t3.micro` chạy trong phân vùng Private Subnet. Nhóm bảo mật của Redis được cấu hình chỉ chấp nhận các kết nối mạng nội bộ trên cổng `6379` từ EC2 API.
- Spring Boot API sử dụng Redis làm tầng cache dữ liệu đệm cho các tài nguyên ít thay đổi nhằm giảm tải truy vấn IO cho MySQL, đồng thời chạy thuật toán giới hạn tần suất (Rate Limiting) cho các cuộc hội thoại chat AI của trợ lý **Nova Money** nhằm ngăn chặn hành vi tấn công spam làm cạn kiệt API key.

### Bước 3: Tích hợp Amazon DynamoDB và AWS SQS

Thiết lập kho lưu trữ phi cấu trúc NoSQL và hệ thống hàng đợi tin nhắn điều phối sự kiện:

- Trên trang **DynamoDB Console**, khởi tạo hai bảng dữ liệu chính với chế độ năng lực theo yêu cầu (**On-Demand Capacity Mode**): bảng `chat_sessions` lưu trữ thông tin phiên trò chuyện (Partition key: `id` kiểu String) và bảng `chat_messages` lưu trữ chi tiết lịch sử tin nhắn (Partition key: `id` kiểu String).
- Gán quyền đọc/ghi DynamoDB cho EC2 thông qua **IAM Instance Profile**. Trong mã nguồn Spring Boot backend, loại bỏ thư viện kết nối MongoDB Atlas cũ, tích hợp thư viện **SDK AWS v2** cho DynamoDB, cấu hình bean `DynamoDbClient` trỏ tới vùng hạ tầng Singapore để lưu lịch sử hội thoại của trợ lý ảo Nova Money một cách nhanh chóng và tối ưu chi phí.
- Khởi tạo hàng đợi tiêu chuẩn **AWS SQS** mang tên `moneymanager-async-jobs`. Để xử lý các tin nhắn bị lỗi sau nhiều lần xử lý lại, cấu hình một hàng đợi phụ **Dead Letter Queue (DLQ)** tên là `moneymanager-async-jobs-dlq` liên kết với hàng đợi chính qua chính sách Redrive Policy thử lại tối đa 3 lần.
- Trong ứng dụng backend, khi người dùng thực hiện giao dịch tài chính lớn, container API sẽ serialize dữ liệu sự kiện thành chuỗi JSON và dùng đối tượng `SqsTemplate` đẩy sự kiện vào SQS. Container Worker sử dụng chú thích `@SqsListener` để lắng nghe SQS và thực thi xử lý bất đồng bộ các công việc như gửi mail thông báo và tính toán lại giới hạn hũ ngân sách mà không ảnh hưởng tới thời gian phản hồi API của người dùng.

### Bước 4: Thiết lập Bảo mật Amazon S3 và VPC Endpoints

Thiết lập kết nối mạng riêng tối ưu hóa độ trễ và chi phí kết nối đến S3:

- Khởi tạo **Amazon S3 Bucket** mang tên `botdevgroup-documents` ở chế độ riêng tư hoàn toàn (**Block Public Access**) và bật tính năng mã hóa dữ liệu **SSE-S3**.
- Tạo một **Gateway VPC Endpoint** cho S3 và gán vào Route Table của các Private Subnets trong VPC. Dòng định tuyến mới được tự động thêm vào sẽ hướng toàn bộ các yêu cầu từ EC2 kết nối tới S3 đi qua mạng trục nội bộ của AWS thay vì truyền qua NAT Gateway ra Internet, giúp cắt giảm 100% chi phí xử lý băng thông trên NAT Gateway đối với lưu lượng S3 và tăng tốc độ truyền tải tệp.
- Tạo một **Interface VPC Endpoint (AWS PrivateLink)** trong các Private Subnet thuộc hai Availability Zone khác nhau để đảm bảo tính dự phòng cao. Interface Endpoint này sẽ cấp phát các địa chỉ IP nội bộ riêng từ VPC.
- Cấu hình một **Inbound Resolver** trong dịch vụ DNS **Route 53** để lắng nghe yêu cầu từ mạng ngoài (văn phòng kết nối VPN) truyền tới, phân giải tên miền công cộng của S3 về địa chỉ IP nội bộ của Interface Endpoint ENIs, giúp các máy trạm tại văn phòng upload hóa đơn hay tải báo cáo qua VPN an toàn.
- Cấu hình chính sách **Endpoint Policy** tại hai VPC Endpoint vừa tạo để quy định chỉ cho phép các thao tác upload/read hướng tới duy nhất S3 Bucket của dự án Money Manager, ngăn chặn việc rò rỉ dữ liệu ra ngoài. Đồng thời, cấu hình chính sách **S3 Bucket Policy** từ chối tuyệt đối mọi yêu cầu truy xuất S3 từ bên ngoài nếu không đi qua hai VPC Endpoint hợp lệ của hệ thống.

> Xem sơ đồ kiến trúc tổng thể tại mục **5.1. Giới thiệu** để hiểu rõ hơn cách các thành phần này liên kết với nhau.
