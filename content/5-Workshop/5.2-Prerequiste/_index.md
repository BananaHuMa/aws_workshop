---
title : "Prerequisite"
date : 2026-01-01 
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

#### AWS account and region
All resources are created in one region: **ap-southeast-2** (Asia Pacific – Sydney), as seen in the website URL. Enable MFA on the root user and work with an IAM user, not root.

#### IAM role for Lambda
Lambda needs permissions to read the `LegalArticles` table and write logs to CloudWatch. Replace `<ACCOUNT_ID>` with your actual AWS account ID.

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