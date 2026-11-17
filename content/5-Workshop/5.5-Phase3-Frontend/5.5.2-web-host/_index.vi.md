---
title : "Host trang trên S3"
date : 2026-01-01 
weight : 2
chapter : false
pre : " <b> 5.5.2 </b> "
---

#### Mục tiêu
Công khai `index.html` dưới dạng static website.

#### Các bước
1. Tạo bucket `ai-legal-assistant-frontend-hau` ở region `ap-southeast-2`.
2. Tải `index.html` lên.
3. Bật **Static website hosting** với `index.html` làm index document.
4. Cho phép đọc công khai riêng bucket này:
   - Tắt **Block Public Access** cho bucket này.
   - Thêm **bucket policy** chỉ đọc.
5. Mở website endpoint.

{{% notice warning %}}
Bucket được đặt công khai có chủ đích, nên chỉ được chứa **các file frontend**. Tuyệt đối không đưa API key vào `index.html`. S3 website endpoint chỉ phục vụ **HTTP**.
{{% /notice %}}

![Cài đặt Static website hosting](/images/5-Workshop/5.5-Frontend/s3-website.png)

![Bucket policy cho phép đọc công khai](/images/5-Workshop/5.5-Frontend/s3-bucket-policy.png)

#### Kiểm tra
Endpoint `http://ai-legal-assistant-frontend-hau.s3-website-ap-southeast-2.amazonaws.com/` mở được trang.