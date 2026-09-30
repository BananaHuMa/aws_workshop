---
title: "Week 1 Worklog"
date: 2026-09-20
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:

* Understand and implement core AWS Identity and Access Management (IAM) best practices.
* Design and deploy secure, highly available VPC network architectures.
* Master EC2 instance lifecycle management, including AMI creation, resizing, and key pair recovery.
* Utilize Amazon S3 for static website hosting, versioning, and cross-region replication, integrated with Amazon CloudFront for secure, low-latency content delivery.
* Gain proficiency in AWS CLI and CloudShell for infrastructure management.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | - **IAM & Cost Management:** Create IAM Groups, Users, Roles, and practice Role Switching.<br>- **AWS 5 Tasks:** Launch/terminate EC2, configure Bedrock, set up AWS Budgets, deploy serverless Lambda app, provision RDS.<br>- **Networking:** Create initial VPC (`ASG`) with CIDR `10.10.0.0/16`. | 14/09/2026 | 14/09/2026 | [IAM & Budgets](https://000002.awsstudygroup.com/), [VPC](https://000003.awsstudygroup.com/3-prerequisite/3.1-createvpc/) |
| 2 | - **Advanced Networking:** Create Public/Private Subnets, Internet Gateway, Route Tables, and dedicated Security Groups.<br>- **Monitoring & Connectivity:** Enable VPC Flow Logs, deploy EC2 Public/Private instances, configure High-Availability NAT Gateways, test with Reachability Analyzer, and set up Site-to-Site VPN. | 15/09/2026 | 15/09/2026 | [VPC Networking](https://000003.awsstudygroup.com/3-prerequisite/), [EC2 & VPN](https://000003.awsstudygroup.com/4-createec2server/), [VPN](https://000003.awsstudygroup.com/5-vpnsitetosite/5.2-vpnsitetosite/) |
| 3 | - **EC2 Management:** Launch Windows Server 2025 & Amazon Linux 2023. Perform Sysprep, create Custom AMIs, and resize instances.<br>- **Recovery & Deployment:** Recover lost key pairs via SSM (Windows) and User Data (Linux). Set up Ubuntu Desktop with RDP. Deploy full-stack Node.js/MySQL apps on both OS environments. | 17/09/2026 | 17/09/2026 | [EC2 Basics](https://000004.awsstudygroup.com/3-launchwindowsinstance/), [App Deployment](https://000004.awsstudygroup.com/6-awsfcjmanagement-linux/) |
| 4 | - **S3 & IAM Best Practices:** Create S3 buckets. Compare hardcoded IAM Access Keys vs. secure IAM Roles (Instance Profiles) for EC2-to-S3 access.<br>- **CLI Proficiency:** Practice basic Linux commands, file transfers, and resource management using AWS CLI and CloudShell. | 18/09/2026 | 18/09/2026 | [IAM Roles](https://000048.awsstudygroup.com/3-iamroleec2/), [CloudShell & CLI](https://000049.awsstudygroup.com/2-basicfeature/) |
| 5 | - **S3 Advanced Features:** Configure S3 Static Website Hosting, manage Block Public Access, and set object ACLs.<br>- **CloudFront & DR:** Integrate CloudFront with Origin Access Control (OAC). Enable S3 Versioning, migrate objects between buckets, and configure Cross-Region Replication (CRR) for disaster recovery. | 20/09/2026 | 20/09/2026 | [Static Website](https://000057.awsstudygroup.com/3-staticwebsite/), [CloudFront](https://000057.awsstudygroup.com/7-cloudfront/), [CRR](https://000057.awsstudygroup.com/10-s3ccr/) |

### Week 1 Achievements:

* **IAM & Security:** Successfully implemented the principle of least privilege by managing permissions via IAM Groups and Roles, eliminating the need for long-term access keys in application code.
* **Network Architecture:** Designed and deployed a highly available, multi-AZ VPC architecture with public/private subnets, NAT Gateways, and secure Site-to-Site VPN connectivity.
* **Compute Mastery:** Gained hands-on experience with the full EC2 lifecycle, including custom AMI creation, instance resizing, and advanced recovery techniques (SSM Run Command and EC2 User Data injection).
* **Storage & Content Delivery:** Successfully hosted a static website on S3, secured it using CloudFront Origin Access Control (OAC), and implemented enterprise-grade data protection using S3 Versioning and Cross-Region Replication (CRR).
* **Automation & CLI:** Became proficient in managing AWS resources programmatically using AWS CLI and CloudShell, improving operational efficiency and reproducibility.
* **Application Deployment:** Successfully deployed and tested a full-stack web application on both Amazon Linux 2023 and Windows Server 2025 environments.