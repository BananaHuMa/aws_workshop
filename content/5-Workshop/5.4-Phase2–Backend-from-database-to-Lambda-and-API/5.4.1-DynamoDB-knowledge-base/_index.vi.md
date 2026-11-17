---
title : "Xây dựng Knowledge Base trên DynamoDB"
date : 2026-01-01 
weight : 1
chapter : false
pre : " <b> 5.4.1 </b> "
---

#### Mục tiêu
Lưu các điều luật vào bảng mà Lambda truy vấn được.

#### Các bước
1. Tạo bảng DynamoDB `LegalArticles`.
2. Thiết kế cấu trúc item (ví dụ: số điều, tiêu đề, nội dung, từ khóa).
3. Nạp các điều luật trích xuất từ Nghị định 13/2023/NĐ-CP, bao gồm các quy định về sử dụng dữ liệu CCCD, dữ liệu cá nhân và xử lý vi phạm.
4. Kiểm tra số lượng item so với tài liệu nguồn.

*Hạn chế: Việc tra cứu dựa trên từ khóa, nên một câu hỏi sử dụng cách diễn đạt khác có thể bỏ sót điều luật đúng.*

![Bảng DynamoDB LegalArticles](/images/5-Workshop/5.4-Backend/dynamodb-table.png)

![Các item mẫu trong bảng](/images/5-Workshop/5.4-Backend/dynamodb-items.png)

#### Kiểm tra
Bảng trả về các điều luật mong đợi khi được quét trong console.