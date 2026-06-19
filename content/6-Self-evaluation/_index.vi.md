---
title: "Tự đánh giá"
date: 2026-04-20
weight: 6
chapter: false
pre: "<b>6. </b>"
---

Sau một quãng thời gian tham gia chương trình First Cloud AI Journey, mình đã hoàn thành phần nền tảng và bắt đầu bước vào giai đoạn triển khai dự án thực tế. Đây là lúc phù hợp để dừng lại, nhìn nhận lại những gì mình đã làm được, và thẳng thắn đánh giá những điểm còn cần cải thiện.

Trong giai đoạn vừa rồi, phần lớn công việc của mình xoay quanh việc làm lab trên AWS, đọc tài liệu chính thức, ghi worklog hàng tuần và dịch một số nội dung kỹ thuật. So với lúc mới bắt đầu, mình đã bớt phụ thuộc vào hướng dẫn từng bước. Tuy nhiên, mình cũng thấy khá rõ là hiện tại mình mới vững hơn ở phần nền tảng, còn nhiều mảng vẫn cần học thêm nếu muốn làm việc độc lập hơn sau này.

### Những gì mình làm được

- **Nắm được nhóm dịch vụ AWS nền tảng ở mức thực hành:** Mình đã có cơ hội làm và hiểu rõ hơn các phần như IAM, VPC, EC2, RDS, S3, CloudWatch, Auto Scaling, Route 53, CloudFront, DynamoDB, Lambda, API Gateway và CloudFormation. Mức của mình hiện tại là có thể làm lại các bài lab, hiểu mục đích của từng thành phần và tự chỉnh một số cấu hình cơ bản khi cần.
- **Khá hơn ở việc tự kiểm tra lỗi:** Trước đây khi gặp lỗi mình thường làm lại từ đầu hoặc chờ người khác chỉ. Bây giờ mình đã quen hơn với việc kiểm tra Security Group, Route Table, IAM Policy, log trên CloudWatch, hoặc đối chiếu với tài liệu AWS trước khi hỏi. Mình chưa thể nói là troubleshoot tốt trong mọi tình huống, nhưng ít nhất đã có quy trình suy nghĩ rõ ràng hơn.
- **Có kỷ luật hơn trong việc tự học:** Lộ trình theo tuần buộc mình phải theo sát tiến độ. Nhờ vậy mình giữ được thói quen đọc trước, làm lab, ghi lại phần đã hiểu và phần còn vướng. Điều mình thấy có ích nhất là không chỉ làm cho xong, mà bắt đầu biết dừng lại để hiểu vì sao một cấu hình lại cần như vậy.
- **Có ý thức hơn về chi phí và dọn tài nguyên:** Sau một thời gian làm lab, mình hiểu rõ hơn việc tạo tài nguyên trên cloud không chỉ là chuyện kỹ thuật mà còn liên quan trực tiếp đến chi phí. Mình đã hình thành thói quen xóa tài nguyên sau khi dùng, kiểm tra các dịch vụ còn chạy và để ý hơn đến phần billing.
- **Viết và diễn đạt kỹ thuật tốt hơn trước:** Việc viết worklog bằng Markdown/Hugo và dịch blog giúp mình cải thiện cách ghi chép và trình bày vấn đề. Mình chưa viết thật gọn và sắc, nhưng đã đỡ lan man hơn và diễn đạt rõ hơn so với lúc đầu.

### Những điểm mình còn yếu

- **Chưa tự tin khi phải tự thiết kế từ yêu cầu mở:** Nếu đã có lab, sơ đồ hoặc hướng dẫn tương đối rõ thì mình làm ổn. Nhưng nếu bắt đầu từ một yêu cầu nghiệp vụ và phải tự đề xuất kiến trúc phù hợp, mình vẫn còn thiếu tự tin.
- **IaC và automation vẫn còn là khoảng trống lớn:** Dù đã chạm vào CloudFormation, phần lớn thao tác của mình vẫn đang thiên về Console và CLI. Mình cần dành thêm thời gian cho hạ tầng dạng mã để sau này làm việc bài bản hơn.
- **Kiến thức networking và security nâng cao còn mỏng:** Các phần VPC cơ bản mình theo được, nhưng những chủ đề khó hơn như hybrid networking, mô hình mạng nhiều lớp, hoặc các tình huống bảo mật phức tạp thì mình vẫn cần học thêm rất nhiều.
- **Kinh nghiệm làm một hệ thống hoàn chỉnh còn ít:** Đến thời điểm hiện tại, phần mình làm chủ yếu vẫn là từng lab hoặc từng nhóm chủ đề. Mình chưa có nhiều trải nghiệm ghép tất cả lại thành một hệ thống hoàn chỉnh có yêu cầu rõ về vận hành, kiểm thử và triển khai.
- **Quản lý thời gian chưa thật ổn ở những tuần nặng:** Có những thời điểm bài trên trường và lab dồn vào cùng lúc, mình xử lý vẫn còn bị động. Đây là điểm mình cần cải thiện nếu muốn theo được các giai đoạn dự án căng hơn ở phần sau.

### Đánh giá chung

Nếu tự đánh giá ở thời điểm hiện tại, mình nghĩ mình đã đi từ mức "biết khái niệm" sang mức "có thể tự làm, tự kiểm tra và tự học tiếp". Đó là bước tiến rõ nhất của mình trong thời gian vừa rồi.

Tuy nhiên, mình chưa xem bản thân là người đã sẵn sàng cho những bài toán kiến trúc hoặc triển khai phức tạp. Mình vẫn đang ở giai đoạn xây nền, mở rộng trải nghiệm thực hành và lấp các khoảng trống về thiết kế hệ thống, IaC, CI/CD và tư duy triển khai end-to-end. Nếu giữ được nhịp học như hiện tại, mình nghĩ phần còn lại của chương trình sẽ là lúc quan trọng để biến kiến thức rời rạc thành năng lực làm việc thực tế hơn.
