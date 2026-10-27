---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---


Tại phần này, bạn cần tóm tắt các nội dung trong workshop mà bạn **dự tính** sẽ làm.

# Trợ lý AI Pháp lý & Bảo mật Doanh nghiệp
## Giải pháp RAG Serverless AWS Thống nhất cho Tự động hóa Tuân thủ & Truy xuất Pháp lý

### 1. Tóm tắt Điều hành
Trợ lý AI Pháp lý & Bảo mật Doanh nghiệp được thiết kế cho bootcamp FCAJ nhằm giúp các doanh nghiệp truy vấn an toàn các tài liệu pháp lý nội bộ (ví dụ: Nghị định 13/PDPD của Việt Nam) và chủ động phát hiện các vi phạm tuân thủ trong các hợp đồng mới được tải lên. Hệ thống tận dụng kiến trúc AWS Serverless Hướng sự kiện (Event-Driven) Lai (Hybrid). Với vai trò là Kiến trúc sư RAG (Người 1), trọng tâm là xây dựng một quy trình (pipeline) Nạp dữ liệu và Cơ sở tri thức vững chắc, đảm bảo việc truy xuất ngữ cảnh pháp lý chính xác, không có ảo giác (hallucination) thông qua lọc siêu dữ liệu tất định (deterministic), chia đoạn thông minh song ngữ và các rào chắn độ tin cậy ngưỡng kép nghiêm ngặt, đồng thời tuân thủ nghiêm ngặt ngân sách dự án 200$.

### 2. Đặt vấn đề
**Vấn đề là gì?**
Các bước kiểm tra tuân thủ pháp lý thủ công diễn ra chậm chạp, dễ xảy ra sai sót và tốn kém. Các hệ thống RAG thương mại tiêu chuẩn thất bại khi xử lý tài liệu pháp lý trong thực tế: chúng phá vỡ định dạng pháp lý tiếng Việt phức tạp (ví dụ: tách "Điều 1" khỏi "Khoản 2"), nhầm lẫn ngữ cảnh giữa các nghị định của chính phủ và hợp đồng tư nhân, và sinh ra ảo giác khi đối mặt với dữ liệu có độ liên quan thấp. Hơn nữa, việc xử lý file PDF trong môi trường serverless thường xuyên kích hoạt các lỗi biên dịch đa nền tảng và treo do hết thời gian chờ (timeout).

**Giải pháp**
Nền tảng sử dụng kiến trúc AWS hướng sự kiện. Khi một tài liệu được tải lên Amazon S3, nó sẽ kích hoạt một hàm AWS Lambda sử dụng **Bộ chia đoạn thông minh vạn năng (Universal Smart Chunker)**. Bộ chia đoạn này sử dụng regex song ngữ chuyên biệt (cho "Điều/Khoản" trong tiếng Việt và "Article/Section" trong tiếng Anh) cùng cơ chế dự phòng dựa trên đoạn văn vững chắc. Nó che thông tin PII, gắn nhãn siêu dữ liệu (`document_type`, `contract_id`), và lưu các chunk JSON sạch sẽ vào một bucket S3 đã xử lý. Amazon Bedrock Knowledge Base (sử dụng Titan Text Embeddings V2 và OpenSearch Serverless) sẽ lập chỉ mục dữ liệu này. Việc truy xuất được kiểm soát nghiêm ngặt thông qua Lọc siêu dữ liệu và Rào chắn Ngưỡng kép (từ chối các điểm số < 0.50) để đảm bảo không có sự nhiễm chéo (cross-contamination) và ngăn chặn ảo giác AI.

**Lợi ích và Lợi tức đầu tư (ROI)**
Giải pháp thiết lập một quy trình nạp dữ liệu cấp độ sản xuất, có thể tái sử dụng, đảm bảo truy xuất pháp lý có độ chính xác cao. Nó loại bỏ việc phân tích cú pháp tài liệu thủ công, đảm bảo quyền riêng tư dữ liệu nghiêm ngặt thông qua che PII, và ngăn chặn các ảo giác AI tốn kém thông qua cách ly siêu dữ liệu tất định. Kiến trúc được tối ưu hóa mạnh mẽ để nằm gọn trong giới hạn ngân sách bootcamp 200$ bằng cách sử dụng các phụ thuộc Python thuần (`pypdf`) để tránh các pipeline build phức tạp và tối ưu hóa kích thước chunk nhằm giảm thiểu việc sử dụng token của Bedrock.

