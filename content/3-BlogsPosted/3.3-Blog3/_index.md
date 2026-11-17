---
title: "Blog 3"
date: 2026-10-27
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# BUILDING A SIMPLE, SECURE STATIC WEBSITE WITH S3 + CLOUDFRONT + ROUTE 53

When you finish a static website (pure HTML/CSS/JS or builds from React, Vue, Next.js), the next challenge is choosing a storage and distribution solution for the internet. The typical goals are: optimized costs, fast access speed, secure HTTPS support, and zero server management effort. The trio of Amazon S3 + Amazon CloudFront + Route 53 is the standardized architecture that solves this problem optimally.

Key points to know:

* **Step 1: File Storage with Amazon S3**: Create an S3 Bucket to hold the built static web source code. Configure the S3 Bucket Policy with appropriate access rights and enable Static website hosting to set default access files (e.g., index.html and 404.html).
* **Step 2: Acceleration & Security with Amazon CloudFront (CDN)**: Create a CloudFront Distribution and point the Origin to the newly created S3 Bucket. Data is cached at global Edge Locations to minimize latency. Integrate a free SSL/TLS certificate from AWS Certificate Manager (ACM) to enable HTTPS. Configure Origin Access Control (OAC) to block direct external access to the S3 Bucket, allowing traffic only through CloudFront.
* **Step 3: Domain Routing with Amazon Route 53**: Create a Hosted Zone for your custom domain on Route 53. Configure an A Record (Alias) to point the main domain or subdomain to the CloudFront Distribution address.
* **Technical Value**: Cost optimization (fully Serverless, monthly costs are near $0 for small projects), Scalability (CloudFront's CDN network automatically handles traffic spikes without infrastructure upgrades), and simplified operations (no need to worry about OS patching or periodic SSL certificate management).

This is one of the classic yet highly important hands-on practices, helping you master the mindset of combining fundamental AWS services to create a complete, secure, and industry-standard system.

Link: https://www.facebook.com/groups/awsstudygroupfcj/?multi_permalinks=2317669882331304&notif_id=1793105995816910&notif_t=feedback_reaction_generic&ref=notif