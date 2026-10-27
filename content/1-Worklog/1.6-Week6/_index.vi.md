---
title: "Nhật ký công việc Tuần 6"
date: 2026-10-25
weight: 6
chapter: false
pre: " <b> 6. </b> "
---
### Mục tiêu Tuần 6:

* Nắm vững Cơ sở hạ tầng dưới dạng mã (IaC) nâng cao bằng AWS CDK và CloudFormation.
* Triển khai các chính sách quản trị chi phí IAM nâng cao và hạn chế tài nguyên.
* Tận dụng AWS Systems Manager để quản lý instance an toàn dựa trên agent mà không cần mở cổng vào (inbound ports).
* Áp dụng các phương pháp hay nhất về xuất sắc trong vận hành (operational excellence) bằng Compute Optimizer, VPC Flow Logs và Data Lifecycle Manager (DLM).

### Các nhiệm vụ sẽ thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | - **AWS Systems Manager (Session Manager):** <br>&emsp; + Cấu hình VPC, Subnets và Security Groups <br>&emsp; + Khởi chạy các instance EC2 Linux (Public) và Windows (Private) <br>&emsp; + Tạo và gắn vai trò IAM SSM <br>&emsp; + Cấu hình VPC Interface Endpoints (SSM, SSMMESSAGES, EC2MESSAGES) <br>&emsp; + Bật ghi nhật ký S3 cho Session Manager <br>&emsp; + Thực hành Chuyển tiếp cổng (Port Forwarding) cho RDP qua CLI | 21/10/2026 | 21/10/2026 | <https://000058.awsstudygroup.com/> |
| 2 | - **AWS CDK Basic 2:** <br>&emsp; + Thiết lập môi trường từ xa CloudShell & VSCode <br>&emsp; + Triển khai ECS, ALB và API Gateway qua CDK <br>&emsp; + Tích hợp Lambda và S3 qua CDK <br>&emsp; + Tái cấu trúc codebase bằng Nested Stacks <br>&emsp; + Dọn dẹp tài nguyên | 22/10/2026 | 22/10/2026 | <https://000076.awsstudygroup.com/> |
| 3 | - **CloudFormation & Kiến trúc 3 tầng:** <br>&emsp; + Thiết lập môi trường Cloud9 <br>&emsp; + Triển khai Lambda và VPC/EC2 qua các template CFN <br>&emsp; + Triển khai Kiến trúc Web 3 tầng (Web, App, DB) <br>&emsp; + Xác thực kết nối và quyền truy cập giữa các tầng <br>&emsp; + Dọn dẹp tài nguyên | 23/10/2026 | 23/10/2026 | <https://000102.awsstudygroup.com/> |
| 4 | - **Xuất sắc trong Vận hành & Quản trị IAM:** <br>&emsp; + Tối ưu hóa kích thước EC2 (Right-Sizing): Cài đặt CloudWatch Agent, xem xét các đề xuất của Compute Optimizer <br>&emsp; + Giám sát mạng: Tạo và bật VPC Flow Logs gửi về CloudWatch <br>&emsp; + IAM: Ủy quyền truy cập Billing Console cho các người dùng/nhóm IAM cụ thể | 24/10/2026 | 24/10/2026 | <https://000032.awsstudygroup.com/> <br> <https://000074.awsstudygroup.com/> <br> <https://000075.awsstudygroup.com/> |
| 5 | - **Quản trị chi phí IAM nâng cao & DLM:** <br>&emsp; + Tạo và gắn các chính sách để giới hạn tài nguyên theo: Vùng (Region), Dòng instance EC2, Kích thước instance và Loại ổ đĩa EBS <br>&emsp; + Kiểm thử hiệu quả của chính sách <br>&emsp; + Amazon DLM: Cấu hình lịch trình chính sách đơn và đa dạng để tự động lưu trữ EBS Snapshot <br>&emsp; + Dọn dẹp cuối cùng | 25/10/2026 | 25/10/2026 | <https://000064.awsstudygroup.com/> <br> <https://000088.awsstudygroup.com/> |

### Thành tựu Tuần 6:

* **Cơ sở hạ tầng dưới dạng mã (IaC) nâng cao:**
  * Định nghĩa và triển khai thành công cơ sở hạ tầng phức tạp bằng AWS CDK (Python), bao gồm các cụm ECS, ALB, API Gateway và các hàm Lambda.
  * Nắm vững CloudFormation bằng cách triển khai Kiến trúc Web 3 tầng hoàn chỉnh theo phong cách production và sử dụng Nested Stacks để cải thiện khả năng bảo trì mã nguồn.

* **Quản lý Instance an toàn:**
  * Loại bỏ nhu cầu về Bastion hosts và các cổng SSH/RDP mở bằng cách làm chủ AWS Systems Manager Session Manager.
  * Cấu hình thành công VPC Interface Endpoints để giữ toàn bộ lưu lượng SSM hoàn toàn trong mạng AWS.
  * Triển khai Chuyển tiếp cổng (Port Forwarding) nâng cao qua AWS CLI để truy cập an toàn vào các instance riêng tư.

* **Quản trị chi phí & Bảo mật IAM:**
  * Ủy quyền thành công và an toàn quyền truy cập bảng điều khiển Billing and Cost Management cho các người dùng/nhóm IAM cụ thể.
  * Thiết kế, triển khai và kiểm thử các chính sách IAM chi tiết để ngăn chặn các cấu hình sai gây tốn kém bằng cách hạn chế việc tạo tài nguyên dựa trên:
    * Các Vùng (Region) AWS cụ thể
    * Các dòng instance EC2 được phê duyệt (ví dụ: T3)
    * Kích thước instance EC2 tối đa
    * Các loại ổ đĩa EBS được phê duyệt (ngăn chặn việc sử dụng provisioned IOPS đắt đỏ)

* **Xuất sắc trong Vận hành:**
  * Cài đặt và cấu hình CloudWatch Agent để thu thập các số liệu chi tiết ở cấp độ hệ điều hành, phục vụ phân tích tối ưu hóa kích thước chính xác qua AWS Compute Optimizer.
  * Bật và giám sát VPC Flow Logs để thu thập và phân tích siêu dữ liệu lưu lượng IP nhằm khắc phục sự cố mạng và kiểm toán bảo mật.
  * Tự động hóa quản lý chi phí lưu trữ và tuân thủ bằng cách cấu hình Amazon Data Lifecycle Manager (DLM) để tự động tạo, lưu trữ và xóa các EBS Snapshot dựa trên các chính sách lịch trình đơn và đa dạng.