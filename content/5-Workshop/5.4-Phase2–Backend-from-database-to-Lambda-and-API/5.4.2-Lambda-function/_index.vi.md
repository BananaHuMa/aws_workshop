---
title : "Lập trình hàm AWS Lambda (logic RAG & Groq API)"
date : 2026-01-01 
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

#### Mục tiêu
Truy xuất ngữ cảnh luật và sinh câu trả lời trong một hàm Python.

#### Các bước
1. Tạo hàm Lambda Python với IAM role từ mục 5.2.
2. Viết hàm `retrieve_legal_context`: truy vấn DynamoDB bằng các từ khóa từ câu hỏi.
3. Gọi Groq API (model `qwen/qwen3.8-27b`) với system prompt, ngữ cảnh luật và câu hỏi.
4. Đặt `GROQ_API_KEY` làm biến môi trường.
5. Tăng timeout lên trên mức mặc định 3 giây để cuộc gọi LLM có thể hoàn tất.
6. Lưu code cuối cùng vào repository.

![Tổng quan hàm Lambda](/images/5-Workshop/5.4-Backend/lambda-function.png)

![Biến môi trường](/images/5-Workshop/5.4-Backend/lambda-env.png)

#### Kiểm tra
Một test event trả về JSON body chứa câu trả lời.