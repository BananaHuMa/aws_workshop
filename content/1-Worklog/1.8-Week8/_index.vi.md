---
title: "Nhật ký công việc Tuần 8"
date: 2026-11-08
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu Tuần 8:

* Tích hợp frontend S3 Static Website với backend API Gateway và các hàm Lambda.
* Triển khai xử lý lỗi mạnh mẽ, giám sát CloudWatch và tối ưu hóa hệ thống để đảm bảo chi phí $0 nghiêm ngặt (AWS Free Tier).
* Phối hợp với nhóm để tinh chỉnh prompt engineering và đảm bảo việc render trích dẫn trên UI được liền mạch.

### Các công việc cần triển khai trong tuần:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | - **Cấu hình API Gateway & CORS:** <br>&emsp; + Cấu hình các endpoint REST API và bật strict CORS headers (`Access-Control-Allow-Origin`, `POST`, `OPTIONS`) <br>&emsp; + Triển khai ánh xạ phản hồi lỗi chuẩn hóa (400 Bad Request, 502/504 Gateway Errors) <br>&emsp; + Kiểm thử các endpoint bằng `curl` để xác minh việc định tuyến payload tới Lambda | 02/11/2026 | 02/11/2026 | Tài liệu AWS API Gateway |
| 2 | - **Tích hợp Frontend (S3 Static Website):** <br>&emsp; + Triển khai `index.html`, CSS và JS lên S3 bucket đã bật static website hosting <br>&emsp; + Kết nối giao diện chat UI với endpoint API Gateway qua HTTPS <br>&emsp; + Đảm bảo frontend phân tích cú pháp chính xác tuple `(context_string, max_score_float)` và các S3 URI từ phản hồi của Lambda | 03/11/2026 | 03/11/2026 | Tài liệu Amazon S3 & Frontend |
| 3 | - **Xử lý lỗi & Giám sát Nâng cao:** <br>&emsp; + Triển khai cơ chế fallback mượt mà cho giới hạn tốc độ Groq API (HTTP 429) kèm thông báo thân thiện trên UI <br>&emsp; + Cấu hình Amazon CloudWatch Log Groups cho Lambda để theo dõi thời gian thực thi và các lỗi <br>&emsp; + Thiết lập CloudWatch Alarms cho thời gian thực thi Lambda khi tiến gần đến giới hạn timeout 30s | 04/11/2026 | 04/11/2026 | Tài liệu AWS CloudWatch |
| 4 | - **Prompt Engineering Cộng tác & Bàn giao:** <br>&emsp; + Làm việc với Thành viên 2 để tinh chỉnh System Prompt, thực thi việc tuân thủ tuyệt đối guardrail `NO_EVIDENCE_FOUND` <br>&emsp; + Định dạng phản hồi Lambda thô để bao gồm các S3 URI sạch, có cấu trúc cho Thành viên 3 render thành các trích dẫn có thể nhấp và xác minh được trên UI | 05/11/2026 | 05/11/2026 | Tài liệu Dự án Nội bộ |
| 5 | - **Tinh chỉnh Hiệu năng & Xác minh Chi phí:** <br>&emsp; + Tối ưu hóa provisioned throughput của bảng DynamoDB `LegalArticles` (duy trì 25 WCU / 25 RCU để nằm trong Free Tier) <br>&emsp; + Thực hiện kiểm thử tải end-to-end để xác minh thời gian phản hồi và độ chính xác <br>&emsp; + Xem xét AWS Cost Explorer để xác nhận kiến trúc vẫn duy trì ở mức $0.00/tháng | 06/11/2026 | 06/11/2026 | Tài liệu AWS Cost Explorer & DynamoDB |

### Thành tựu Tuần 8:

* Tích hợp thành công frontend tĩnh lưu trữ trên S3 với backend API, cho phép các tương tác chat liền mạch, thời gian thực và an toàn cho các truy vấn pháp lý.
* Triển khai xử lý lỗi mạnh mẽ, cấp độ production, đảm bảo hệ thống quản lý mượt mà các giới hạn tốc độ Groq API (429) và timeout backend mà không làm gián đoạn trải nghiệm người dùng.
* Thiết lập hệ thống ghi log và giám sát CloudWatch toàn diện, cung cấp khả năng hiển thị đầy đủ các chỉ số thực thi Lambda và hiệu suất truy xuất RAG.
* Tinh chỉnh System Prompt RAG trong sự phối hợp chặt chẽ với nhóm prompt engineering, đạt được mức tuân thủ 100% đối với ràng buộc "không ảo giác" và định dạng hoàn hảo cho các trích dẫn trên UI.
* Xác thực và tối ưu hóa toàn bộ kiến trúc Serverless (Lambda, DynamoDB, API Gateway, S3), xác nhận thông qua AWS Cost Explorer rằng hệ thống hoạt động hoàn toàn trong AWS Free Tier, duy trì chi phí vận hành mục tiêu $0.00/tháng.