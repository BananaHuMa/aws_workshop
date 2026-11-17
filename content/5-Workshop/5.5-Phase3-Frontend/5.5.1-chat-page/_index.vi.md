---
title : "Dựng giao diện chat"
date : 2026-01-01 
weight : 1
chapter : false
pre : " <b> 5.5.1 </b> "
---

#### Mục tiêu
Tạo một trang tĩnh duy nhất gọi backend bằng `fetch`.

#### Các bước
1. Dựng bố cục chat: tiêu đề, badge trạng thái, lời chào, danh sách tin nhắn, ô nhập và nút gửi.
2. Khi gửi, gọi `fetch` bằng HTTP POST tới URL API và hiển thị trạng thái đang xử lý.
3. Hiển thị thông báo rõ ràng cho các lỗi (`400`, `429`, `502/504`).
4. **Khuyến nghị:** Thêm disclaimer hiển thị rằng câu trả lời là sơ bộ, không phải tư vấn pháp lý.

![Trang chat của website](/images/5-Workshop/5.5-Frontend/frontend-ui.png)

#### Kiểm tra
Mở `index.html` trên máy thấy trang chat và lời chào.