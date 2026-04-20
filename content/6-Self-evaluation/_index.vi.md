---
title: "Tự đánh giá"
date: 2026-04-20
weight: 6
chapter: false
pre: "<b>6. </b>"
---

Nhìn lại quãng thời gian thực tập tại First Cloud Journey từ tháng 4 đến tháng 7 năm 2026, mình thực sự cảm thấy đây là một hành trình "lột xác" đáng nhớ. Hồi mới vào chương trình, kiến thức của mình về cloud computing mỏng lét, chủ yếu toàn lý thuyết suông học trên trường. Nhưng nhờ môi trường thực chiến và lộ trình cực kỳ rõ ràng của FCJ, mình đã có thể biến những mớ lý thuyết đó thành kỹ năng thực tế.

Công việc chính của mình xoay quanh việc tự tay build, bảo mật và deploy hạ tầng AWS từ con số không. Hàng tuần, mình phải hoàn thành một đống bài lab siêu chi tiết, tự ngồi mò mẫm fix lỗi (troubleshoot), tìm cách tối ưu chi phí (kẻo lố bill), và còn góp chút sức cho cộng đồng FCJ qua việc dịch blog hay viết docs nữa. Nói thật là nhờ vậy mà mình không chỉ cứng cáp hơn về mặt technical, mà còn rèn được cái "mindset" làm việc chuyên nghiệp của một kỹ sư cloud thực thụ.

Để nhìn lại bản thân một cách công tâm nhất, xem mình đã làm được gì và còn yếu chỗ nào, mình xin tự "chấm điểm" bản thân qua những tiêu chí dưới đây nhé:

### Điểm sáng & Những gì mình làm được

- **Lên tay hẳn với các dịch vụ lõi của AWS:** Phải nói là mình đã có cơ hội "vọc vạch" kha khá các dịch vụ của AWS. Từ mấy cái cơ bản như tạo User/Group trong IAM, setup VPC, cho đến những thứ "khoai" hơn như cấu hình Multi-AZ, Application Load Balancers (ALB), Auto Scaling, hay nối Route 53 với CloudFront. Giờ thì mình đã khá tự tin múa phím trên cả AWS Console lẫn gõ lệnh CLI rồi.
- **Kỹ năng tự bắt bệnh và fix bug:** Hồi đầu làm lab, mình cứ bám rịt lấy cái hướng dẫn, sai một ly là hoảng. Nhưng dần dần, mình học được cách tự bơi. Ví dụ lúc EC2 không ping được vào RDS, hay set nhầm luật trong Security Group, mình đã biết lôi Reachability Analyzer, soi VPC Flow Logs hay check CloudWatch để tìm tận gốc vấn đề trước khi đi cầu cứu mấy anh mentor. Cảm giác tự fix được lỗi nó "đã" gì đâu!
- **Tính tự giác và tự học:** Lộ trình 12 tuần ép mình vào một cái guồng khá căng. Mình luôn cố gắng giữ kỷ luật để nộp lab đúng hạn. Thay vì chỉ cắm đầu làm theo kiểu "học vẹt", mình bắt đầu có thói quen mò lên đọc doc chính chủ của AWS để hiểu bản chất câu chuyện. 
- **Quản lý "hầu bao" (Chi phí AWS):** Bài học xương máu là làm cloud thì tiền đi nhanh lắm. Nên mình đã luyện được thói quen làm xong lab nào là xóa sạch sẽ tài nguyên lab đó. Mình cũng tự set AWS Budgets và Billing Alarms đàng hoàng. Tự hào là suốt kỳ thực tập, mình chưa làm cháy túi AWS credits lần nào!
- **Chia sẻ kiến thức:** Chăm chỉ dịch blog AWS và viết worklog hàng tuần bằng Markdown/Hugo giúp kỹ năng viết lách của mình lên tay hẳn. Cảm giác diễn đạt một cái gì đó phức tạp thành thứ dễ hiểu cho mọi người cùng đọc mang lại cho mình rất nhiều động lực.

### Những chỗ mình thấy bản thân còn "non" và cần cố gắng thêm

Dù tự thấy bản thân tiến bộ nhiều, nhưng mình biết mình vẫn còn phải cày bừa nhiều lắm ở những mảng sau:

- **Chưa tự tin thiết kế từ đầu:** Hiện tại đưa sơ đồ là mình build được ngay, nhưng bảo mình tự thiết kế một hệ thống scalable, an toàn mà lại rẻ từ một yêu cầu nghiệp vụ trống trơn thì mình vẫn hơi "khớp". Đây là mục tiêu lớn mình cần cải thiện.
- **Cần "nâng cấp" lên Automation (IaC):** Trong kỳ thực tập đa số mình toàn click tay trên Console hoặc gõ CLI. Để theo kịp xu hướng DevOps bây giờ, mình xác định mục tiêu sắp tới là phải nhai bằng được CloudFormation hoặc Terraform để tự động hóa mọi thứ.
- **Mảng Networking nâng cao còn yếu:** Mình hiểu VPC cơ bản, nhưng động đến mấy thứ tầm cỡ doanh nghiệp như Transit Gateway, Direct Connect hay VPN phức tạp là mình vẫn lơ mơ lắm. Chắc chắn phải học thêm phần này.
- **Quản lý thời gian lúc chạy deadline:** Có những tuần bài tập trên trường ngập đầu cộng thêm bài lab FCJ khó nhằn làm mình bị rối, hay thức khuya. Mình cần học cách phân bổ thời gian thông minh hơn thay vì cứ dùng sức "cày" ngày đêm.
- **Cần năng nổ hơn khi làm việc nhóm:** Tính mình hay có kiểu gặp lỗi là tự chui vào góc ngồi mò mẫm cả buổi trời. Mình nhận ra đi làm thực tế thì cần phải biết cách đặt câu hỏi nhanh, gọn, lẹ và chia sẻ nhiều hơn trên group chung để học hỏi chéo từ mọi người. Mình sẽ cố gắng cởi mở hơn!

> ### 🚀 **(Sẽ có cập nhật thêm sau)**
