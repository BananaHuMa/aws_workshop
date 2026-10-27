---
title: "Nhật ký công việc Tuần 5"
date: 2026-10-18
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---
### Mục tiêu Tuần 5:

* Nắm vững bộ nhớ đệm trong RAM (in-memory caching) và quản lý dữ liệu bằng Amazon ElastiCache for Redis.
* Triển khai tổ chức tài nguyên và tự động hóa hiệu quả bằng Gắn thẻ (Tagging) và Nhóm tài nguyên (Resource Groups) của AWS.
* Quản lý các instance EC2 một cách bảo mật và ở quy mô lớn mà không cần mở cổng vào (inbound ports) bằng AWS Systems Manager (Session Manager, Patch Manager, Run Command).
* Hiểu và mô phỏng quy trình sao chép và chuyển đổi dự phòng (failover) trong khôi phục sau thảm họa bằng AWS Elastic Disaster Recovery (DRS).

### Các nhiệm vụ sẽ thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | - **Amazon ElastiCache for Redis:** <br>&emsp; + Tạo subnet groups và triển khai các cụm Redis (Tắt & Bật chế độ Cluster) <br>&emsp; + Khám phá các endpoints qua Console và AWS CLI <br>&emsp; + Tích hợp với Python (Boto3) SDK <br>&emsp; + Thực hành các thao tác Redis: Strings, Hashes, Pub/Sub và Streams | 10/12/2026 | 10/12/2026 | <https://000061.awsstudygroup.com/> |
| 2 | - **Quản lý tài nguyên:** <br>&emsp; + Áp dụng và quản lý Tags trên các instance EC2 qua Console và AWS CLI <br>&emsp; + Lọc tài nguyên theo tags <br>&emsp; + Tạo và quản lý AWS Resource Groups dựa trên Tag | 10/12/2026 | 10/12/2026 | <https://000027.awsstudygroup.com/> |
| 3 | - **AWS Systems Manager:** <br>&emsp; + Cấu hình VPC, subnets và Security Groups cho SSM <br>&emsp; + Gắn vai trò IAM `AmazonSSMManagedInstanceCore` cho các instance Windows EC2 <br>&emsp; + Thực hiện quét và cài đặt bản vá bằng Patch Manager <br>&emsp; + Chạy các script PowerShell qua Run Command | 10/15/2026 | 10/15/2026 | <https://000031.awsstudygroup.com/> |
| 4 | - **AWS Elastic Disaster Recovery (DRS):** <br>&emsp; + Triển khai hạ tầng cơ sở qua CloudFormation <br>&emsp; + Cấu hình cài đặt sao chép mặc định và vai trò IAM cho agent <br>&emsp; + Cài đặt các agent sao chép trên máy chủ nguồn <br>&emsp; + Cấu hình Launch Templates và thực hiện Diễn tập Failover (Failover Drill) | 10/16/2026 | 10/16/2026 | <https://000100.awsstudygroup.com/> |

### Thành tựu Tuần 5:

* **Thành thạo ElastiCache & Redis:** 
  * Triển khai và quản lý thành công các cụm Redis ở cả cấu hình Tắt và Bật chế độ Cluster.
  * Khám phá và sử dụng các endpoint Primary, Reader và Configuration thông qua cả AWS Console và CLI.
  * Phát triển các script Python (Boto3) để tạo cụm theo chương trình, quản lý Kiểm soát truy cập dựa trên vai trò (RBAC) và thực hiện các thao tác Redis nâng cao bao gồm thao tác String/Hash, nhắn tin Pub/Sub và xử lý Stream đa luồng.

* **Tổ chức tài nguyên:** 
  * Áp dụng các chiến lược gắn thẻ nhất quán (cặp Key-Value) cho các instance EC2 để phân bổ chi phí và theo dõi môi trường.
  * Tạo và sử dụng AWS Resource Groups để lọc và quản lý các bộ sưu tập tài nguyên dựa trên tiêu chí tag, hợp lý hóa các tác vụ quản trị.

* **Quản lý dựa trên Agent an toàn (Systems Manager):** 
  * Loại bỏ nhu cầu truy cập SSH/RDP truyền thống bằng cách cấu hình AWS Systems Manager Session Manager.
  * Gán thành công các vai trò IAM của SSM cho các instance Windows và xác minh kết nối qua Fleet Manager.
  * Tự động hóa việc vá lỗi hệ điều hành bằng Patch Manager và thực thi các lệnh PowerShell từ xa trên nhiều instance bằng Run Command, với đầu ra được ghi nhật ký vào S3.

* **Mô phỏng Khôi phục sau Thảm họa (DRS):** 
  * Cung cấp một môi trường tại chỗ (on-premises) được mô phỏng và cấu hình cài đặt sao chép mặc định của AWS DRS.
  * Cài đặt và cấu hình agent sao chép DRS trên các máy chủ Linux nguồn, theo dõi quá trình đồng bộ hóa ban đầu và tạo đĩa staging cho đến khi đạt trạng thái "Healthy" (Khỏe mạnh).
  * Định nghĩa các EC2 Launch Templates cho các instance được khôi phục và thực hiện thành công một Diễn tập Failover (Failover Drill) không gây gián đoạn, xác minh việc cung cấp biệt lập các instance web và cơ sở dữ liệu được khôi phục.

* **Xuất sắc trong Vận hành:** Luôn tuân thủ nguyên tắc đặc quyền tối thiểu (principle of least privilege) và thực hiện dọn dẹp tài nguyên toàn diện (chấm dứt các instance, xóa các cụm và xóa các CloudFormation stacks) để ngăn chặn chi phí phát sinh ngoài ý muốn.