---
title: "Blog 3"
date: 2026-10-27
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# XÂY DỰNG TRANG WEB TĨNH ĐƠN GIẢN, BẢO MẬT VỚI S3 + CLOUDFRONT + ROUTE 53

Khi hoàn thành một trang web tĩnh (HTML/CSS/JS thuần hoặc các bản build từ React, Vue, Next.js), bài toán tiếp theo là lựa chọn giải pháp lưu trữ và phân phối lên internet. Mục tiêu đặt ra thường là: chi phí tối ưu, tốc độ truy cập nhanh, hỗ trợ HTTPS an toàn và không tốn công quản lý server. Bộ ba dịch vụ Amazon S3 + Amazon CloudFront + Route 53 là kiến trúc chuẩn hóa giúp giải quyết bài toán này một cách tối ưu.

Những điểm chính cần biết:

* **Bước 1: Lưu trữ tập tin với Amazon S3**: Khởi tạo S3 Bucket chứa mã nguồn web tĩnh đã build, cấu hình Bucket Policy hợp lý và bật tính năng Static website hosting (thiết lập file truy cập mặc định như index.html và 404.html).
* **Bước 2: Tăng tốc & Bảo mật với Amazon CloudFront (CDN)**: Tạo CloudFront Distribution và trỏ nguồn (Origin) về S3 Bucket. Dữ liệu được cache tại các Edge Location toàn cầu để giảm độ trễ. Tích hợp chứng chỉ SSL/TLS miễn phí từ AWS Certificate Manager (ACM) cho HTTPS và cấu hình OAC (Origin Access Control) để chặn truy cập trực tiếp vào S3, chỉ cho phép traffic đi qua CloudFront.
* **Bước 3: Định tuyến tên miền với Amazon Route 53**: Tạo Hosted Zone cho tên miền trên Route 53, sau đó cấu hình bản ghi A Record (dạng Alias) để trỏ tên miền chính hoặc subdomain về địa chỉ CloudFront Distribution.
* **Giá trị kỹ thuật**: Tối ưu chi phí (kiến trúc Serverless, chi phí hàng tháng gần như bằng 0 cho dự án nhỏ), khả năng mở rộng tự động (Scalability) nhờ mạng lưới CDN xử lý traffic đột biến, và đơn giản hóa vận hành (không cần vá lỗi OS hay quản lý SSL định kỳ).

Đây là một trong những bài thực hành kinh điển nhưng rất quan trọng, giúp bạn nắm vững tư duy kết hợp các dịch vụ cơ bản trên AWS để tạo nên một hệ thống hoàn chỉnh, bảo mật và chuẩn công nghiệp.

Link: https://www.facebook.com/groups/awsstudygroupfcj/?multi_permalinks=2317669882331304&notif_id=1793105995816910&notif_t=feedback_reaction_generic&ref=notif