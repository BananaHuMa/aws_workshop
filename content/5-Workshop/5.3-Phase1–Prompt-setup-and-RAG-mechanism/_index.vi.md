---
title : "Giai đoạn 1 – Thiết lập Prompt & cơ chế RAG"
date : 2026-01-01
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Thiết kế Prompt và RAG

Trong phần này, bạn sẽ định hình cách mô hình ngôn ngữ nhận và xử lý dữ liệu pháp lý trước khi viết code. Bạn sẽ xây dựng system prompt để thiết lập vai trò cho mô hình, thiết lập các ràng buộc ngữ cảnh nghiêm ngặt để ngăn chặn việc bịa đặt thông tin, và xác định cấu trúc đầu vào để đưa dữ liệu từ DynamoDB vào prompt. Công việc thiết kế này sẽ được thử nghiệm trong Groq playground trước khi được triển khai vào hàm Lambda.

![overview](/images/5-Workshop/5.3-Prompt/overview.png)

#### Nội dung

- [Xây dựng System Prompt định hướng vai trò](5.3.1-Build-a-role-defining-system-prompt/_index.vi.md)
- [Thiết lập ràng buộc ngữ cảnh](5.3.2-Set-the-context-constraint/_index.vi.md)
- [Xác định cấu trúc dữ liệu đầu vào](5.3.3-Define-the-input-structure/_index.vi.md)