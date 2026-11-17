---
title : "Kiểm thử Backend"
date : 2026-01-01 
weight : 4
chapter : false
pre : " <b> 5.4.4 </b> "
---

#### Mục tiêu
Chứng minh backend hoạt động trước khi nối giao diện.

#### Các bước
1. Gửi POST bằng `curl` với một câu hỏi mẫu.
2. Mở CloudWatch Logs và kiểm tra thời gian phản hồi, dữ liệu trả về và cấu trúc JSON.
3. Test các trường hợp lỗi: câu hỏi rỗng (400) và, nếu có thể, trường hợp quá giới hạn (429).

```bash
curl -X POST "<API_URL>" \
  -H "Content-Type: application/json" \
  -d '{"question": "Dùng CCCD gửi quảng cáo có bị phạt không?"}'