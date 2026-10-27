---
title: "Week 6 Worklog"
date: 2026-10-25
weight: 6
chapter: false
pre: " <b> 6. </b> "
---
### Week 6 Objectives:

* Master advanced Infrastructure as Code (IaC) using AWS CDK and CloudFormation.
* Implement advanced IAM cost governance and resource restriction policies.
* Utilize AWS Systems Manager for secure, agent-based instance management without opening inbound ports.
* Apply operational excellence best practices using Compute Optimizer, VPC Flow Logs, and Data Lifecycle Manager (DLM).

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 1   | - **AWS Systems Manager (Session Manager):** <br>&emsp; + Setup VPC, Subnets, and Security Groups <br>&emsp; + Launch Linux (Public) and Windows (Private) EC2 instances <br>&emsp; + Create & attach SSM IAM Role <br>&emsp; + Configure VPC Interface Endpoints (SSM, SSMMESSAGES, EC2MESSAGES) <br>&emsp; + Enable S3 logging for Session Manager <br>&emsp; + Practice Port Forwarding for RDP via CLI | 21/10/2026 | 21/10/2026      | <https://000058.awsstudygroup.com/>       |
| 2   | - **AWS CDK Basic 2:** <br>&emsp; + Setup CloudShell & VSCode remote environment <br>&emsp; + Deploy ECS, ALB, and API Gateway via CDK <br>&emsp; + Integrate Lambda and S3 via CDK <br>&emsp; + Refactor codebase using Nested Stacks <br>&emsp; + Cleanup resources | 22/10/2026 | 22/10/2026      | <https://000076.awsstudygroup.com/>       |
| 3   | - **CloudFormation & 3-Tier Architecture:** <br>&emsp; + Setup Cloud9 environment <br>&emsp; + Deploy Lambda and VPC/EC2 via CFN templates <br>&emsp; + Deploy 3-Tier Web Architecture (Web, App, DB) <br>&emsp; + Validate tier connectivity and access <br>&emsp; + Cleanup resources | 23/10/2026 | 23/10/2026      | <https://000102.awsstudygroup.com/>       |
| 4   | - **Operational Excellence & IAM Governance:** <br>&emsp; + EC2 Right-Sizing: Install CloudWatch Agent, review Compute Optimizer recommendations <br>&emsp; + Network Monitoring: Create and enable VPC Flow Logs to CloudWatch <br>&emsp; + IAM: Delegate Billing Console access to specific IAM users/groups | 24/10/2026 | 24/10/2026      | <https://000032.awsstudygroup.com/> <br> <https://000074.awsstudygroup.com/> <br> <https://000075.awsstudygroup.com/> |
| 5   | - **Advanced IAM Cost Governance & DLM:** <br>&emsp; + Create and attach policies to limit resources by: Region, EC2 Instance Family, Instance Size, and EBS Volume Type <br>&emsp; + Test policy effectiveness <br>&emsp; + Amazon DLM: Configure single and multiple policy schedules for automated EBS Snapshot archival <br>&emsp; + Final cleanup | 25/10/2026 | 25/10/2026      | <https://000064.awsstudygroup.com/> <br> <https://000088.awsstudygroup.com/> |


### Week 6 Achievements:

* **Advanced Infrastructure as Code (IaC):**
  * Successfully defined and deployed complex infrastructure using AWS CDK (Python), including ECS clusters, ALBs, API Gateways, and Lambda functions.
  * Mastered CloudFormation by deploying a complete, production-style 3-Tier Web Architecture and utilizing Nested Stacks for better code maintainability.

* **Secure Instance Management:**
  * Eliminated the need for Bastion hosts and open SSH/RDP ports by mastering AWS Systems Manager Session Manager.
  * Successfully configured VPC Interface Endpoints to keep all SSM traffic entirely within the AWS network.
  * Implemented advanced Port Forwarding via the AWS CLI to securely access private instances.

* **IAM Cost Governance & Security:**
  * Successfully delegated secure Billing and Cost Management console access to specific IAM users/groups.
  * Designed, implemented, and tested granular IAM policies to prevent costly misconfigurations by restricting resource creation based on:
    * Specific AWS Regions
    * Approved EC2 Instance Families (e.g., T3)
    * Maximum EC2 Instance Sizes
    * Approved EBS Volume Types (preventing expensive provisioned IOPS)

* **Operational Excellence:**
  * Installed and configured the CloudWatch Agent to gather detailed OS-level metrics for accurate right-sizing analysis via AWS Compute Optimizer.
  * Enabled and monitored VPC Flow Logs to capture and analyze IP traffic metadata for network troubleshooting and security auditing.
  * Automated storage cost management and compliance by configuring Amazon Data Lifecycle Manager (DLM) to automatically create, archive, and delete EBS Snapshots based on single and multiple schedule policies.