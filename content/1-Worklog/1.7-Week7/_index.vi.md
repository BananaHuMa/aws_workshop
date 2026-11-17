---
title: "Nhật ký công việc Tuần 7"
date: 2026-11-01
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu Tuần 7:

* Hoàn thiện việc tạo nguyên mẫu pipeline RAG cục bộ và xác thực độ chính xác của truy xuất trước khi triển khai lên AWS.
* Triển khai, xử lý sự cố và tối ưu hóa pipeline nạp dữ liệu serverless trên AWS (Lambda, S3, Bedrock).
* Phác thảo, thiết kế kiến trúc và khởi động quá trình triển khai kỹ thuật cho đề xuất "Nền tảng RAG Pháp lý (Nghị định 13/2023/NĐ-CP)".

### Các công việc cần triển khai trong tuần:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | - **Tạo nguyên mẫu & Xác thực RAG cục bộ:** <br>&emsp; + Xác thực pipeline sử dụng ChromaDB & `sentence-transformers` đa ngôn ngữ để mô phỏng hành vi của AWS <br>&emsp; + Phát triển Engine Chia nhỏ Thông minh Toàn cục (Tầng 1: regex song ngữ cho phân cấp pháp lý VN/EN; Tầng 2: bộ chia nhỏ theo đoạn dự phòng) <br>&emsp; + Triển khai Cơ chế kiểm soát Ngưỡng Kép (>0.65 để bao gồm, <0.50 trả về `NO_EVIDENCE_FOUND`) <br>&emsp; + Xây dựng engine Tự Đánh giá Động Toàn cục (khớp vân tay 60 ký tự) | 26/10/2026 | 26/10/2026 | Tài liệu Dự án Nội bộ |
| 2 | - **Triển khai AWS & Các giải pháp Kỹ thuật:** <br>&emsp; + Thiết kế kiến trúc định tuyến S3 bucket kép (`raw-docs` so với `processed-chunks`) để đóng dấu metadata một cách tất định <br>&emsp; + Giải quyết khủng hoảng biên dịch Lambda Layer đa nền tảng bằng cách chuyển từ `pdfplumber` sang `pypdf` thuần Python <br>&emsp; + Tinh chỉnh tài nguyên tính toán của Lambda lên 512 MB RAM và Timeout 30s để ngăn chặn sự cố khi phân tích cú pháp PDF <br>&emsp; + Cấu hình các chính sách IAM đặc quyền tối thiểu và S3 Event Notifications | 27/10/2026 | 27/10/2026 | Tài liệu AWS Lambda & IAM |
| 3 | - **Tích hợp Amazon Bedrock Knowledge Base:** <br>&emsp; + Cấu hình Knowledge Base để nạp trực tiếp JSON đã được chia nhỏ từ S3 <br>&emsp; + Chọn Amazon Titan Text Embeddings V2 để đạt độ chính xác tìm kiếm ngữ nghĩa đa ngôn ngữ tự nhiên <br>&emsp; + Cấp phát Amazon OpenSearch Serverless thông qua Bedrock Quick Create <br>&emsp; + Đồng bộ hóa và lập chỉ mục thành công hơn 255 chunk JSON được cấu trúc hoàn hảo, gắn thẻ metadata | 28/10/2026 | 28/10/2026 | Tài liệu Amazon Bedrock |
| 4 | - **Đề xuất RAG Pháp lý (Giai đoạn 1 & 2):** <br>&emsp; + Xác định phạm vi và luồng dữ liệu RAG Serverless cho Nghị định 13/2023/NĐ-CP <br>&emsp; + Phác thảo System Prompts nghiêm ngặt để ràng buộc ngữ cảnh tuyệt đối (không ảo giác) <br>&emsp; + Cấp phát bảng DynamoDB `LegalArticles` <br>&emsp; + Phát triển hàm Python Lambda để truy xuất ngữ cảnh và tích hợp Groq API (`qwen/qwen3.8-27b`) | 29/10/2026 | 29/10/2026 | Tài liệu Dự án Nội bộ |
| 5 | - **Đề xuất RAG Pháp lý (Giai đoạn 3 & 4):** <br>&emsp; + Cấu hình API Gateway (CORS headers, xử lý lỗi chuẩn hóa cho 400, 429, 502/504) <br>&emsp; + Triển khai S3 Static Website và tích hợp giao diện chat frontend với API backend <br>&emsp; + Thực hiện kiểm thử end-to-end (thông qua `curl` và web UI), xác minh độ chính xác của LLM và hoàn tất triển khai với chi phí $0 | 30/10/2026 | 30/10/2026 | Tài liệu AWS API Gateway |

### Thành tựu Tuần 7:

* Xác thực thành công pipeline RAG cục bộ, đạt độ chính xác truy xuất được chứng minh bằng toán học (**Average Precision > 0.75**) bằng phương pháp Tự Đánh giá Động Toàn cục, loại bỏ hoàn toàn thiên kiến được lập trình sẵn.
* Giải quyết các trở ngại triển khai AWS quan trọng, bao gồm lỗi biên dịch Lambda Layer đa nền tảng và sự cố timeout tính toán, đảm bảo một pipeline nạp dữ liệu serverless ổn định, sẵn sàng cho môi trường production.
* Tích hợp thành công Amazon Bedrock Knowledge Base với **Titan Text Embeddings V2** và OpenSearch Serverless, lập chỉ mục hơn 255 chunk được cấu trúc hoàn hảo, gắn thẻ metadata với **không xảy ra nhiễm chéo** giữa các loại tài liệu.
* Phác thảo và cấu trúc hóa đề xuất kỹ thuật toàn diện cho **"Nền tảng RAG Pháp lý (Nghị định 13/2023/NĐ-CP)"**, định nghĩa một kiến trúc Serverless có khả năng mở rộng cao, chi phí $0 (S3, API Gateway, Lambda, DynamoDB, Groq API).
* Chuyển giao giao ước API `retrieve_with_dynamic_filter` cho toàn bộ nhóm, đảm bảo các phản hồi dự phòng an toàn (`NO_EVIDENCE_FOUND`) và cung cấp các S3 URI thô để trích dẫn có thể nhấp trên UI, đảm bảo quá trình chuyển giao suôn sẻ cho các giai đoạn Prompt Engineering và UI.