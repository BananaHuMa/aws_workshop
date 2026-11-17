---
title: "Nhật ký công việc Tuần 9"
date: 2026-11-13
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu Tuần 9:

* Thực hiện kiểm thử end-to-end nghiêm ngặt, xác thực các trường hợp biên (edge-case) và tích hợp trích dẫn UI cho Nền tảng RAG Pháp lý.
* Thực hiện đánh giá bảo mật toàn diện và hoàn thiện việc tăng cường bảo mật nguyên tắc đặc quyền tối thiểu (least-privilege) cho IAM.
* Hoàn tất tài liệu kỹ thuật, trình diễn cho các bên liên quan (stakeholders) và bàn giao dự án chính thức.

### Các công việc cần triển khai trong tuần:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | - **Kiểm thử End-to-End Cuối cùng & Xác thực Trường hợp Biên:** <br>&emsp; + Thực hiện UAT nghiêm ngặt trên Nền tảng RAG Pháp lý <br>&emsp; + Kiểm thử các cơ chế bảo vệ chống ảo giác bằng cách truy vấn các điều khoản pháp lý không tồn tại để xác minh cơ chế dự phòng `NO_EVIDENCE_FOUND` <br>&emsp; + Xác thực hiệu suất truy vấn DynamoDB và độ trễ của Groq API dưới tải giả lập | 09/11/2026 | 09/11/2026 | Tài liệu Kiểm thử Nội bộ |
| 2 | - **Tích hợp Trích dẫn UI & Tinh chỉnh UX:** <br>&emsp; + Hợp tác với nhóm UI để ánh xạ các S3 URI thô từ phản hồi Lambda thành các trích dẫn pháp lý có thể nhấp và xác minh được <br>&emsp; + Tinh chỉnh UX giao diện chat để hiển thị rõ ràng tài liệu nguồn (ví dụ: Nghị định 13/2023/NĐ-CP) bên cạnh câu trả lời của LLM | 10/11/2026 | 10/11/2026 | Tài liệu Tích hợp Frontend |
| 3 | - **Đánh giá Bảo mật & Tăng cường IAM:** <br>&emsp; + Thực hiện rà soát bảo mật cuối cùng đối với tất cả các vai trò và chính sách IAM <br>&emsp; + Đảm bảo quyền truy cập đặc quyền tối thiểu nghiêm ngặt cho Lambda (S3 Read, DynamoDB Query, CloudWatch Logs) <br>&emsp; + Xác minh các chính sách S3 bucket để ngăn chặn truy cập công khai trái phép vào các tài liệu pháp lý thô | 11/11/2026 | 11/11/2026 | Thực tiễn Tốt nhất về AWS IAM & Bảo mật |
| 4 | - **Tài liệu Kỹ thuật & Chuyển giao Kiến thức:** <br>&emsp; + Soạn thảo tài liệu kỹ thuật toàn diện, bao gồm sơ đồ kiến trúc, giao ước API và sổ tay triển khai (deployment runbooks) <br>&emsp; + Ghi