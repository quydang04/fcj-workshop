---
title: "Blog 2"
date: 2026-04-20
weight: 2
chapter: false
pre: "<b>3.2. </b>"
---

## Xây Dựng Workflow Nhiều Bước Đáng Tin Cậy Với AWS Lambda Durable Functions

Các ứng dụng hiện đại thường phải xử lý những quy trình gồm nhiều bước nối tiếp nhau – ví dụ xử lý đơn hàng, onboarding người dùng, hoặc điều phối các workflow AI gọi nhiều lần đến LLM và công cụ bên ngoài. Trước đây, để làm việc này trên AWS Lambda, lập trình viên phải ghép nối thêm Step Functions, SQS, DynamoDB để lưu trạng thái, dẫn đến hạ tầng phức tạp. Tại re:Invent 2025, AWS giới thiệu **AWS Lambda Durable Functions** – cho phép viết toàn bộ workflow dưới dạng code tuần tự ngay trong một hàm Lambda duy nhất, mà vẫn giữ được khả năng chịu lỗi và tạm dừng dài hạn.

### AWS Lambda Durable Functions là gì?

Durable Functions là các hàm Lambda thông thường được bật chế độ **durable execution**. Tính năng này mở rộng mô hình lập trình của Lambda bằng hai primitive mới là **step** và **wait**, cho phép tự động lưu tiến độ (checkpoint), khôi phục sau khi lỗi, và tạm dừng thực thi tới một năm mà không tốn phí compute trong lúc chờ. Bạn không cần quản lý thêm hạ tầng hay tự viết code quản lý trạng thái và xử lý lỗi.

Bản chất kỹ thuật là cơ chế **checkpoint và replay**: khi xảy ra lỗi, Lambda chạy lại hàm từ đầu nhưng bỏ qua các bước đã hoàn thành (đã có checkpoint) và dùng lại kết quả đã lưu, nhờ đó không mất tiến độ.

### Vấn đề của Lambda truyền thống

Với Lambda tiêu chuẩn, code của bạn chạy từ đầu đến cuối trong một lần invocation và hoàn toàn stateless. Điều này tạo ra ba hạn chế lớn khi xây dựng workflow phức tạp:

1. **Mất trạng thái khi lỗi:** Nếu lỗi xảy ra ở bất kỳ bước nào, toàn bộ hàm phải được retry lại từ đầu; mọi state phải tự lưu thủ công vào DynamoDB hoặc S3.
2. **Giới hạn thời gian:** Một lần thực thi tối đa 15 phút, không phù hợp với quy trình kéo dài hoặc cần chờ phê duyệt của con người.
3. **Phải tự xử lý idempotency:** Lập trình viên phải tự bảo vệ chống lại các lần gọi trùng và tự xây dựng chiến lược deploy an toàn.

### Cách hoạt động: Checkpoint & Replay

Durable Functions giải quyết các vấn đề trên bằng hai primitive cốt lõi trong open-source Durable Execution SDK:

- **Step – `context.step()`:** Bọc một khối logic nghiệp vụ để tự động tạo checkpoint và retry. Sau khi một step hoàn thành, nó sẽ được bỏ qua trong lần replay tiếp theo.
- **Wait – `context.wait()` / callback:** Tạm dừng thực thi trong một khoảng thời gian hoặc cho đến khi nhận tín hiệu bên ngoài (ví dụ phê duyệt của con người). Trong lúc chờ, hàm bị huỷ và không tính phí compute, sau đó tự động resume.

Sơ đồ kiến trúc dưới đây minh hoạ một AI workflow dùng Durable Functions: client gọi qua API Gateway tới hàm Lambda (đã bật durable execution); hàm dùng `step()` để gọi Bedrock (LLM) và lưu kết quả – mỗi step được checkpoint tự động; dùng `wait()`/callback để tạm dừng chờ phê duyệt rồi resume; trạng thái execution được phát ra EventBridge và CloudWatch để giám sát.

