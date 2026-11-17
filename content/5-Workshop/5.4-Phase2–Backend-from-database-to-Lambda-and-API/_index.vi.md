---
title : "Giai đoạn 2 – Backend: từ Database đến Lambda & API"
date : 2026-01-01
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### Tổng quan

+ Trong phần này, bạn sẽ xây dựng một backend serverless truy xuất điều luật, gọi LLM và cung cấp một API ổn định.

+ **Các thành phần chính của giai đoạn này:**
    + **Cơ sở tri thức (DynamoDB):** Lưu trữ các điều luật (Nghị định 13/2023/NĐ-CP) để truy xuất dựa trên từ khóa.
    + **Điện toán (AWS Lambda):** Thực thi logic Python để truy vấn cơ sở dữ liệu, lắp ráp prompt và gọi Groq API bên ngoài.
    + **Lớp API (API Gateway):** Cung cấp endpoint HTTPS công khai đã bật CORS và xử lý lỗi chuẩn hóa để frontend có thể sử dụng.
    + **Giám sát (CloudWatch):** Ghi lại logs và metrics để theo dõi hiệu suất, thời gian phản hồi và khắc phục sự cố.

![Tổng quan kiến trúc Backend](/images/5-Workshop/5.4-Backend/overview.png)