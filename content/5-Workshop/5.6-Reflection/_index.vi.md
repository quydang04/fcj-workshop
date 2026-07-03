---
title : "Khó khăn & hướng phát triển"
date : 2024-01-01
weight : 6
chapter : false
pre : " <b> 5.6. </b> "
---

Phần này ghi lại những khó khăn thực tế gặp phải khi triển khai từng bước hạ tầng Money Manager tại mục **5.3** (VPC/EC2, RDS/ElastiCache, DynamoDB/SQS, S3/VPC Endpoints, CloudWatch), đối chiếu với kiến trúc High Availability đã đề xuất ở phần **2**, cách em xử lý và hướng phát triển tiếp theo.

### Khó khăn gặp phải

- **EC2 đơn lẻ thay vì Auto Scaling Group đa AZ:** Bản đề xuất ở phần 2, mục 4 đặt mục tiêu High Availability bằng EC2 + Auto Scaling Group trải trên 2 Availability Zone. Trong khung thời gian workshop, em mới dừng lại ở một EC2 `t3.micro` đơn lẻ chạy hai container `moneymanager-api`/`moneymanager-worker` (Bước 1, mục 5.3) — chưa kịp dựng Launch Template, Target Group cho ALB và Auto Scaling Policy vì cần thêm thời gian kiểm thử health check trước khi nhân bản instance.
- **Nhầm lẫn giữa Gateway Endpoint và Interface Endpoint cho S3:** Ban đầu em nghĩ chỉ cần một loại VPC Endpoint là đủ. Sau khi đọc kỹ tài liệu mới hiểu Gateway Endpoint miễn phí nhưng chỉ dùng được cho traffic nội bộ VPC, còn Interface Endpoint (PrivateLink) mất phí theo giờ nhưng cấp IP riêng và cho phép truy cập từ VPN/on-prem qua Route 53 Resolver. Vì Bước 4 (mục 5.3) yêu cầu cả EC2 trong VPC lẫn máy trạm văn phòng qua VPN đều truy cập được S3, cuối cùng phải dùng kết hợp cả hai loại.
- **Endpoint Policy và S3 Bucket Policy xung đột nhau:** Lúc mới thiết lập, em cấu hình Bucket Policy chặn toàn bộ truy cập không qua VPC Endpoint trước khi gán đúng Resource ARN của bucket vào Endpoint Policy, dẫn đến việc chính EC2 API cũng bị `Access Denied` khi gọi S3. Phải rà lại từng bước, test bằng `aws s3 cp` trực tiếp từ EC2 mới phát hiện ra lỗi thứ tự cấu hình.
- **Route 53 Resolver Inbound Endpoint là phần hoàn toàn mới:** Trước đó em chỉ quen dùng Route 53 cho public DNS record thông thường, chưa từng cấu hình DNS resolver nội bộ để văn phòng qua VPN phân giải được tên miền S3 về IP của Interface Endpoint. Đây là phần mất nhiều thời gian tìm hiểu nhất trong toàn bộ Bước 4.
- **Chuyển từ MongoDB Atlas sang DynamoDB và thiết kế lại hàng đợi SQS:** Khi thực hiện Bước 3 (mục 5.3), việc gỡ bỏ thư viện MongoDB Atlas cũ và thiết kế lại Partition Key cho hai bảng `chat_sessions`/`chat_messages` bằng SDK AWS v2 tốn khá nhiều thời gian thử-sai. Cấu hình Redrive Policy cho DLQ `moneymanager-async-jobs-dlq` (tối đa 3 lần thử lại) cũng phải điều chỉnh vài lần vì số lần retry mặc định quá thấp khiến job hợp lệ bị đẩy sang DLQ oan.

### Cách giải quyết

- Đối chiếu kiến trúc đề xuất ở phần 2 với những gì có thể hoàn thành trong khung thời gian workshop: ưu tiên dựng đúng luồng dữ liệu chính (VPC, EC2 chạy container, RDS/Redis, DynamoDB/SQS, S3/VPC Endpoint, CloudWatch) trước, còn phần Auto Scaling Group/ALB đa AZ được ghi nhận là hạng mục còn thiếu để bổ sung sau, thay vì cố làm toàn bộ cùng lúc mà không phần nào xong triệt để.
- Đọc lại tài liệu chính thức của AWS về VPC Endpoints và Route 53 Resolver, so sánh Gateway vs Interface Endpoint bằng bảng để chọn đúng loại cho từng luồng traffic.
- Kiểm thử từng bước nhỏ thay vì cấu hình hết một lần: tạo Gateway Endpoint trước, test truy cập từ EC2 bằng CLI (`aws s3 cp`, `aws dynamodb scan`, `aws sqs receive-message`), sau đó mới thêm Interface Endpoint và Endpoint Policy, test lại sau mỗi thay đổi để dễ khoanh vùng lỗi.
- Khi gặp lỗi quyền truy cập, xem CloudWatch Logs và VPC Flow Logs để xác định request bị chặn ở tầng nào (Security Group, Bucket Policy hay Endpoint Policy) thay vì đoán mò.

### Hướng phát triển trong tương lai

- Bổ sung Auto Scaling Group và Application Load Balancer đa AZ đúng như kiến trúc High Availability đã đề xuất ở phần 2, mục 4, thay cho EC2 đơn lẻ hiện tại.
- Áp dụng Reserved Instances cho các thành phần chạy ổn định (EC2, RDS, ElastiCache) như hướng tối ưu chi phí đã nêu ở phần 2, mục 8 (đánh giá rủi ro).
- Chuyển toàn bộ hạ tầng (VPC, Endpoint, Route Table, Bucket Policy...) hiện đang thao tác tay trên Console sang Infrastructure as Code (CloudFormation hoặc Terraform) để dễ tái tạo, review và version control.
- Mở rộng thêm Gateway/Interface Endpoint cho các dịch vụ khác đang gọi qua NAT Gateway (DynamoDB, SQS) để giảm tiếp chi phí NAT Gateway và tăng bảo mật đường truyền.
- Gộp các CloudWatch Alarm và Log Group hiện đang xem rời rạc thành một Dashboard tổng hợp duy nhất để giám sát nhanh hơn khi hệ thống có sự cố.
- Thực hiện test recovery/failover cho RDS multi-AZ và ElastiCache HA đúng như kế hoạch Tuần 12 đã đặt ra ở phần 2, mục 6 — phần này chưa kịp kiểm thử trong phạm vi workshop.
