---
title : "Xác định cấu trúc dữ liệu đầu vào"
date : 2026-01-01 
weight : 3
chapter : false
pre : " <b> 5.3.3 </b> "
---

#### Mục tiêu
Quyết định cách Lambda tiêm (inject) dữ liệu DynamoDB vào prompt gửi đi.

#### Các bước
1. Định dạng mỗi điều luật truy xuất thành một khối có nhãn (số điều + nội dung).
2. Đặt ngữ cảnh luật trước câu hỏi của người dùng trong message.
3. Giới hạn số lượng và độ dài điều luật để nằm trong giới hạn rate và token của mô hình.
4. Ghi mẫu cuối cùng vào `docs/`.

![Lắp ráp prompt: system prompt + ngữ cảnh luật + câu hỏi → Groq](/images/5-Workshop/5.3-Prompt/prompt-assembly.png)

#### Kiểm tra
Prompt in ra có đủ ba phần đúng thứ tự.