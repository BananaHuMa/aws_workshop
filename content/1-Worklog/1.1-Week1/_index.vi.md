---
title: "Worklog Tổng hợp (Tuần 1 - Tuần 3)"
date: 2026-09-30
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

### Mục tiêu giai đoạn (Tuần 1 - Tuần 3):

* Nắm vững các dịch vụ AWS cốt lõi: IAM, EC2, VPC, S3, RDS, CloudWatch, Lambda và Lightsail.
* Thực hành triển khai hạ tầng mạng chuẩn production (Multi-AZ, NAT Gateway, Site-to-Site VPN).
* Triển khai, quản lý và bảo mật ứng dụng trên EC2 (Linux/Windows) và Lightsail.
* Thiết lập quy trình giám sát (Monitoring) và tự động hóa (Automation) vận hành hệ thống.
* Thực hành di chuyển máy ảo (VM Import/Export) và quản lý container cơ bản.

### Các công việc đã triển khai:

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2 (14/09) | - **IAM & Bảo mật:** Tạo IAM Group, User, Role, thực hành Switch Roles.<br>- **Tối ưu chi phí:** Hoàn thành 5 tác vụ "Money-Making", thiết lập AWS Budgets.<br>- **Networking:** Khởi tạo VPC (`ASG`, CIDR `10.10.0.0/16`). | 14/09/2026 | 14/09/2026 | [Lab 000002](https://000002.awsstudygroup.com/), [Lab 000003](https://000003.awsstudygroup.com/) |
| 3 (15/09) | - **VPC Nâng cao:** Tạo Public/Private Subnets (Multi-AZ), Internet Gateway, Route Table, Security Groups.<br>- **Giám sát mạng:** Bật VPC Flow Logs.<br>- **EC2 & Kết nối:** Launch EC2 Public/Private, SSH Bastion, NAT Gateway (High Availability), Reachability Analyzer.<br>- **Hybrid Cloud:** Cấu hình Site-to-Site VPN (IKEv2, BGP). | 15/09/2026 | 15/09/2026 | [Lab 000003](https://000003.awsstudygroup.com/) |
| 5 (17/09) | - **EC2 Management:** Launch Windows Server 2025 & Amazon Linux 2023, kết nối RDP/SSH (MobaXterm, PuTTY).<br>- **Lifecycle:** Resize instance, tạo EBS Snapshot, Custom AMI (Sysprep), Launch từ AMI.<br>- **Khôi phục truy cập:** Sử dụng SSM (Windows) và User Data (Linux) khi mất Key Pair.<br>- **App Deployment:** Triển khai ứng dụng Node.js/MySQL trên Linux và Windows (XAMPP). | 17/09/2026 | 17/09/2026 | [Lab 000004](https://000004.awsstudygroup.com/) |
| 6 (18/09) | - **S3 & IAM Access Key:** Tạo S3 Bucket, tạo IAM User có Programmatic Access, thực hành upload file qua Python (boto3) với hardcoded key.<br>- **IAM Role for EC2:** Gán Instance Profile, sửa script để sử dụng temporary credentials an toàn.<br>- **CloudShell & CLI:** Thực hành lệnh Linux cơ bản, quản lý tài nguyên qua AWS CLI. | 18/09/2026 | 18/09/2026 | [Lab 000048](https://000048.awsstudygroup.com/), [Lab 000049](https://000049.awsstudygroup.com/) |
| CN (20/09) | - **S3 Static Website:** Enable hosting, cấu hình Block Public Access và ACLs.<br>- **CloudFront:** Tạo Distribution, cấu hình Origin Access Control (OAC) để bảo mật S3, kiểm tra hiệu suất Edge Location.<br>- **S3 Advanced:** Bật Versioning, Move Objects, cấu hình Cross-Region Replication (CRR). | 20/09/2026 | 20/09/2026 | [Lab 000057](https://000057.awsstudygroup.com/) |
| 3 (22/09) | - **RDS Deployment:** Tạo VPC, SG, Subnet Group cho RDS. Launch MySQL Multi-AZ instance.<br>- **App Integration:** Kết nối EC2 với RDS, seeding database, deploy app qua PM2.<br>- **Backup & Restore:** Thực hành tạo DB Snapshot và khôi phục sang instance mới.<br>- **Cleanup:** Dọn dẹp tài nguyên RDS và VPC. | 22/09/2026 | 22/09/2026 | [Lab 000005](https://000005.awsstudygroup.com/) |
| 5 (24/09) | - **Lightsail Apps:** Deploy Highly Available Database, WordPress, PrestaShop, Akaunting.<br>- **Networking & Security:** Gán Static IP, cấu hình domain, hardening (disable SSH port 22).<br>- **Operations:** Tạo Manual/Automated Snapshots, Scale-up instance, cấu hình CloudWatch Alarms.<br>- **Lightsail Containers:** Tạo Container Service, deploy public (Nginx) và custom image.<br>- **CLI Automation:** Quản lý S3, SNS, IAM, Networking và EC2 hoàn toàn bằng AWS CLI. | 24/09/2026 | 24/09/2026 | [Lab 000045](https://000045.awsstudygroup.com/), [Lab 000046](https://000046.awsstudygroup.com/), [Lab 000011](https://000011.awsstudygroup.com/) |
| CN (28/09) | - **VM Import/Export:** Chuẩn bị VM Ubuntu trên VMware, upload `.vmdk` lên S3, tạo IAM Role `vmimport`, import thành AMI và launch EC2.<br>- **Export:** Cấu hình S3 ACL/Policy, export EC2 instance thành file VMDK để deploy on-premises.<br>- **Cleanup:** Dọn dẹp AMI, Volume, S3 và EC2. | 28/09/2026 | 28/09/2026 | [Lab 000014](https://000014.awsstudygroup.com/) |
| 3 (29/09) | - **CloudWatch Workshop:** Deploy stack qua CloudFormation.<br>- **Monitoring:** Xem Metrics, sử dụng Search/Math Expressions, Dynamic Labels.<br>- **Logs & Alarms:** Truy vấn Logs Insights, tạo Metric Filter, thiết lập Alarm với SNS Notification, xây dựng Dashboard.<br>- **Cleanup:** Xóa CloudFormation Stack. | 29/09/2026 | 29/09/2026 | [Lab 000008](https://000008.awsstudygroup.com/) |
| 4 (30/09) | - **Lambda Automation:** Tạo 2 Lambda Functions (Start/Stop EC2) với Python, tích hợp Slack Incoming Webhook.<br>- **EventBridge:** Lập lịch chạy tự động (Rate-based schedule).<br>- **Testing & Cleanup:** Kiểm thử trigger, xác nhận thông báo Slack, xóa toàn bộ tài nguyên (Lambda, EventBridge, IAM Role, EC2, VPC, Slack App). | 30/09/2026 | 30/09/2026 | [Lab 000022](https://000022.awsstudygroup.com/) |

### Kết quả đạt được:

* **Quản trị định danh & Bảo mật:** Thành thạo tạo và quản lý IAM Users, Groups, Roles, áp dụng nguyên tắc đặc quyền tối thiểu (least privilege) và chuyển đổi an toàn từ Access Key sang IAM Roles cho EC2.
* **Kiến trúc mạng (Networking):** Thiết kế và triển khai thành công hạ tầng VPC chuẩn production: Multi-AZ Subnets, NAT Gateway (High Availability), Internet Gateway, Route Tables, Security Groups chặt chẽ, VPC Flow Logs và Site-to-Site VPN.
* **Điện toán (Compute):** Vận hành linh hoạt EC2 (Amazon Linux, Windows Server, Ubuntu), thành thạo các thao tác: Resize, tạo Snapshot/AMI, khôi phục truy cập khẩn cấp (SSM, User Data), và tự động hóa Start/Stop bằng Lambda + EventBridge + Slack.
* **Lưu trữ (Storage):** Quản lý chuyên sâu Amazon S3: Static Website Hosting, Versioning, Cross-Region Replication (CRR), Move Objects, và bảo mật tuyệt đối bằng CloudFront Origin Access Control (OAC).
* **Cơ sở dữ liệu (Database):** Triển khai và quản lý Amazon RDS (MySQL Multi-AZ) và Lightsail Database, thực hành sao lưu (Snapshot) và khôi phục (Restore) thành công.
* **Giám sát (Observability):** Sử dụng thành thạo CloudWatch để theo dõi Metrics, truy vấn Logs Insights, tạo Metric Filters từ log, thiết lập Alarms gửi cảnh báo qua SNS và tổng hợp trên Dashboard.
* **Di chuyển & Container:** Thực hiện thành công quy trình VM Import/Export giữa môi trường on-premises (VMware) và AWS, đồng thời nắm được cách deploy container trên Lightsail.
* **Kỷ luật vận hành:** Tuân thủ nghiêm ngặt quy trình dọn dẹp tài nguyên (Cleanup) sau mỗi bài lab để tránh phát sinh chi phí ngoài ý muốn.