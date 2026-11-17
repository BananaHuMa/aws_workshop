---
title : "Write the Lambda function (RAG logic + Groq API)"
date : 2026-01-01 
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

#### Goal
Retrieve legal context and generate the answer in one Python function.

#### Steps
1. Create the Python Lambda function with the IAM role from section 5.2.
2. Write `retrieve_legal_context`: query DynamoDB using keywords from the question.
3. Call the Groq API (model `qwen/qwen3.8-27b`) with the system prompt, the legal context, and the question.
4. Set `GROQ_API_KEY` as an environment variable.
5. Raise the timeout above the 3-second default so the LLM call can finish.
6. Save the final code in the repository.

![Lambda function overview](/images/5-Workshop/5.4-Backend/lambda-function.png)

![Environment variables](/images/5-Workshop/5.4-Backend/lambda-env.png)

#### Verify
A test event returns a JSON body containing an answer.