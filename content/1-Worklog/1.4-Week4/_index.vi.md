---
title: "Nhật ký công việc Tuần 4"
date: 2026-10-09
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
### Mục tiêu Tuần 4:

* Nắm vững các dịch vụ điện toán và cơ sở dữ liệu nâng cao của AWS (Auto Scaling, ELB, DynamoDB).
* Triển khai các kiến trúc mạng lai (hybrid) (Route 53 Resolver, AWS Managed Microsoft AD).
* Thành thạo việc quản lý tài nguyên AWS thông qua AWS Management Console, AWS CLI và Python (Boto3) SDK.

### Các nhiệm vụ sẽ thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | - **Auto Scaling & ELB**: Đã triển khai hạ tầng ứng dụng FCAJ (VPC, EC2, RDS), tạo AMI/Launch Template, cấu hình ALB và kiểm thử các chính sách mở rộng (scaling) Thủ công (Manual), Theo lịch (Scheduled), Động (Dynamic) và Dự đoán (Predictive). | 10/05/2026 | 10/05/2026 | <https://000006.awsstudygroup.com/> |
| 2 | - **DNS Lai (Hybrid DNS)**: Đã triển khai AWS Managed Microsoft AD, cấu hình các Endpoint Vào/Ra (Inbound/Outbound) của Route 53, tạo các Quy tắc Resolver (Resolver Rules) và xác minh khả năng phân giải DNS hai chiều thông qua RDGW. | 10/06/2026 | 10/06/2026 | <https://000010.awsstudygroup.com/> |
| 3 | - **Amazon DynamoDB (Console & CLI)**: Nghiên cứu các khái niệm cốt lõi (khóa, chỉ mục, tính nhất quán). Thực hành tạo bảng, các thao tác CRUD, truy vấn và quản lý GSI thông qua AWS Console và CloudShell. | 10/09/2026 | 10/09/2026 | <https://000060.awsstudygroup.com/> |
| 4 | - **Amazon DynamoDB (Python SDK)**: Cấu hình Boto3, tự động hóa việc tạo bảng, nhập dữ liệu (tải hàng loạt - bulk load), truy vấn nâng cao, quét (scan) và dọn dẹp tài nguyên bằng các tập lệnh Python. | 10/09/2026 | 10/09/2026 | <https://000060.awsstudygroup.com/> |

### Thành tựu Tuần 4:

* Thiết kế và kiểm thử thành công kiến trúc có khả năng mở rộng và sẵn sàng cao (highly available) bằng Application Load Balancer (ALB) và EC2 Auto Scaling Groups, xác thực các hành vi mở rộng Thủ công, Theo lịch, Động (Theo dõi mục tiêu - Target Tracking) và Dự đoán.
* Xây dựng môi trường DNS lai (hybrid) hoạt động hiệu quả, kết nối Active Directory mô phỏng tại chỗ (on-premises) với AWS Route 53 Resolver bằng các endpoint Vào/Ra và các quy tắc chuyển tiếp có điều kiện (conditional forwarding rules).
* Nắm vững các khái niệm cơ sở dữ liệu NoSQL trong Amazon DynamoDB, bao gồm khóa phân vùng/khóa sắp xếp (partition/sort keys), các mô hình nhất quán khi đọc (Nhất quán cuối cùng - Eventually Consistent so với Nhất quán mạnh - Strongly Consistent) và các chế độ dung lượng (Cấp phát sẵn - Provisioned so với Theo nhu cầu - On-Demand).
* Thực hiện thành công các thao tác dữ liệu từ đầu đến cuối (CRUD, Query, Scan, Global Secondary Indexes) bằng ba phương pháp khác nhau: AWS Management Console, AWS CLI (CloudShell) và Python (Boto3 SDK).
* Củng cố kỹ năng tự động hóa hạ tầng bằng cách viết script để khởi tạo dữ liệu (seeding), tải dữ liệu JSON hàng loạt và dọn dẹp tài nguyên toàn diện để đảm bảo quản lý chi phí hiệu quả trong môi trường lab.