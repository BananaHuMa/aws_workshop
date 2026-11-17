---
title : "Frontend – S3 static website"
date : 2026-01-01
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### Tổng quan

+ Trong phần này, bạn sẽ xây dựng và triển khai giao diện chat phía người dùng kết nối với backend API. Frontend là một trang HTML tĩnh duy nhất được host trên Amazon S3, giúp giữ chi phí gần như bằng 0 và tận dụng tính năng static website hosting có sẵn của S3.

+ **Các khía cạnh chính của giai đoạn này:**
    + **Giao diện tĩnh (`index.html`):** Một trang chat nhẹ được xây dựng bằng HTML, CSS và JavaScript, sử dụng `fetch` để gọi endpoint API Gateway.
    + **Hosting (Amazon S3):** Trang được phục vụ dưới dạng static website công khai, chỉ tắt Block Public Access cho bucket này và áp dụng bucket policy chỉ đọc.
    + **Tích hợp:** Frontend được kết nối với URL backend API thật và xử lý trạng thái loading cũng như các mã lỗi (400, 429, 502/504) một cách rõ ràng.
    + **An toàn:** Một disclaimer hiển thị nhắc nhở người dùng rằng câu trả lời chỉ mang tính sơ bộ và không phải tư vấn pháp lý chính thức.

![Tổng quan kiến trúc Frontend](/images/5-Workshop/5.5-Frontend/overview.png)

#### Nội dung

- [Dựng giao diện chat](5.5.1-build-chat-page/)
- [Host trang trên S3](5.5.2-host-on-s3/)
- [Nối API và test end-to-end](5.5.3-connect-and-test/)