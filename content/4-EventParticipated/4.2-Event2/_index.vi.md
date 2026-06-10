---
title: "Event 2 - AWS Vietnam Community Day 2026"
date: 2026-04-20
weight: 2
chapter: false
pre: "<b>4.2. </b>"
---

## Event 2 - AWS Vietnam Community Day 2026

Trang này tổng hợp nội dung các bài chia sẻ tại **AWS Vietnam Community Day 2026**, bao gồm
thiết kế context AI, hạ tầng edge, kinh nghiệm hackathon, độ tin cậy của LLM,
và hệ thống multi-agent cấp doanh nghiệp.

---

### Trọng tâm chung

> AI không chỉ là công cụ demo. AI cần có bối cảnh, kiến trúc và quy trình triển khai rõ ràng.

- AWS đóng vai trò nền tảng cho hạ tầng, bảo mật, vận hành và mở rộng hệ thống AI
- Các bài chia sẻ đều nhấn mạnh tính thực tế: từ prompt, hackathon, CloudFront đến enterprise-grade multi-agent

---

### 1. Giới thiệu

AWS Vietnam Community Day 2026 quy tụ các chuyên gia chia sẻ kinh nghiệm thực tế trong việc xây dựng
hệ thống AI và cloud trên AWS. Các chủ đề trải rộng từ năng suất cá nhân với AI, công cụ trợ lý
doanh nghiệp, hạ tầng CDN, phát triển sản phẩm trong hackathon, vấn đề độ tin cậy của LLM,
đến hệ thống chấm điểm tín dụng multi-agent cấp enterprise.

---

### 2. Tóm tắt các bài chia sẻ

#### 2.1 Tinh Truong - Build Second Brain

Bài chia sẻ tập trung vào cách làm việc hiệu quả với AI thông qua **quản lý context**.
Diễn giả nhấn mạnh rằng các AI model hiện nay đã rất mạnh, nhưng kết quả vẫn thường kém
vì người dùng hoặc không cung cấp đủ bối cảnh, hoặc đưa vào những bối cảnh sai trọng tâm.

**Một context tốt cần có:**

- Mục tiêu cần đạt được
- Tình huống hiện tại
- Ràng buộc kỹ thuật
- Bằng chứng hoặc dữ liệu liên quan

**Sai lầm phổ biến:**

- Đưa quá nhiều tài liệu không chọn lọc
- Sao chép nguyên các file dài
- Chỉ nêu lại những điều hiển nhiên mà AI đã biết

**Nguyên tắc cốt lõi:**

> Context quality quan trọng hơn context quantity.

**Khái niệm Second AI Brain:**

Đây là hệ thống tổ chức tri thức cá nhân, giúp bạn nhớ lại dự án và truy xuất đúng thông tin
trước khi đặt câu hỏi cho AI.

**Bài học rút ra:** Người dùng AI giỏi là người biết chuyển một yêu cầu mơ hồ thành
một task có mục tiêu, dữ liệu và output rõ ràng.

---

#### 2.2 Phạm Nguyễn Hải Anh - Friendly AI Assistant with Amazon Quick Suite

Bài trình bày đề cập đến các khó khăn phổ biến của business users và PM: quản lý quá nhiều tài liệu,
cuộc họp, email, dữ liệu và các tác vụ lặp lại. **Amazon Quick Suite** được giới thiệu như một
AI assistant xây dựng trên Bedrock, web search và dữ liệu nội bộ để tối ưu những workflow này.

**Amazon Quick Suite hỗ trợ:**

- Chat và Q&A thông minh
- Research và intelligent search
- Dashboard BI
- Workflow automation
- Nhúng API vào workflow doanh nghiệp
- Nền tảng: Amazon Bedrock + Web Search + Dữ liệu nội bộ

**Use case minh họa:**

Một AI PM assistant có thể tự động tạo Meeting Minutes (MoM),
gửi email cho stakeholders và lên lịch cho cuộc họp tiếp theo.

**Giá trị chính:**

- Giảm thời gian dành cho các tác vụ lặp lại và việc thu thập thông tin
- Giúp người dùng tập trung hơn vào quyết định và phối hợp nhóm

**Bài học rút ra:** AI tạo ra giá trị lớn nhất khi được đặt đúng vào workflow,
hiểu dữ liệu nội bộ và hỗ trợ hành động tiếp theo.

---

#### 2.3 Nguyễn Tuấn Thịnh - From Edge To Origin: CloudFront as Your Foundation

Bài chia sẻ tập trung vào **Amazon CloudFront** như một lớp nền tảng hoàn chỉnh từ edge đến origin,
bao quát chi phí, bảo mật, hiệu năng và reliability ở quy mô lớn.

**Mô hình chi phí:**

- Gói giá cố định bao gồm CDN, WAF, DDoS, DNS và logging
- Mức giá dễ dự đoán, phù hợp với small website owners, business users và scaling businesses
- Xử lý được traffic spike mà không gây bùng nổ chi phí bất ngờ

