---
title : "Thiết lập ràng buộc ngữ cảnh"
date : 2026-01-01 
weight : 2
chapter : false
pre : " <b> 5.3.2 </b> "
---

#### Mục tiêu
Buộc mô hình chỉ trả lời dựa trên văn bản pháp luật lấy từ cơ sở dữ liệu.

#### Các bước
1. Thêm quy tắc nghiêm ngặt: chỉ trả lời dựa trên văn bản pháp luật được cung cấp; không bịa đặt hay suy diễn ngoài luồng.
2. Thêm phương án dự phòng: nếu văn bản được cung cấp không đủ, nói rõ là chưa đủ căn cứ.
3. Test bằng câu hỏi ngoài phạm vi (ví dụ câu hỏi về thuế).

![Câu hỏi ngoài phạm vi được xử lý đúng](/images/5-Workshop/5.3-Prompt/context-constraint-test.png)

#### Kiểm tra
Câu hỏi ngoài phạm vi nhận câu trả lời 'chưa đủ căn cứ' thay vì câu trả lời bịa.