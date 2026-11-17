---
title : "Phase 1 – Prompt setup and RAG mechanism"
date : 2026-01-01
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Prompt and RAG design

In this section, you will define how the language model receives and handles legal data before writing any code. You will build a system prompt to set the model's role, establish strict context constraints to prevent hallucinations, and define the input structure for injecting DynamoDB data into the prompt. This design work will be tested in the Groq playground before being implemented in the Lambda function.

![overview](/images/5-Workshop/5.3-Prompt/overview.png)

#### Content

- [Build a role-defining system prompt](5.3.1-Build-a-role-defining-system-prompt/_index.md)
- [Set the context constraint](5.3.2-Set-the-context-constraint/_index.md)
- [Define the input structure](5.3.3-Define-the-input-structure/_index.md)