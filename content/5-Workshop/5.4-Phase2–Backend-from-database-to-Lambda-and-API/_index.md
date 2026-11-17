---
title : "Phase 2 – Backend: from database to Lambda and API"
date : 2026-01-01
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

#### Overview

+ In this section, you will build a serverless backend that retrieves legal articles, calls the LLM, and exposes a stable API. 

+ **Key components of this phase:**
    + **Knowledge Base (DynamoDB):** Stores the legal articles (Decree 13/2023/ND-CP) for keyword-based retrieval.
    + **Compute (AWS Lambda):** Executes the Python logic to query the database, assemble the prompt, and call the external Groq API.
    + **API Layer (API Gateway):** Provides a public HTTPS endpoint with CORS enabled and standardized error handling for the frontend to consume.
    + **Monitoring (CloudWatch):** Captures logs and metrics to track performance, response times, and troubleshoot errors.

![Backend architecture overview](/images/5-Workshop/5.4-Backend/overview.png)