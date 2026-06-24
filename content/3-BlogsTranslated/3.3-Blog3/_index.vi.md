---
title: "Blog 3"
date: 2026-04-20
weight: 3
chapter: false
pre: "<b>3.3. </b>"
---

## OpenSearch Serverless Thế Hệ Mới: Vector Search Co Giãn Về 0 Cho Ứng Dụng AI Agent

Các ứng dụng AI agent có một đặc điểm rất riêng về tải: một agent có thể bắn ra hàng trăm truy vấn vector trong lúc suy luận một tác vụ, rồi im lặng hàng giờ. Với hạ tầng tìm kiếm truyền thống, bạn vẫn phải trả tiền cho phần năng lực không dùng tới trong những khoảng rảnh đó. Ngày 28/05/2026, AWS công bố thế hệ mới của **Amazon OpenSearch Serverless** (gọi là NextGen) – một search và vector engine được thiết kế lại từ đầu để phục vụ đúng kiểu workload bất định này.

### OpenSearch Serverless NextGen là gì?

NextGen là kiến trúc mới của Amazon OpenSearch Serverless, một search và vector engine được quản lý hoàn toàn (fully managed). Điểm cốt lõi là nó **tách rời (decouple) hoàn toàn compute và storage** thông qua một shared storage layer, cho phép co giãn năng lực tính toán độc lập với khối lượng dữ liệu. Nhờ đó dịch vụ có thể cấp phát tài nguyên trong vài giây và co giãn về tận 0 khi ứng dụng rảnh.

AWS đặt tên hai kiến trúc: các collection cũ nay gọi là **Classic**, còn kiến trúc mới là **NextGen** và là mặc định khi tạo collection mới qua Console. Trong API/CLI, bạn chỉ định `--generation NEXTGEN` (hoặc `--generation CLASSIC` để giữ kiến trúc cũ).

### Vấn đề của kiến trúc Classic

Kiến trúc Serverless ban đầu luôn duy trì tối thiểu hai OpenSearch Compute Unit (OCU) chạy thường trực. Điều này hợp lý với một search engine production có tải ổn định, nhưng lại lãng phí với workload kiểu agent:

- **Trả phí cả khi rảnh:** Compute luôn được cấp phát ở mức tối thiểu, nên bạn vẫn tốn tiền dù không có truy vấn nào.
- **Compute gắn liền storage:** Không thể co giãn riêng phần tính toán theo nhu cầu mà không ảnh hưởng tới dữ liệu đã lưu.
- **Co giãn chậm:** Cấp phát tài nguyên tính bằng phút, khó theo kịp các đợt tăng tải đột ngột của agentic workflow.

### Cách NextGen hoạt động: tách rời Compute & Storage

Thay đổi nền tảng của NextGen là tách rời compute khỏi storage. Một shared storage layer mới được cả Indexing OCU và Search OCU truy cập, nhờ vậy OCU có thể co giãn lên xuống bất kể lượng dữ liệu đang lưu. Bạn có thể có nhiều index chứa dữ liệu mà không tốn chi phí compute nếu không đang index hay tìm kiếm.

Sơ đồ kiến trúc dưới đây minh hoạ cách NextGen phục vụ một AI agent: agent tạo embedding qua Bedrock rồi ghi vào Indexing OCU; truy vấn vector đi qua Search OCU. Cả Indexing OCU và Search OCU (tầng compute) co giãn độc lập và chia sẻ chung một Shared Storage Layer, cho phép scale-to-zero khi rảnh.

![Kiến trúc Amazon OpenSearch Serverless NextGen](/images/3-Blog/3.3-Blog3/image1.png)

### Điểm nổi bật & lợi ích cốt lõi

- **Scale-to-zero thực sự:** Khi không có request trong cửa sổ idle (10 phút), dịch vụ giải phóng compute và OCU về 0 – ngừng tính phí compute. Khi có lưu lượng trở lại, năng lực phục hồi trong khoảng 10 giây.
- **Co giãn nhanh hơn 20 lần:** Tạo tài nguyên trong vài giây và mở rộng năng lực nhanh gấp 20 lần so với thế hệ trước, đáp ứng cả những agentic workflow khó dự đoán nhất.
- **Tiết kiệm tới 60% chi phí:** Với workload có nhiều thời gian rảnh, kiến trúc mới giảm tới 60% chi phí hạ tầng so với việc cấp phát cụm cho tải đỉnh.
- **Tích hợp AI-native:** Tích hợp sẵn với các nền tảng phát triển AI như Vercel và Kiro; là một phần của OpenSearch Agent Skills để dùng trực tiếp trong Claude Code, Cursor, Codex bằng câu lệnh ngôn ngữ tự nhiên.

### Các trường hợp sử dụng lý tưởng

- **Backend vector cho AI agent:** Lưu và truy vấn vector embedding cho RAG, semantic search mà chỉ trả tiền khi agent thực sự truy vấn.
- **Semantic Search:** Duy trì chỉ mục vector cho truy vấn ngôn ngữ tự nhiên, thay cho việc tự vận hành một vector database riêng.
- **Workload tải bất định:** Ví dụ sàn thương mại điện tử tăng tải 10x trong flash sale rồi về 0 – co giãn tức thì mà không cần cấp phát trước cho đỉnh.
- **Môi trường dev/test:** Express Create dựng nhanh một collection với policy mặc định, hữu ích để thử nghiệm.

### Tình trạng phát hành

Thế hệ mới của OpenSearch Serverless được công bố ngày 28/05/2026 và đã ở trạng thái GA. Tại thời điểm ra mắt, hai loại collection được hỗ trợ là full-text search và vector search. Có thể tạo collection qua Console, AWS SDK và AWS CLI; hỗ trợ AWS CloudFormation sẽ có sau.

> Lưu ý: shared storage vẫn tính phí lưu trữ theo GB/tháng kể cả khi compute đã về 0, nên các con số 20x và 60% là có điều kiện, gắn với baseline cụ thể và workload có nhiều thời gian rảnh.

### Kết luận

OpenSearch Serverless NextGen giải quyết đúng bài toán chi phí của kỷ nguyên AI agent: tải bùng nổ rồi im lặng. Bằng cách tách rời compute và storage để co giãn về 0, nó cho phép triển khai backend tìm kiếm và vector production-ready trong vài phút, trả tiền theo mức dùng thực tế. Đây là mảnh ghép tự nhiên cho các kiến trúc RAG và semantic search mà không cần tự vận hành một vector database riêng.

### Tài liệu tham khảo

- [Introducing the next generation of Amazon OpenSearch Serverless (AWS News Blog)](https://aws.amazon.com/blogs/aws/introducing-the-next-generation-of-amazon-opensearch-serverless-for-building-your-agentic-ai-applications/)
- [The next generation of Amazon OpenSearch Serverless (AWS Big Data Blog)](https://aws.amazon.com/blogs/big-data/the-next-generation-of-amazon-opensearch-serverless-built-from-the-ground-up-for-agents/)
- [Amazon OpenSearch Service Pricing](https://aws.amazon.com/opensearch-service/pricing/)
