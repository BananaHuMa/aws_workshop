---
title: "Blog 2"
date: 2026-10-27
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---

# MỚI HỌC AWS CẦN LƯU Ý GÌ ĐỂ KHÔNG "GIẬT MÌNH" VÌ HÓA ĐƠN CUỐI THÁNG?

Một trong những tình huống quen thuộc với người mới bắt đầu trải nghiệm AWS là lỡ tay bật một tài nguyên thử nghiệm rồi quên tắt, dẫn đến hóa đơn bất ngờ vào cuối tháng. Việc kiểm soát chi phí không chỉ giúp bạn yên tâm thực hành mà còn là kỹ năng cơ bản và quan trọng trong quản trị hạ tầng Cloud.

Những điểm chính cần biết:

* **Thiết lập AWS Budgets & Billing Alerts**: Cấu hình ngưỡng ngân sách an toàn (ví dụ: $5 hoặc $10). Hệ thống sẽ tự động gửi email cảnh báo khi chi phí thực tế hoặc dự báo vượt quá ngưỡng này, giúp phát hiện kịp thời các tài nguyên chạy ngầm.
* **Tận dụng AWS Free Tier đúng cách**: Nắm rõ các điều kiện đi kèm. Ví dụ: EC2 miễn phí 750 giờ/tháng cho dòng t2.micro hoặc t3.micro. Chạy đồng thời 2 instance sẽ bị tính phí gấp đôi và nhanh chóng vượt mức miễn phí. Luôn kiểm tra kỹ giới hạn dung lượng của S3 và EBS.
* **Dọn dẹp tài nguyên không sử dụng**: Tắt hoặc xóa EC2 instance khi không làm việc. Lưu ý Elastic IP chỉ miễn phí khi được gán vào một instance đang ở trạng thái Running (nếu ngắt kết nối hoặc gán vào instance Stopped, bạn vẫn bị tính phí). Đừng quên xóa các Unattached EBS Volumes và Snapshots để tránh phí lưu trữ ẩn.
* **Theo dõi chi tiết với AWS Cost Explorer**: Sử dụng công cụ trực quan này để phân tích chi phí theo thời gian, theo dịch vụ hoặc theo Tag. Thói quen kiểm tra báo cáo chi phí 1-2 lần/tuần giúp bạn nhanh chóng phát hiện các dịch vụ đang tiêu tốn ngân sách bất thường.

Tối ưu và kiểm soát chi phí là một phần không thể thiếu trong tư duy làm việc với Cloud Computing. Thiết lập hạ tầng an toàn ngay từ đầu sẽ giúp bạn thoải mái học tập và thử nghiệm các dịch vụ AWS mà không phải lo lắng về vấn đề hóa đơn.

Link: https://www.facebook.com/groups/awsstudygroupfcj/posts/2317495209015438/?notif_id=1793075766463069&notif_t=group_post_approved&ref=notif