### 3. Kiến trúc Giải pháp
Nền tảng sử dụng kiến trúc serverless AWS để quản lý việc nạp và truy xuất tài liệu. Dữ liệu được tải lên bucket S3 Thô (Raw), kích hoạt một hàm Lambda để trích xuất, chia nhỏ, che thông tin và gắn thẻ dữ liệu. Các chunk JSON đã xử lý được lưu vào bucket S3 Đã xử lý (Processed), đóng vai trò là nguồn dữ liệu cho Amazon Bedrock Knowledge Base. Kiến trúc chi tiết như sau:

*(Chỗ trống cho Sơ đồ Kiến trúc: S3 Raw -> EventBridge -> Lambda (pypdf + Smart Chunker + Che PII) -> S3 Processed -> Bedrock Knowledge Base (Titan Embeddings V2 + OpenSearch Serverless) -> Bedrock Retrieve API với Bộ lọc Siêu dữ liệu)*

**Các dịch vụ AWS được sử dụng**
- **Amazon S3**: Kiến trúc bucket kép để lưu trữ tài liệu thô và lưu trữ chunk JSON đã xử lý.
- **AWS Lambda**: Compute hướng sự kiện để trích xuất văn bản PDF, chia đoạn thông minh và gắn thẻ siêu dữ liệu.
- **Amazon Bedrock Knowledge Base**: Công cụ RAG cốt lõi để lưu trữ vector và truy xuất ngữ nghĩa.
- **Amazon OpenSearch Serverless**: Cơ sở dữ liệu vector nền tảng (được cấp phát qua Bedrock Quick Create).
- **Amazon Titan Text Embeddings V2**: Mô hình embedding đa ngôn ngữ để vector hóa chính xác cả văn bản pháp lý tiếng Việt và tiếng Anh.

**Thiết kế Thành phần**
- **Nạp dữ liệu**: S3 Event Notifications kích hoạt hàm Lambda khi file được tải lên các thư mục cụ thể (`decrees/` hoặc `contracts/`).
- **Xử lý dữ liệu**: Lambda sử dụng `pypdf` (Python thuần) để trích xuất văn bản, áp dụng Bộ chia đoạn thông minh vạn năng (Regex + Dự phòng Đoạn văn), che PII và gắn thẻ siêu dữ liệu.
- **Lưu trữ dữ liệu**: Các chunk JSON sạch, phân cấp được lưu vào bucket S3 Đã xử lý.
- **Cơ sở tri thức**: Bedrock đồng bộ hóa bucket S3, tạo ra các embedding và lưu trữ các vector cùng với siêu dữ liệu phẳng (flat metadata) để lọc.
- **Truy xuất & Rào chắn**: API backend gọi API `Retrieve` của Bedrock với các bộ lọc siêu dữ liệu `document_type` nghiêm ngặt và thực thi điểm tin cậy ngưỡng kép (0.65 để đưa vào, 0.50 là mức sàn tuyệt đối) để ngăn chặn ảo giác.

### 4. Triển khai Kỹ thuật
**Các giai đoạn triển khai**
Dự án này tuân theo chu kỳ phát triển 4 giai đoạn có cấu trúc:
- **Giai đoạn 1: Tạo mẫu & Xác thực Cục bộ**: Phát triển và kiểm thử Bộ chia đoạn thông minh vạn năng và Mock Bedrock API cục bộ bằng ChromaDB và các file PDF tiếng Việt/Tiếng Anh thực tế để xác thực logic regex và dự phòng.
- **Giai đoạn 2: Triển khai Pipeline Nạp dữ liệu AWS**: Triển khai hàm Lambda, giải quyết các vấn đề phụ thuộc đa nền tảng bằng cách xây dựng một `pypdf` Lambda Layer tùy chỉnh, cấu hình các chính sách IAM đặc quyền tối thiểu (least-privilege), và điều chỉnh tài nguyên compute (512MB RAM, timeout 30s) để ngăn chặn treo.
- **Giai đoạn 3: Tích hợp Bedrock Knowledge Base**: Cấp phát Bedrock Knowledge Base, kết nối bucket S3 Đã xử lý, chọn Titan Text Embeddings V2 và thực hiện đồng bộ dữ liệu ban đầu.
- **Giai đoạn 4: Đánh giá Động Vạn năng & Bàn giao**: Chạy script tự đánh giá tự động trên Bedrock KB thực tế để chứng minh độ chính xác của truy xuất (>75%), sau đó bàn giao hợp đồng API `retrieve_with_dynamic_filter` cho Người 2 (Kỹ sư Prompt).

**Yêu cầu Kỹ thuật**
- **Công cụ Nạp dữ liệu**: Python 3.12, `pypdf` (để tương thích đa nền tảng), `boto3`, và Regex nâng cao để phân tích cú pháp phân cấp pháp lý song ngữ.
- **Đánh giá RAG**: Script Python tùy chỉnh cho Tự đánh giá Động Vạn năng (lấy mẫu chunk, tạo truy vấn và xác minh vân tay 60 ký tự) để chứng minh độ chính xác toán học mà không có độ lệch được hardcode.
- **Bảo mật**: Che PII dựa trên Regex (email, số điện thoại) trước khi vector hóa.

