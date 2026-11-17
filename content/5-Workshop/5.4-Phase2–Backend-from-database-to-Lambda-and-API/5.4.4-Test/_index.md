---
title : "Test the backend"
date : 2026-01-01 
weight : 4
chapter : false
pre : " <b> 5.4.4 </b> "
---

#### Goal
Prove the backend works before connecting any interface.

#### Steps
1. Send a POST with `curl` using a sample question.
2. Open CloudWatch Logs and check the response time, the returned data, and the JSON structure.
3. Test the error cases: empty question (400) and, if possible, a rate-limit case (429).

```bash
curl -X POST "<API_URL>" \
  -H "Content-Type: application/json" \
  -d '{"question": "Does using ID card data for advertising get fined?"}'