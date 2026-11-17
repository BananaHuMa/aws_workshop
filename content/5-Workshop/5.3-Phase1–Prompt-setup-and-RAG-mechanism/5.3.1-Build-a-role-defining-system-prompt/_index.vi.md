---
title : "Xây dựng System Prompt định hướng vai trò"
date : 2026-01-01 
weight : 1
chapter : false
pre : " <b> 5.3.1 </b> "
---

#### Mục tiêu
Ép mô hình đóng vai chuyên gia tư vấn pháp luật về các quy định tại Việt Nam, như Nghị định 13/2023/NĐ-CP.

#### Các bước
1. Viết câu định nghĩa vai trò (chuyên gia luật dữ liệu cá nhân Việt Nam).
2. Yêu cầu trả lời bằng tiếng Việt và nêu điều luật đã dùng.
3. Thêm disclaimer: câu trả lời sơ bộ, không phải tư vấn pháp lý chính thức.
4. Thử bản nháp trong Groq playground.

#### Mẫu tham khảo
Thay thế bằng prompt thực tế của nhóm:
> Bạn là chuyên gia tư vấn pháp lý về luật dữ liệu cá nhân Việt Nam.
> Trả lời bằng tiếng Việt và nêu rõ điều luật bạn dựa vào.
> Đây là câu trả lời sơ bộ, không phải tư vấn pháp lý chính thức.

![System prompt trong Groq playground](/images/5-Workshop/5.3-Prompt/system-prompt.png)

#### Kiểm tra
Mô hình trả lời đúng vai trò và giọng điệu mong muốn.