### 5. Tiến độ & Các mốc quan trọng
**Tiến độ Dự án**
- **Tuần 1**: Tạo mẫu cục bộ, tinh chỉnh regex và kiểm thử mock ChromaDB.
- **Tuần 2**: Triển khai AWS Lambda, tạo Layer tùy chỉnh, cấu hình IAM và thiết lập S3 trigger.
- **Tuần 3**: Cấp phát Amazon Bedrock Knowledge Base, đồng bộ dữ liệu và xác thực bộ lọc siêu dữ liệu.
- **Tuần 4**: Đánh giá Động Vạn năng, tinh chỉnh hiệu suất, hoàn thiện tài liệu và bàn giao cho đội ngũ LLM/Prompt Engineering.

### 6. Ước tính Ngân sách
Kiến trúc được tối ưu hóa nghiêm ngặt cho **giới hạn ngân sách bootcamp 200$**.
- **AWS Lambda**: ~$0.00/tháng (Nằm gọn trong free tier cho việc xử lý tài liệu ở mức vừa phải).
- **Amazon S3**: ~$0.05/tháng (Lưu trữ tối thiểu cho PDF thô và chunk JSON đã xử lý).
- **Amazon Bedrock Knowledge Base (OpenSearch Serverless)**: ~$140.00/tháng (Tối thiểu 4 OCU cho dev/testing. *Lưu ý: Có thể tạm dừng giữa các buổi demo để tiết kiệm chi phí, hoặc chuyển sang Aurora PostgreSQL Serverless để có chi phí cơ bản thấp hơn nếu cần*).
- **Amazon Bedrock (Embeddings & Retrieval)**: ~$10.00 - $20.00/tháng (Được tối ưu hóa bằng cách truy xuất Top-K=5 nghiêm ngặt và các chunk nhỏ, dày đặc ngữ nghĩa để giảm thiểu việc sử dụng token).
- **Tổng chi phí ước tính hàng tháng**: ~$150.00 - $160.05, an toàn dưới mức giới hạn 200$.

### 7. Đánh giá Rủi ro
**Ma trận Rủi ro**
- **Lỗi Trích xuất PDF (Hình ảnh quét)**: Tác động trung bình, xác suất trung bình.
- **Lambda Timeout/Treo do hết bộ nhớ**: Tác động cao, xác suất thấp (đã được giảm thiểu).
- **Lỗi Phụ thuộc Đa nền tảng**: Tác động cao, xác suất trung bình (đã được giảm thiểu).
- **Ảo giác AI / Nhiễm chéo Ngữ cảnh**: Tác động cao, xác suất trung bình (đã được giảm thiểu).

**Chiến lược Giảm thiểu**
- **Trích xuất**: Sử dụng `pypdf` để trích xuất PDF dựa trên văn bản đáng tin cậy. (Cải tiến trong tương lai: Thêm Amazon Textract cho hình ảnh quét).
- **Compute**: Chủ động điều chỉnh Lambda lên 512 MB bộ nhớ và thời gian chờ 30 giây để xử lý các tác vụ phân tích nặng.
- **Phụ thuộc**: Sử dụng 100% thư viện Python thuần (`pypdf`) và Lambda Layer tùy chỉnh để tránh lỗi biên dịch C-extension từ Windows sang Linux.
- **Ảo giác**: Thực thi Lọc siêu dữ liệu nghiêm ngặt (`document_type`) và Rào chắn Ngưỡng kép (từ chối điểm truy xuất < 0.50) để đảm bảo LLM chỉ nhận được ngữ cảnh cô lập và có độ liên quan cao.

### 8. Kết quả Mong đợi
**Cải tiến Kỹ thuật:** 
- Tự động hóa việc chia nhỏ và gắn thẻ siêu dữ liệu cho các tài liệu pháp lý phức tạp, lộn xộn.
- Cách ly truy xuất tất định (không nhiễm chéo giữa các nghị định và hợp đồng).
- Điểm chính xác của truy xuất được chứng minh bằng toán học thông qua Tự đánh giá Động Vạn năng.

**Giá trị Dài hạn:**
- Một mẫu pipeline nạp dữ liệu serverless cấp độ doanh nghiệp, có thể tái sử dụng, có thể điều chỉnh cho bất kỳ hệ thống RAG tuân thủ pháp lý, y tế hoặc tài chính nào.
- Một nền tảng vững chắc để Người 2 và Người 3 xây dựng giao diện chatbot có độ chính xác cao, có trích dẫn.