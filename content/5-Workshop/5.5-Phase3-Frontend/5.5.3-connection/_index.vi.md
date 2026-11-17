---
title : "Nối API và test end-to-end"
date : 2026-01-01 
weight : 3
chapter : false
pre : " <b> 5.5.3 </b> "
---

#### Mục tiêu
Cho trang đã deploy gọi backend thật.

#### Các bước
1. Đặt URL gọi API trong `index.html` và tải lại lên bucket S3.
2. Mở website và hỏi câu hỏi mẫu.
3. Mở **console của trình duyệt** (developer console) và kiểm tra không có lỗi CORS.
4. Kiểm tra request trong **CloudWatch Logs**.

![Câu trả lời hiển thị trên trang web](/images/5-Workshop/5.5-Frontend/e2e-result.png)

#### Kiểm tra
Câu hỏi → câu trả lời có căn cứ trên trang, kèm một dòng log tương ứng.