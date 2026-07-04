---
title : "Kiểm tra kết quả & thực nghiệm"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

Em tiến hành chạy thử nghiệm thực tế để kiểm tra tính đúng đắn và hiệu năng của toàn bộ giải pháp hạ tầng đã triển khai, bao gồm định tuyến DNS riêng qua VPC Endpoints, kiểm soát quyền truy cập S3, tích hợp DynamoDB/SQS, giám sát CloudWatch và hành vi tổng thể của ứng dụng chạy trực tiếp trên backend EC2/ALB.

### Video trải nghiệm ứng dụng Web

Video dưới đây trình bày toàn bộ luồng hoạt động của ứng dụng **Web** trên hạ tầng đã triển khai: định tuyến DNS đến S3 qua endpoint riêng, xuất/tải báo cáo giao dịch tháng qua S3, trợ lý AI Nova Money với lịch sử chat lưu trên DynamoDB, xử lý giao dịch bất đồng bộ qua SQS, và dashboard giám sát CloudWatch.

{{< youtube oCs0s21PJMw >}}

> **Kiểm thử Mobile:** Video demo trên YouTube cho ứng dụng Mobile (React Native Expo) sẽ được bổ sung sau. Bên dưới là bộ ảnh chụp màn hình kiểm thử trực tiếp trên ứng dụng Mobile.

### Kiểm thử gửi request thực tế

Truy cập tên miền `botdevgroup.me` để xác nhận bản ghi DNS trỏ đúng và trang chủ Money Manager tải thành công qua hạ tầng ALB/EC2 đã triển khai.

