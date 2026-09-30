---
title: "Nhật ký công việc Tuần 1"
date: 2026-09-20
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu Tuần 1:

* Hiểu và triển khai các phương pháp hay nhất (best practices) cốt lõi về Quản lý Danh tính và Truy cập (IAM) của AWS.
* Thiết kế và triển khai các kiến trúc mạng VPC an toàn, có tính sẵn sàng cao (highly available).
* Nắm vững quy trình quản lý vòng đời của EC2 instance, bao gồm tạo AMI, thay đổi kích thước (resizing) và khôi phục key pair.
* Tận dụng Amazon S3 để lưu trữ trang web tĩnh, quản lý phiên bản (versioning) và sao chép đa vùng (cross-region replication), tích hợp với Amazon CloudFront để phân phối nội dung an toàn, độ trễ thấp.
* Thành thạo việc sử dụng AWS CLI và CloudShell để quản lý hạ tầng.

### Các nhiệm vụ cần thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | - **Quản lý IAM & Chi phí:** Tạo IAM Groups, Users, Roles và thực hành chuyển đổi vai trò (Role Switching).<br>- **5 Nhiệm vụ AWS:** Khởi tạo/dừng EC2, cấu hình Bedrock, thiết lập AWS Budgets, triển khai ứng dụng serverless Lambda, cấp phát RDS.<br>- **Mạng (Networking):** Tạo VPC ban đầu (`ASG`) với CIDR `10.10.0.0/16`. | 14/09/2026 | 14/09/2026 | [IAM & Budgets](https://000002.awsstudygroup.com/), [VPC](https://000003.awsstudygroup.com/3-prerequisite/3.1-createvpc/) |
| 2 | - **Mạng nâng cao:** Tạo Public/Private Subnets, Internet Gateway, Route Tables và các Security Group chuyên dụng.<br>- **Giám sát & Kết nối:** Bật VPC Flow Logs, triển khai EC2 instance Public/Private, cấu hình NAT Gateways có tính sẵn sàng cao, kiểm thử bằng Reachability Analyzer và thiết lập Site-to-Site VPN. | 15/09/2026 | 15/09/2026 | [VPC Networking](https://000003.awsstudygroup.com/3-prerequisite/), [EC2 & VPN](https://000003.awsstudygroup.com/4-createec2server/), [VPN](https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/) |
| 3 | - **Quản lý EC2:** Khởi tạo Windows Server 2025 & Amazon Linux 2023. Thực hiện Sysprep, tạo Custom AMI và thay đổi kích thước instance.<br>- **Khôi phục & Triển khai:** Khôi phục key pair bị mất qua SSM (Windows) và User Data (Linux). Thiết lập Ubuntu Desktop với RDP. Triển khai ứng dụng full-stack Node.js/MySQL trên cả hai môi trường hệ điều hành. | 17/09/2026 | 17/09/2026 | [EC2 Basics](https://000004.awsstudygroup.com/3-launchwindowsinstance/), [App Deployment](https://000004.awsstudygroup.com/6-awsfcjmanagement-linux/) |
| 4 | - **S3 & Phương pháp hay nhất về IAM:** Tạo S3 buckets. So sánh việc hardcode IAM Access Keys với việc sử dụng IAM Roles (Instance Profiles) an toàn hơn để EC2 truy cập S3.<br>- **Thành thạo CLI:** Thực hành các lệnh Linux cơ bản, chuyển tệp và quản lý tài nguyên bằng AWS CLI và CloudShell. | 18/09/2026 | 18/09/2026 | [IAM Roles](https://000048.awsstudygroup.com/3-iamroleec2/), [CloudShell & CLI](https://000049.awsstudygroup.com/2-basicfeature/) |
| 5 | - **Tính năng nâng cao của S3:** Cấu hình lưu trữ trang web tĩnh (Static Website Hosting) trên S3, quản lý Block Public Access và thiết lập object ACLs.<br>- **CloudFront & Khôi phục sau thảm họa (DR):** Tích hợp CloudFront với Origin Access Control (OAC). Bật S3 Versioning, di chuyển objects giữa các buckets và cấu hình Cross-Region Replication (CRR) để khôi phục sau thảm họa. | 20/09/2026 | 20/09/2026 | [Static Website](https://000057.awsstudygroup.com/3-staticwebsite/), [CloudFront](https://000057.awsstudygroup.com/7-cloudfront/), [CRR](https://000057.awsstudygroup.com/10-s3ccr/) |

### Thành tựu Tuần 1:

* **IAM & Bảo mật:** Triển khai thành công nguyên tắc đặc quyền tối thiểu (principle of least privilege) bằng cách quản lý quyền thông qua IAM Groups và Roles, loại bỏ nhu cầu sử dụng access keys dài hạn trong mã ứng dụng.
* **Kiến trúc Mạng:** Thiết kế và triển khai kiến trúc VPC đa vùng sẵn sàng (multi-AZ) với public/private subnets, NAT Gateways và kết nối Site-to-Site VPN an toàn.
* **Làm chủ Compute (Máy chủ):** Có kinh nghiệm thực tế với toàn bộ vòng đời của EC2, bao gồm tạo custom AMI, thay đổi kích thước instance và các kỹ thuật khôi phục nâng cao (SSM Run Command và inject EC2 User Data).
* **Lưu trữ & Phân phối nội dung:** Lưu trữ thành công trang web tĩnh trên S3, bảo mật bằng CloudFront Origin Access Control (OAC) và triển khai bảo vệ dữ liệu cấp doanh nghiệp sử dụng S3 Versioning và Cross-Region Replication (CRR).
* **Tự động hóa & CLI:** Thành thạo việc quản lý tài nguyên AWS theo chương trình (programmatically) bằng AWS CLI và CloudShell, cải thiện hiệu quả vận hành và khả năng tái lập.
* **Triển khai Ứng dụng:** Triển khai và kiểm thử thành công một ứng dụng web full-stack trên cả hai môi trường Amazon Linux 2023 và Windows Server 2025.