![Kiến trúc AI workflow với AWS Lambda Durable Functions](/images/3-Blog/3.2-Blog2/image1.png)

### Điểm nổi bật & lợi ích cốt lõi

- **Chịu lỗi tự động:** SDK tự checkpoint, tự retry với backoff cấu hình được, đảm bảo idempotency (chỉ một execution chạy cho mỗi request dù upstream có gọi lại).
- **Tạm dừng tới một năm:** Phù hợp cho workflow human-in-the-loop, chờ phê duyệt, hoặc xử lý theo lịch – không tốn tiền compute trong lúc chờ.
- **Giữ nguyên trải nghiệm Lambda:** Vẫn là hàm Lambda với cùng event handler và integration; chỉ cần bật một công tắc durable execution khi tạo hàm.
- **Đa ngôn ngữ:** SDK hỗ trợ JavaScript, TypeScript, Python và Java (Java đang ở bản Developer Preview).

### Các trường hợp sử dụng lý tưởng

- **Workflow AI nhiều bước:** Điều phối chuỗi gọi LLM, gọi tool và xử lý kết quả mà vẫn an toàn khi một lệnh gọi thất bại.
- **Xử lý đơn hàng & thanh toán:** Duy trì trạng thái giao dịch qua các lần lỗi, tự retry; điều phối ủy quyền, kiểm tra gian lận và quyết toán.
- **Phê duyệt human-in-the-loop:** Quy trình duyệt tài liệu, duyệt đơn nghỉ phép – tạm dừng chờ con người quyết định rồi mới tiếp tục.
- **Tác vụ chạy theo lịch / dài ngày:** Onboarding nhiều ngày, subscription trial, thông báo có độ trễ, xử lý batch theo cửa sổ thời gian.

### Ví dụ code (Python)

Sau khi bật durable execution và thêm SDK, bạn dùng `DurableContext` để bọc từng bước nghiệp vụ:

```python
def handler(event, context):
    # Bước 1: gọi LLM - được checkpoint tự động
    summary = context.step("summarize", lambda: call_llm(event))

    # Bước 2: chờ phê duyệt (miễn phí compute khi chờ)
    decision = context.wait_for_callback("approval")

    # Bước 3: chỉ chạy khi đã được duyệt
    if decision == "approved":
        context.step("persist", lambda: save_result(summary))
```

> Lưu ý: dù tổng workflow có thể kéo dài tới một năm, mỗi container Lambda vẫn chỉ chạy tối đa 15 phút giữa các lần checkpoint/wait.

### Tình trạng phát hành

Lambda Durable Functions được công bố ngày 02/12/2025 (re:Invent 2025), khả dụng ban đầu (GA) tại US East (Ohio) với runtime Python và Node.js, sau đó mở rộng thêm nhiều region. SDK cho Java ra mắt bản Developer Preview ngày 26/02/2026.

### Kết luận

AWS Lambda Durable Functions xoá bỏ ranh giới giữa sự đơn giản của Lambda và độ phức tạp của các hệ điều phối workflow. Thay vì ghép nối Step Functions, SQS và DynamoDB, bạn viết logic tuần tự trong một hàm duy nhất và để SDK lo việc checkpoint, retry và tạm dừng. Đây là lựa chọn lý tưởng cho các workflow AI nhiều bước, xử lý đơn hàng, và quy trình cần phê duyệt.

### Tài liệu tham khảo

- [Build multi-step applications and AI workflows with AWS Lambda durable functions (AWS News Blog)](https://aws.amazon.com/blogs/aws/build-multi-step-applications-and-ai-workflows-with-aws-lambda-durable-functions/)
- [Building fault-tolerant applications with AWS Lambda durable functions (AWS Compute Blog)](https://aws.amazon.com/blogs/compute/building-fault-tolerant-applications-with-aws-lambda-durable-functions/)
- [AWS Lambda durable functions – Product page](https://aws.amazon.com/lambda/durable-functions/)
