---
title : "Host the page on S3"
date : 2026-01-01 
weight : 2
chapter : false
pre : " <b> 5.5.2 </b> "
---

#### Goal
Publish `index.html` as a static website.

#### Steps
1. Create the bucket `ai-legal-assistant-frontend-hau` in `ap-southeast-2`.
2. Upload `index.html`.
3. Enable **Static website hosting** with `index.html` as the index document.
4. Allow public read of this bucket only:
   - Turn off **Block Public Access** for this bucket.
   - Add a read-only **bucket policy**.
5. Open the website endpoint.

{{% notice warning %}}
The bucket is public on purpose, so it may hold **only the frontend files**. Never put API keys in `index.html`. S3 website endpoints serve **HTTP only**.
{{% /notice %}}

![Static website hosting settings](/images/5-Workshop/5.5-Frontend/s3-website.png)

![Public-read bucket policy](/images/5-Workshop/5.5-Frontend/s3-bucket-policy.png)

#### Verify
The endpoint `http://ai-legal-assistant-frontend-hau.s3-website-ap-southeast-2.amazonaws.com/` loads the page.