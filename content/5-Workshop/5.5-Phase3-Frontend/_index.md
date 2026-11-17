---
title : "Frontend – S3 static website"
date : 2026-01-01
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

#### Overview

+ In this section, you will build and deploy the user-facing chat interface that connects to the backend API. The frontend is a single static HTML page hosted on Amazon S3, keeping costs near zero while leveraging S3's native static website hosting.

+ **Key aspects of this phase:**
    + **Static UI (`index.html`):** A lightweight chat page built with HTML, CSS, and JavaScript that uses `fetch` to call the API Gateway endpoint.
    + **Hosting (Amazon S3):** The page is served as a public static website, with Block Public Access disabled only for this bucket and a read-only bucket policy applied.
    + **Integration:** The frontend is wired to the real backend API URL and handles loading states and error codes (400, 429, 502/504) gracefully.
    + **Safety:** A visible disclaimer reminds users that answers are preliminary and not official legal advice.

![Frontend architecture overview](/images/5-Workshop/5.5-Frontend/overview.png)

#### Content

- [Build the chat page](5.5.1-build-chat-page/)
- [Host the page on S3](5.5.2-host-on-s3/)
- [Connect to the API and test end-to-end](5.5.3-connect-and-test/)