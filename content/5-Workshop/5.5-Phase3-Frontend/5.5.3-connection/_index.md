---
title : "Connect to the API and test end-to-end"
date : 2026-01-01 
weight : 3
chapter : false
pre : " <b> 5.5.3 </b> "
---

#### Goal
Make the live page call the real backend.

#### Steps
1. Set the API invoke URL in `index.html` and re-upload it to the S3 bucket.
2. Open the live site and ask the sample question.
3. Open the browser **developer console** and check there is no CORS error.
4. Check the request in **CloudWatch Logs**.

![An answer displayed on the live site](/images/5-Workshop/5.5-Frontend/e2e-result.png)

#### Verify
Question → grounded answer on the page, with a matching log entry.