---
title: "Week 3 Worklog"
date: 2026-10-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Master hybrid cloud migration techniques using AWS VM Import/Export.
* Implement comprehensive observability and monitoring using Amazon CloudWatch.
* Build serverless automation workflows for infrastructure lifecycle management using AWS Lambda and EventBridge.
* Deploy and administer a hybrid Active Directory environment using AWS Managed Microsoft AD.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | - **VM Import/Export:** Prepare on-prem VMware Ubuntu VM, upload `.vmdk` to S3, create `vmimport` IAM role, import to AMI, and deploy as EC2. <br> - **VM Export:** Configure S3 ACLs/policies, export EC2 instance back to VMDK format, and perform full resource cleanup. | 28/09/2026 | 28/09/2026 | [VM Import/Export Lab](https://000014.awsstudygroup.com/) |
| 2 | - **CloudWatch Monitoring:** Deploy CloudWatch workshop stack, analyze Metrics (Search/Math expressions, Dynamic labels), query Logs Insights, create Metric Filters, and configure Alarms with SNS notifications and Dashboards. <br> - **S3 & CloudFront:** Deploy static website, configure CloudFront with OAC, test Edge latency, enable Versioning, and configure Cross-Region Replication (CRR). | 29/09/2026 | 29/09/2026 | [CloudWatch Lab](https://000008.awsstudygroup.com/), [S3/CloudFront Lab](https://000094.awsstudygroup.com/) |
| 3 | - **Serverless Automation:** Create VPC, EC2 instance, and Slack Incoming Webhook. Develop Python Lambda functions (`auto-start`/`auto-stop`) with custom IAM roles. <br> - **EventBridge & Testing:** Schedule Lambda triggers, test EC2 state transitions, verify Slack notifications, and execute complete resource cleanup. | 30/09/2026 | 30/09/2026 | [Lambda Automation Lab](https://000022.awsstudygroup.com/) |
| 4 | - **Managed AD Deployment:** Deploy base network via CloudFormation, provision AWS Managed Microsoft AD (Standard Edition) in private subnets. <br> - **EC2 Setup:** Launch public Bastion Host and private Windows Server 2022 AD-Manager, configuring automatic domain join via IAM instance profile. | 02/10/2026 | 02/10/2026 | [Managed AD Lab](https://000095.awsstudygroup.com/) |
| 5 | - **AD Configuration & Testing:** RDP pivot through Bastion to AD-Manager, verify domain join, configure `hosts` file, install AD Administrative Tools, and perform bidirectional ping tests (IP/Hostname). <br> - **Cleanup:** Terminate EC2 instances, delete Managed AD, and remove CloudFormation stack. | 04/10/2026 | 04/10/2026 | [Managed AD Lab](https://000095.awsstudygroup.com/) |

### Week 3 Achievements:

* **Hybrid Cloud Migration:** Successfully mastered the AWS VM Import/Export service, including the creation of custom IAM trust policies, S3 bucket configurations, and CLI-driven migration of on-premises VMware workloads to AWS AMIs (and vice versa).
* **Advanced Observability:** Gained deep proficiency in Amazon CloudWatch by creating custom Metric Filters from raw logs, utilizing Logs Insights for advanced querying, and building unified Dashboards with SNS-backed Alarms for proactive incident response.
* **Serverless Infrastructure Automation:** Designed and deployed a fully automated EC2 lifecycle management solution using AWS Lambda (Python) and EventBridge Scheduler, integrated seamlessly with Slack Incoming Webhooks for real-time operational alerts.
* **Enterprise Directory Services:** Successfully deployed AWS Managed Microsoft Active Directory across multiple Availability Zones. Configured secure network pivoting (RDP via Bastion Host), automated domain joining, and validated hybrid DNS resolution and AD management tools.
* **Cost Optimization & Security:** Consistently applied the principle of least privilege (custom IAM roles, restricted Security Groups) and executed rigorous, systematic resource cleanup procedures (CloudFormation stack deletion, AMI deregistration, S3 bucket emptying) to prevent unintended billing.
* **High Availability & Disaster Recovery:** Configured S3 Cross-Region Replication (CRR) and Bucket Versioning, ensuring data durability and rapid rollback capabilities for static web assets.