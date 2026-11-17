---
title : "Cấu hình API Gateway & chuẩn hóa Error Handling"
date : 2026-01-01 
weight : 3
chapter : false
pre : " <b> 5.4.3 </b> "
---

#### Mục tiêu
Mở hàm Lambda qua endpoint HTTPS công khai mà trình duyệt được phép gọi.

#### Các bước
1. Tạo API (HTTP hoặc REST) với route POST trỏ tới hàm Lambda.
2. Cấu hình CORS: `Access-Control-Allow-Origin: *`, các method POST và OPTIONS.
3. Xây tầng bắt lỗi trong Lambda trả về các mã trạng thái chuẩn.
4. Deploy stage và ghi lại URL gọi API.

| Mã | Khi nào | Ý nghĩa với client |
| :--- | :--- | :--- |
| 400 | Dữ liệu không hợp lệ | Sửa lại request |
| 429 | Chạm giới hạn của Groq API | Chờ rồi thử lại |
| 502 / 504 | Lỗi hệ thống hoặc AI | Thử lại sau |

![API Gateway routes và integration](/images/5-Workshop/5.4-Backend/apigw-routes.png)

![Cấu hình CORS](/images/5-Workshop/5.4-Backend/apigw-cors.png)

#### Kiểm tra
Request từ trình duyệt qua trang web S3 không bị chặn bởi CORS.