**Các tính năng bảo mật:**

| Tính năng | Mô tả |
|-----------|------|
| DDoS Protection | Bảo vệ trước các cuộc tấn công lưu lượng lớn |
| WAF | Web Application Firewall |
| DNS | Tích hợp với Route 53 |
| TLS / mTLS | TLS miễn phí cùng mutual TLS cho kết nối mã hóa |
| Signed URL | Phân phối nội dung có xác thực |
| Origin Cloaking | Ẩn origin server khỏi truy cập công khai |

**Tối ưu hiệu năng:**

- Multi-layer caching tại edge để giảm tải origin và tối ưu băng thông
- Hỗ trợ HTTP/3
- Compression
- Persistent connections để giảm tải origin
- Edge functions cho các logic yêu cầu độ trễ thấp

**Các yếu tố reliability:**

- Phục vụ stale content khi origin gặp sự cố
- Origin failover
- Intelligent routing

**Bài học rút ra:** CloudFront không chỉ là một CDN. Đây là lớp foundation cho tối ưu chi phí,
bảo mật, hiệu năng và khả năng chịu lỗi.

---

#### 2.4 Team VIB - 36 Giờ với LotusHacks: Xây dựng UTMorpho từ Ý tưởng đến Hiện thực

Team VIB chia sẻ câu chuyện thực tế khi tham gia **hackathon LotusHacks** trong 36 giờ,
từ chỗ chưa có ý tưởng đến lúc hoàn thành demo hoạt động của **UTMorpho**.

**UTMorpho làm gì:**

Người dùng có thể chụp ảnh, vẽ hoặc tải lên bản phác thảo UI, sau đó AI sẽ tạo giao diện web từ đầu vào đó.

**Kiến trúc sử dụng:**

```text
CloudFront -> API Gateway -> Lambda -> Bedrock -> S3 / DynamoDB
```

**Pipeline AI agent:**

1. **Vision Analyst** - Phân tích bản phác thảo đầu vào
2. **UI Designer** - Chuyển thành design specification
3. **Coder** - Sinh ra mã nguồn thực tế

**Những thách thức chính:**

- Giới hạn token từ context window của LLM
- AI overgeneration tạo ra output nhiễu
- Áp lực thời gian pitch
- Scope creep do có quá nhiều ý tưởng

**Bài học rút ra:** Real frustration tạo ra real ideas. Hackathon đòi hỏi teamwork tốt,
kiểm soát phạm vi chặt và tập trung vào một trải nghiệm cốt lõi thực sự hữu ích.

---

#### 2.5 Đào Đức - Non-Determinism of "Deterministic" LLM Settings

Bài trình bày này trả lời một câu hỏi kỹ thuật quan trọng: **Vì sao LLM vẫn có thể cho ra kết quả khác nhau
ngay cả khi đặt `temperature=0`?** Đây là vấn đề rất đáng lưu ý với các hệ thống có mức độ rủi ro cao
như legal, financial hoặc medical information retrieval.

**Cách LLM sinh token:**

- Logit computation -> Softmax -> Sampling
- `temperature` chỉ điều chỉnh phân phối xác suất, chứ không loại bỏ hoàn toàn nguồn gốc của non-determinism

**Các thử nghiệm đã thực hiện:**

- **5 model được kiểm thử:** GPT-3.5, GPT-4o, Llama-3 70B, Llama-3 8B, Mixtral 8x7B
- **8 tác vụ x 10 lần chạy** cho mỗi model; kết quả cho thấy độ chính xác dao động đáng kể giữa các lần chạy giống hệt nhau

**Nguyên nhân kỹ thuật:**

| Nguyên nhân | Giải thích |
|-------------|------------|
| Floating-point arithmetic | Các phép tính trên GPU không hoàn toàn deterministic |
| Parallel execution order | Thứ tự scheduling của GPU thread có thể thay đổi |
| Batching inference | Việc batching phía provider làm thay đổi thứ tự xử lý |

**Chiến lược giảm thiểu:**

- Chạy nhiều lần và dùng **majority voting**
- Dùng **structured output** như JSON, regex hoặc grammar-based constraints
- Implement **regression testing** để kiểm tra độ ổn định của output
- **Self-host** model khi cần kiểm soát hoàn toàn quá trình inference
- Thiết kế hệ thống **chịu được dao động** ngay từ đầu

**Điểm cân bằng:** `temperature ~= 0.1` cho sự cân bằng tốt hơn giữa độ ổn định và chất lượng output
so với việc cố định tuyệt đối ở `temperature=0`.

**Bài học rút ra:** `temperature=0` không phải là reliability guarantee.
Hệ thống cần được thiết kế để xử lý variance ngay từ đầu.

---

#### 2.6 Vy Lam - Enterprise-Grade Multi-Agent System: Startup Credit Scoring

Bài chia sẻ trình bày một **hệ thống chấm điểm tín dụng multi-agent** cho startup, một lĩnh vực
mà mô hình đánh giá tín dụng truyền thống thường thất bại vì dữ liệu của startup khác biệt căn bản
so với doanh nghiệp đã vận hành lâu năm.

