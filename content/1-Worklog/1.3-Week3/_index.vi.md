---
title: "Nhật ký công việc Tuần 3"
date: 2026-10-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu Tuần 3:

* Nắm vững các kỹ thuật di chuyển lên hybrid cloud bằng AWS VM Import/Export.
* Triển khai giám sát và quan sát (observability) toàn diện bằng Amazon CloudWatch.
* Xây dựng các quy trình tự động hóa serverless để quản lý vòng đời hạ tầng bằng AWS Lambda và EventBridge.
* Triển khai và quản trị môi trường Active Directory hybrid bằng AWS Managed Microsoft AD.

### Các công việc thực hiện trong tuần này:
| Ngày | Công việc | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | - **VM Import/Export:** Chuẩn bị máy ảo Ubuntu VMware tại chỗ (on-prem), tải tệp `.vmdk` lên S3, tạo IAM role `vmimport`, import thành AMI và triển khai dưới dạng EC2. <br> - **VM Export:** Cấu hình S3 ACL/policy, export EC2 instance trở lại định dạng VMDK và dọn dẹp toàn bộ tài nguyên. | 28/09/2026 | 28/09/2026 | [VM Import/Export Lab](https://000014.awsstudygroup.com/) |
| 2 | - **Giám sát CloudWatch:** Triển khai CloudWatch workshop stack, phân tích Metrics (biểu thức Search/Math, Dynamic labels), truy vấn Logs Insights, tạo Metric Filters, cấu hình Alarms với thông báo SNS và Dashboards. <br> - **S3 & CloudFront:** Triển khai website tĩnh, cấu hình CloudFront với OAC, kiểm tra độ trễ tại Edge, bật Versioning và cấu hình Cross-Region Replication (CRR). | 29/09/2026 | 29/09/2026 | [CloudWatch Lab](https://000008.awsstudygroup.com/), [S3/CloudFront Lab](https://000094.awsstudygroup.com/) |
| 3 | - **Tự động hóa Serverless:** Tạo VPC, EC2 instance và Slack Incoming Webhook. Phát triển các hàm Lambda bằng Python (`auto-start`/`auto-stop`) với IAM role tùy chỉnh. <br> - **EventBridge & Kiểm thử:** Lập lịch kích hoạt Lambda, kiểm tra việc chuyển đổi trạng thái EC2, xác minh thông báo Slack và thực hiện dọn dẹp toàn bộ tài nguyên. | 30/09/2026 | 30/09/2026 | [Lambda Automation Lab](https://000022.awsstudygroup.com/) |
| 4 | - **Triển khai Managed AD:** Triển khai hạ tầng mạng cơ sở bằng CloudFormation, khởi tạo AWS Managed Microsoft AD (Standard Edition) trong các private subnet. <br> - **Thiết lập EC2:** Khởi chạy Bastion Host public và Windows Server 2022 AD-Manager trong private subnet, cấu hình tự động tham gia domain (domain join) thông qua IAM instance profile. | 02/10/2026 | 02/10/2026 | [Managed AD Lab](https://000095.awsstudygroup.com/) |
| 5 | - **Cấu hình & Kiểm thử AD:** RDP chuyển tiếp (pivot) qua Bastion đến AD-Manager, xác minh việc tham gia domain, cấu hình tệp `hosts`, cài đặt AD Administrative Tools và thực hiện kiểm tra ping hai chiều (theo IP/Hostname). <br> - **Dọn dẹp:** Terminate các EC2 instance, xóa Managed AD và gỡ bỏ CloudFormation stack. | 04/10/2026 | 04/10/2026 | [Managed AD Lab](https://000095.awsstudygroup.com/) |

### Kết quả đạt được trong Tuần 3:

* **Di chuyển Hybrid Cloud:** Nắm vững dịch vụ AWS VM Import/Export, bao gồm việc tạo IAM trust policy tùy chỉnh, cấu hình S3 bucket và di chuyển bằng CLI các workload VMware tại chỗ lên AWS AMI (và ngược lại).
* **Observability nâng cao:** Thành thạo Amazon CloudWatch thông qua việc tạo Metric Filters tùy chỉnh từ log thô, sử dụng Logs Insights để truy vấn nâng cao và xây dựng Dashboards tổng hợp cùng Alarms tích hợp SNS nhằm phản ứng chủ động với sự cố.
* **Tự động hóa hạ tầng Serverless:** Thiết kế và triển khai giải pháp quản lý vòng đời EC2 hoàn toàn tự động bằng AWS Lambda (Python) và EventBridge Scheduler, tích hợp liền mạch với Slack Incoming Webhooks để gửi cảnh báo vận hành theo thời gian thực.
* **Dịch vụ thư mục doanh nghiệp:** Triển khai thành công AWS Managed Microsoft Active Directory trên nhiều Availability Zone. Cấu hình chuyển tiếp mạng an toàn (RDP qua Bastion Host), tự động hóa việc tham gia domain, đồng thời xác thực việc phân giải DNS hybrid và các công cụ quản trị AD.
* **Tối ưu chi phí & Bảo mật:** Áp dụng nhất quán nguyên tắc đặc quyền tối thiểu (IAM role tùy chỉnh, Security Group giới hạn) và thực hiện quy trình dọn dẹp tài nguyên chặt chẽ, có hệ thống (xóa CloudFormation stack, hủy đăng ký AMI, làm trống S3 bucket) để tránh phát sinh chi phí ngoài ý muốn.
* **Tính sẵn sàng cao & Khôi phục thảm họa:** Cấu hình S3 Cross-Region Replication (CRR) và Bucket Versioning, đảm bảo độ bền dữ liệu và khả năng khôi phục nhanh cho các tài nguyên web tĩnh.