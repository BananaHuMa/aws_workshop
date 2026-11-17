---
title : "Các bước chuẩn bị"
date : 2026-01-01 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

#### Tài khoản AWS và region
Toàn bộ tài nguyên tạo trong một region: **ap-southeast-2** (Asia Pacific – Sydney), theo URL của website. Bật MFA cho root và làm việc bằng IAM user, không dùng root.

#### IAM role cho Lambda
Lambda cần quyền đọc bảng `LegalArticles` và ghi log vào CloudWatch. Thay `<ACCOUNT_ID>` bằng ID tài khoản AWS thực tế của bạn.

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "logs:CreateLogGroup",
            "Resource": "arn:aws:logs:ap-southeast-2:<ACCOUNT_ID>:*"
        },
        {
            "Effect": "Allow",
            "Action": [
                "logs:CreateLogStream",
                "logs:PutLogEvents"
            ],
            "Resource": [
                "arn:aws:logs:ap-southeast-2:<ACCOUNT_ID>:log-group:/aws/lambda/legal-ai-chat-lambda:*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "dynamodb:Scan",
                "dynamodb:Query",
                "dynamodb:GetItem"
            ],
            "Resource": "arn:aws:dynamodb:ap-southeast-2:<ACCOUNT_ID>:table/LegalArticles"
        }
    ]
}