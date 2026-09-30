---
title: "Nhật ký công việc Tuần 2"
date: 2026-09-27
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---


### Mục tiêu Tuần 2:

* Triển khai và quản lý cơ sở dữ liệu quan hệ bằng Amazon RDS với tính sẵn sàng cao (Multi-AZ).
* Tận dụng Amazon Lightsail để triển khai nhanh chóng, hiệu quả về chi phí các ứng dụng được cấu hình sẵn (WordPress, PrestaShop, Akaunting).
* Khám phá việc triển khai ứng dụng dạng container bằng Amazon Lightsail Container Services.
* Tự động hóa việc cấp phát và quản lý hạ tầng bằng các lệnh AWS CLI nâng cao trên nhiều dịch vụ khác nhau.

### Các nhiệm vụ cần thực hiện trong tuần:
| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 1 | - **Cơ sở dữ liệu & Compute**: Tạo VPC, Subnets và Security Groups cho RDS. <br> - Khởi tạo instance Amazon RDS (MySQL) Multi-AZ. <br> - Triển khai instance EC2 Amazon Linux 2023 và kết nối qua SSH (MobaXterm). <br> - **Thực hành**: Triển khai ứng dụng Node.js, kết nối với RDS, khởi tạo dữ liệu mẫu (seed database) và thực hành tạo/khôi phục RDS Snapshot. | 22/09/2026 | 22/09/2026 | <ul><li><a href="https://000005.awsstudygroup.com/2-prerequiste/2.1-create-vpc/">Tạo VPC</a></li><li><a href="https://000005.awsstudygroup.com/2-prerequiste/2.2-create-ec2-sg/">Tạo Security Groups</a></li><li><a href="https://000005.awsstudygroup.com/2-prerequiste/2.3-create-rds-subnet-group/">Tạo RDS Subnet Group</a></li><li><a href="https://000005.awsstudygroup.com/3-create-rds/">Tạo RDS Instance</a></li><li><a href="https://000005.awsstudygroup.com/4-create-ec2/">Tạo EC2 Instance</a></li><li><a href="https://000005.awsstudygroup.com/5-deploy-app/">Triển khai Ứng dụng</a></li><li><a href="https://000005.awsstudygroup.com/6-backup/">Sao lưu và Khôi phục</a></li></ul> |
| 2 | - **Triển khai trên Lightsail**: Cấp phát Lightsail Database có tính sẵn sàng cao (HA). Triển khai các instance WordPress, PrestaShop và Akaunting. <br> - Cấu hình Static IPs, kết nối cơ sở dữ liệu từ xa và các cài đặt ứng dụng Bitnami. <br> - **Bảo mật**: Tăng cường bảo mật cho các instance bằng cách vô hiệu hóa quyền truy cập SSH công khai (Port 22). | 24/09/2026 | 24/09/2026 | <ul><li><a href="https://000045.awsstudygroup.com/1-database/">Triển khai Lightsail Database</a></li><li><a href="https://000045.awsstudygroup.com/2-wp-instance/2.1-deploy-instance/">Triển khai WordPress</a></li><li><a href="https://000045.awsstudygroup.com/3-e-commerce-instance/3.1-deploy/">Triển khai PrestaShop</a></li><li><a href="https://000045.awsstudygroup.com/4-akaunting-instance/4.1-deploy-instance/">Triển khai Akaunting</a></li><li><a href="https://000045.awsstudygroup.com/5-secure-the-applications/">Bảo mật Ứng dụng</a></li></ul> |
| 2 | - **Vận hành & Giám sát**: Tạo Manual và Automated Snapshots. Nâng cấp (scale) WordPress lên gói instance lớn hơn thông qua di chuyển snapshot. Cấu hình cảnh báo CPU Burst Capacity kèm thông báo qua email. | 24/09/2026 | 24/09/2026 | <ul><li><a href="https://000045.awsstudygroup.com/6-create-snapshots/">Tạo Snapshots</a></li><li><a href="https://000045.awsstudygroup.com/7-migrate-to-larger-instances/">Di chuyển sang Instance lớn hơn</a></li><li><a href="https://000045.awsstudygroup.com/8-create-alarms/">Tạo Cảnh báo</a></li></ul> |
| 2 | - **Containerization (Đóng gói)**: Tạo Amazon Lightsail Container Service. <br> - **Thực hành**: Triển khai image Nginx công khai từ Docker Hub, sau đó xây dựng và triển khai một custom container image bằng Docker và AWS CLI. | 24/09/2026 | 24/09/2026 | <ul><li><a href="https://000046.awsstudygroup.com/1-prepare/">Các bước Chuẩn bị</a></li><li><a href="https://000046.awsstudygroup.com/2-create-containerservice/">Tạo Container Service</a></li><li><a href="https://000046.awsstudygroup.com/3-deploy-publicimage/">Triển khai Public Image</a></li><li><a href="https://000046.awsstudygroup.com/4-deploy-yourimage/">Triển khai Custom Image</a></li></ul> |
| 2 | - **Tự động hóa CLI nâng cao**: Cài đặt AWS CLI v2 và cấu hình nhiều profiles. <br> - **Thực hành**: Quản lý IAM (users/groups/keys), S3 (buckets/objects), SNS (topics/subscriptions), VPC Networking và toàn bộ vòng đời của EC2 hoàn toàn thông qua dòng lệnh. | 24/09/2026 | 24/09/2026 | <ul><li><a href="https://000011.awsstudygroup.com/3-installcli/">Cài đặt AWS CLI</a></li><li><a href="https://000011.awsstudygroup.com/5-s3/">CLI với S3</a></li><li><a href="https://000011.awsstudygroup.com/6-sns/">CLI với SNS</a></li><li><a href="https://000011.awsstudygroup.com/7-iam/">CLI với IAM</a></li><li><a href="https://000011.awsstudygroup.com/8-network/">CLI với Networking</a></li><li><a href="https://000011.awsstudygroup.com/9-ec2/">CLI với EC2</a></li></ul> |


### Thành tựu Tuần 2:

* Cấp phát thành công instance Amazon RDS MySQL Multi-AZ có tính sẵn sàng cao và kết nối an toàn với ứng dụng được lưu trữ trên EC2 bằng các quy tắc Security Group chặt chẽ.
* Làm chủ Amazon Lightsail để triển khai ứng dụng nhanh chóng, tích hợp thành công ba ứng dụng riêng biệt (WordPress, PrestaShop, Akaunting) với một Lightsail Database tập trung, có tính sẵn sàng cao.
* Triển khai các phương pháp hay nhất (best practices) trong vận hành Lightsail, bao gồm gán Static IPs, cấu hình snapshot tự động/thủ công, nâng cấp (scale) instance lên gói lớn hơn một cách liền mạch và thiết lập cảnh báo giám sát CPU chủ động.
* Có kinh nghiệm thực tế với containerization thông qua việc triển khai cả image công khai từ Docker Hub và custom container image bằng Amazon Lightsail Container Service.
* Chuyển đổi từ thao tác thủ công trên console sang quản lý hạ tầng tự động hóa bằng cách làm chủ AWS CLI v2, cấp phát và xóa bỏ (teardown) thành công các tài nguyên phức tạp (IAM, S3, SNS, VPC, EC2) thông qua các script dòng lệnh.
* Luôn áp dụng các phương pháp hay nhất về bảo mật và tối ưu hóa chi phí, bao gồm việc vô hiệu hóa quyền truy cập SSH công khai không cần thiết và dọn dẹp có hệ thống tất cả các tài nguyên tạm thời vào cuối mỗi module.