> **Web:** [Trải nghiệm tại đây](https://botdevgroup.me)

<div align="center">

![Trang chủ Money Manager tải thành công qua tên miền botdevgroup.me](/images/5-Workshop/5.4-Validation/dns-routing-site-loaded.png?width=60pc&classes=shadow)

***Hình 25. Trang chủ Money Manager tải thành công qua tên miền botdevgroup.me***

</div>

Gửi thử tin nhắn đến trợ lý AI Nova Money để kiểm tra luồng chat hoạt động đúng và trả về gợi ý phù hợp.

<div align="center">

![Kiểm thử hội thoại với trợ lý AI Nova Money](/images/5-Workshop/5.4-Validation/nova-money-chat-test.png?width=60pc&classes=shadow)

***Hình 26. Kiểm thử hội thoại với trợ lý AI Nova Money***

</div>

Sau khi chat, truy vấn Scan trực tiếp trên bảng `chat_messages` tại DynamoDB Console để xác nhận toàn bộ 6 tin nhắn của phiên chat vừa test (`role: user/assistant`) đã được ghi nhận đúng, chứng minh luồng lưu lịch sử chat qua DynamoDB hoạt động chính xác.

<div align="center">

![Kết quả Scan bảng chat_messages trên DynamoDB xác nhận lịch sử chat đã được lưu](/images/5-Workshop/5.4-Validation/dynamodb-chat-messages-scan.png?width=60pc&classes=shadow)

***Hình 27. Kết quả Scan bảng chat_messages trên DynamoDB xác nhận lịch sử chat đã được lưu***

</div>

Thực hiện thao tác "Xuất Excel" trên trang Báo cáo để kiểm thử luồng xử lý bất đồng bộ (EC2 API đẩy job vào SQS -> Worker xử lý -> Lambda tạo file -> lưu vào S3). Trình duyệt nhận và tải về thành công tệp `report-2026-6-59ffa92d.xlsx`.

<div align="center">

![Tệp báo cáo Excel được xuất và tải về thành công sau khi xử lý qua SQS + Lambda](/images/5-Workshop/5.4-Validation/s3-export-notification.png?width=60pc&classes=shadow)

***Hình 28. Tệp báo cáo Excel được xuất và tải về thành công sau khi xử lý qua SQS + Lambda***

</div>

Mở tệp Excel vừa tải để đối chiếu dữ liệu: nội dung khớp chính xác với giao dịch "Lương tháng" (5.000.000đ, ngày 30/06/2026) đã nhập trên hệ thống.

<div align="center">

![Nội dung tệp Excel vừa export khớp đúng với dữ liệu giao dịch trên hệ thống](/images/5-Workshop/5.4-Validation/s3-exported-report-content.png?width=30pc&classes=shadow)

***Hình 29. Nội dung tệp Excel vừa export khớp đúng với dữ liệu giao dịch trên hệ thống***

</div>

### Kiểm tra log & metric qua CloudWatch

Trên CloudWatch Console, alarm `EC2ErrorAlarm` (dựa trên Metric Filter đọc log lỗi từ Log Group `/aws/ec2/moneymanager-app`) đang ở trạng thái theo dõi bình thường.

<div align="center">

![Danh sách CloudWatch Alarms, alarm EC2ErrorAlarm đang được theo dõi](/images/5-Workshop/5.4-Validation/cloudwatch-alarms-list.png?width=60pc&classes=shadow)

***Hình 30. Danh sách CloudWatch Alarms, alarm EC2ErrorAlarm đang được theo dõi***

</div>

Xem chi tiết biểu đồ metric `EC2ErrorCount` của alarm trong khoảng 3 giờ gần nhất: ngưỡng cảnh báo được cấu hình là "EC2ErrorCount >= 1 trong 1 datapoint / 5 phút". Alarm hiển thị trạng thái **Insufficient data** vì log ứng dụng trong khung giờ kiểm thử không phát sinh dòng lỗi nào (không có datapoint để tính), qua đó xác nhận Metric Filter và Alarm đã được cấu hình và hoạt động đúng, sẵn sàng chuyển sang trạng thái ALARM và gửi cảnh báo qua SNS ngay khi log ghi nhận lỗi thực tế.

<div align="center">

![Biểu đồ chi tiết metric EC2ErrorCount của alarm EC2ErrorAlarm](/images/5-Workshop/5.4-Validation/cloudwatch-alarm-detail-graph.png?width=60pc&classes=shadow)

***Hình 31. Biểu đồ chi tiết metric EC2ErrorCount của alarm EC2ErrorAlarm***

</div>

### Kiểm thử ứng dụng Mobile

Cùng bộ dữ liệu và backend đã kiểm thử ở trên, ứng dụng **Mobile** (React Native Expo) được kiểm thử trực tiếp trên thiết bị để xác nhận các luồng nghiệp vụ chính hoạt động đồng nhất với bản Web.

> **Mobile:** [Trải nghiệm tại đây](https://mobile.botdevgroup.me)<br>
> **Link dự phòng:** [Trải nghiệm tại đây](https://notvnt.github.io/BotDEV/)

{{< youtube riegCGswCls >}}

<div align="center">

![Màn hình Tổng quan trên Mobile hiển thị số dư, thu chi và biểu đồ tài chính tháng 6/2026](/images/5-Workshop/5.4-Validation/Mobile/mobile-dashboard-overview.jpg?width=22pc&classes=shadow)

***Hình 32. Màn hình Tổng quan trên Mobile hiển thị số dư, thu chi và biểu đồ tài chính***

</div>

<div align="center">

![Màn hình Thêm danh mục trên Mobile để phân loại giao dịch thu/chi](/images/5-Workshop/5.4-Validation/Mobile/mobile-add-category.jpg?width=22pc&classes=shadow)

***Hình 33. Màn hình Thêm danh mục trên Mobile để phân loại giao dịch thu/chi***

</div>

<div align="center">

![Màn hình Lịch sử chi tiêu trên Mobile với biểu đồ tổng quan và nút thêm giao dịch](/images/5-Workshop/5.4-Validation/Mobile/mobile-expense-history.jpg?width=22pc&classes=shadow)

***Hình 34. Màn hình Lịch sử chi tiêu trên Mobile với biểu đồ tổng quan và nút thêm giao dịch***

</div>

<div align="center">

![Màn hình Lịch sử thu nhập trên Mobile với biểu đồ tổng quan tương ứng](/images/5-Workshop/5.4-Validation/Mobile/mobile-income-history.jpg?width=22pc&classes=shadow)

***Hình 35. Màn hình Lịch sử thu nhập trên Mobile với biểu đồ tổng quan tương ứng***

</div>

<div align="center">

![Màn hình Lịch giao dịch theo tháng trên Mobile, đánh dấu ngày có phát sinh chi tiêu](/images/5-Workshop/5.4-Validation/Mobile/mobile-history-calendar.jpg?width=22pc&classes=shadow)

***Hình 36. Màn hình Lịch giao dịch theo tháng trên Mobile, đánh dấu ngày có phát sinh chi tiêu***

</div>

<div align="center">

![Màn hình Ngân sách trên Mobile để thiết lập hạn mức chi tiêu theo danh mục và theo tháng](/images/5-Workshop/5.4-Validation/Mobile/mobile-budget-limits.jpg?width=22pc&classes=shadow)

***Hình 37. Màn hình Ngân sách trên Mobile để thiết lập hạn mức chi tiêu theo danh mục và theo tháng***

</div>

<div align="center">

![Màn hình Dự báo trên Mobile hiển thị dự báo chi tiêu tháng tới so với trung bình lịch sử](/images/5-Workshop/5.4-Validation/Mobile/mobile-forecast.jpg?width=22pc&classes=shadow)

***Hình 38. Màn hình Dự báo trên Mobile hiển thị dự báo chi tiêu tháng tới so với trung bình lịch sử***

</div>

<div align="center">

![Màn hình chat với trợ lý AI Nova Money trên Mobile](/images/5-Workshop/5.4-Validation/Mobile/mobile-nova-money-chat.jpg?width=22pc&classes=shadow)

***Hình 39. Màn hình chat với trợ lý AI Nova Money trên Mobile***

</div>

<div align="center">

![Màn hình Tài khoản trên Mobile hiển thị thông tin người dùng và các tùy chọn quản lý tài chính](/images/5-Workshop/5.4-Validation/Mobile/mobile-settings-account.jpg?width=22pc&classes=shadow)

***Hình 40. Màn hình Tài khoản trên Mobile hiển thị thông tin người dùng và các tùy chọn quản lý tài chính***

</div>

<div align="center">

![Màn hình Cài đặt trên Mobile với các tùy chọn thông báo và đăng xuất](/images/5-Workshop/5.4-Validation/Mobile/mobile-settings-notifications.jpg?width=22pc&classes=shadow)

***Hình 41. Màn hình Cài đặt trên Mobile với các tùy chọn thông báo và đăng xuất***

</div>

Kiểm thử tính năng xuất báo cáo Excel trên Mobile: tại màn hình Lịch sử thu nhập, chọn khung thời gian "Tất cả" và xuất file `income_report_all_months.xlsx`, hệ thống hiển thị đúng bảng lựa chọn ứng dụng để mở/chia sẻ tệp.

<div align="center">

![Màn hình xuất báo cáo thu nhập trên Mobile với tệp income_report_all_months.xlsx](/images/5-Workshop/5.4-Validation/Mobile/mobile-export-income-report.png?width=22pc&classes=shadow)

***Hình 42. Màn hình xuất báo cáo thu nhập trên Mobile với tệp income_report_all_months.xlsx***

</div>

Tương tự, tại màn hình Lịch sử chi tiêu, chọn khung thời gian "Tháng này" và xuất file `expense_report_7_2026.xlsx`, xác nhận luồng xuất báo cáo chi tiêu trên Mobile hoạt động đúng.

<div align="center">

![Màn hình xuất báo cáo chi tiêu trên Mobile với tệp expense_report_7_2026.xlsx](/images/5-Workshop/5.4-Validation/Mobile/mobile-export-expense-report.png?width=22pc&classes=shadow)

***Hình 43. Màn hình xuất báo cáo chi tiêu trên Mobile với tệp expense_report_7_2026.xlsx***

</div>

Kết quả: các màn hình Tổng quan, Danh mục, Lịch sử thu/chi, Lịch, Ngân sách, Dự báo, trợ lý AI Nova Money và Tài khoản trên Mobile đều hiển thị và đồng bộ dữ liệu đúng với backend chung đã triển khai trên AWS.

### Kết quả mong đợi

Tất cả các luồng kiểm thử trên (DNS routing qua VPC Endpoint, chat AI + lưu lịch sử DynamoDB, export báo cáo bất đồng bộ qua SQS/Lambda/S3, giám sát log/metric qua CloudWatch, cùng các màn hình nghiệp vụ chính trên Mobile) đều cho kết quả đúng như thiết kế, xác nhận hạ tầng đã triển khai ở mục 5.3 hoạt động ổn định end-to-end trên cả hai nền tảng Web và Mobile.