**Vì sao traditional credit scoring không phù hợp với startup:**

- Cần lịch sử tài chính dài, tài sản thế chấp và mô hình doanh thu ổn định
- Startup thường chỉ có traction, chất lượng đội ngũ, IP và dữ liệu phi cấu trúc

**Các chiều dữ liệu của startup:**

| Chiều | Ví dụ |
|-------|-------|
| Financial | Revenue, burn rate, runway |
| Market | TAM, competitive landscape |
| Team | Kinh nghiệm, background, diversity |
| Traction | Tăng trưởng người dùng, retention, partnerships |

**Thiết kế hệ thống - Virtual Credit Committee:**

| Agent | Trách nhiệm |
|-------|-------------|
| Manager | Điều phối toàn bộ quá trình đánh giá |
| Financial Analyst | Đánh giá các chỉ số tài chính |
| Market Analyst | Đánh giá cơ hội thị trường |
| Team Evaluator | Rà soát đội ngũ sáng lập |
| Risk Assessor | Xác định các yếu tố rủi ro |
| Compliance Agent | Đảm bảo tuân thủ quy định |

**Yêu cầu output:**

- Credit score
- Risk rating
- Confidence level
- Audit trail với khả năng giải thích quyết định

**Các cân nhắc ở cấp enterprise - 6 trụ cột:**

| Trụ cột | Phạm vi |
|---------|---------|
| Security | Authentication, authorization, encryption |
| Data Governance | Data lineage, access control, retention |
| Networking | VPC isolation, private endpoints |
| Operations | Monitoring, alerting, incident response |
| Human Factors | Explainability, reviewer workflows |
| Compliance | Regulatory alignment, audit readiness |

**Guardrails - Ba tầng (Input -> Processing -> Output):**

| Tầng | Kiểm soát |
|------|-----------|
| Input | Content filtering, PII detection, injection prevention |
| Processing | Model selection controls, inference constraints |
| Output | Response validation, compliance verification |

**Lộ trình triển khai:**

```text
Local App / CrewAI -> AgentCore -> Docker -> ECR -> Bedrock -> API Gateway
                    + VPC, IAM, Secrets, Monitoring, Autoscaling, DR Strategy
```

**ROI kỳ vọng:**

- Thời gian xử lý: từ vài tuần xuống vài giờ
- Giảm analyst hours
- Tăng độ chính xác phê duyệt nhờ đánh giá đa chiều

---

### 3. Một số hình ảnh khi tham gia sự kiện

Dưới đây là một số hình ảnh ghi lại khi tham gia sự kiện:

![Hình ảnh tại Event 2 - 1](/4-eventparticipated/4.2-event2/img/20260523_092830.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 2](/4-eventparticipated/4.2-event2/img/20260523_093545.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 3](/4-eventparticipated/4.2-event2/img/20260523_093957.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 4](/4-eventparticipated/4.2-event2/img/20260523_102804.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 5](/4-eventparticipated/4.2-event2/img/20260523_103836.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 6](/4-eventparticipated/4.2-event2/img/20260523_111821.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 7](/4-eventparticipated/4.2-event2/img/20260523_113118.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 8](/4-eventparticipated/4.2-event2/img/20260523_113155.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 9](/4-eventparticipated/4.2-event2/img/20260523_113421.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 10](/4-eventparticipated/4.2-event2/img/20260523_121023.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 11](/4-eventparticipated/4.2-event2/img/20260523_121819.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 12](/4-eventparticipated/4.2-event2/img/20260523_121905.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 13](/4-eventparticipated/4.2-event2/img/20260523_122343.jpg?width=20pc&classes=shadow)
![Hình ảnh tại Event 2 - 14](/4-eventparticipated/4.2-event2/img/Screenshot%202026-06-10%20114648.png?width=20pc&classes=shadow)

---

### 4. Kết luận

AWS Vietnam Community Day 2026 cho thấy giá trị của AI không nằm ở riêng model,
mà còn nằm ở cách cung cấp context, thiết kế architecture, triển khai security và guardrails,
cũng như vận hành hệ thống ở quy mô thực tế.

| Đối tượng | Bài học chính |
|-----------|---------------|
| Cá nhân | Học cách cung cấp context chất lượng và xây dựng Second Brain để làm việc hiệu quả hơn với AI |
| Đội nhóm sản phẩm | Ưu tiên bài toán thực, giới hạn scope và đưa AI vào workflow cụ thể |
| Hạ tầng | Tận dụng CloudFront và các dịch vụ AWS cho performance, security và reliability |
| Enterprise | Multi-agent systems cần guardrails, audit trails, compliance và ROI rõ ràng trước khi đưa vào production |

> **Thông điệp chung:** AI chỉ thực sự tạo ra giá trị khi được kết hợp với tư duy sản phẩm,
> kiến trúc hệ thống phù hợp và quy trình vận hành đáng tin cậy.
