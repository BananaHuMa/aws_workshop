---
title: "Week 5 Worklog"
date: 2026-10-18
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---
### Week 5 Objectives:

* Master in-memory caching and data management using Amazon ElastiCache for Redis.
* Implement effective resource organization and automation using AWS Tagging and Resource Groups.
* Manage EC2 instances securely and at scale without opening inbound ports using AWS Systems Manager (Session Manager, Patch Manager, Run Command).
* Understand and simulate disaster recovery replication and failover processes using AWS Elastic Disaster Recovery (DRS).

### Tasks to be carried out this week:
| Day | Task                                                                                                                                                                                                   | Start Date | Completion Date | Reference Material                        |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | --------------- | ----------------------------------------- |
| 1   | - **Amazon ElastiCache for Redis:** <br>&emsp; + Create subnet groups and deploy Redis clusters (Cluster Mode Disabled & Enabled) <br>&emsp; + Discover endpoints via Console and AWS CLI <br>&emsp; + Integrate with Python (Boto3) SDK <br>&emsp; + Practice Redis operations: Strings, Hashes, Pub/Sub, and Streams | 10/12/2026 | 10/12/2026      | <https://000061.awsstudygroup.com/> |
| 2   | - **Resource Management:** <br>&emsp; + Apply and manage Tags on EC2 instances via Console and AWS CLI <br>&emsp; + Filter resources by tags <br>&emsp; + Create and manage Tag-based AWS Resource Groups | 10/12/2026 | 10/12/2026      | <https://000027.awsstudygroup.com/> |
| 3   | - **AWS Systems Manager:** <br>&emsp; + Configure VPC, subnets, and Security Groups for SSM <br>&emsp; + Attach `AmazonSSMManagedInstanceCore` IAM roles to Windows EC2 instances <br>&emsp; + Execute Patch Manager scans and installations <br>&emsp; + Run PowerShell scripts via Run Command | 10/15/2026 | 10/15/2026      | <https://000031.awsstudygroup.com/> |
| 4   | - **AWS Elastic Disaster Recovery (DRS):** <br>&emsp; + Deploy base infrastructure via CloudFormation <br>&emsp; + Configure default replication settings and IAM agent roles <br>&emsp; + Install replication agents on source servers <br>&emsp; + Configure Launch Templates and execute a Failover Drill | 10/16/2026 | 10/16/2026      | <https://000100.awsstudygroup.com/> |


### Week 5 Achievements:

* **ElastiCache & Redis Mastery:** 
  * Successfully deployed and managed Redis clusters in both Cluster Mode Disabled and Enabled configurations.
  * Discovered and utilized Primary, Reader, and Configuration endpoints via both the AWS Console and CLI.
  * Developed Python (Boto3) scripts to programmatically create clusters, manage Role-Based Access Control (RBAC), and perform advanced Redis operations including String/Hash manipulation, Pub/Sub messaging, and multi-threaded Stream processing.

* **Resource Organization:** 
  * Applied consistent tagging strategies (Key-Value pairs) to EC2 instances for cost allocation and environment tracking.
  * Created and utilized AWS Resource Groups to filter and manage collections of resources based on tag criteria, streamlining administrative tasks.

* **Secure, Agent-Based Management (Systems Manager):** 
  * Eliminated the need for traditional SSH/RDP access by configuring AWS Systems Manager Session Manager.
  * Successfully attached SSM IAM roles to Windows instances and verified connectivity via Fleet Manager.
  * Automated OS patching using Patch Manager and executed remote PowerShell commands across multiple instances using Run Command, with outputs logged to S3.

* **Disaster Recovery Simulation (DRS):** 
  * Provisioned a simulated on-premises environment and configured AWS DRS default replication settings.
  * Installed and configured the DRS replication agent on source Linux servers, monitoring the initial sync and staging disk creation until reaching a "Healthy" status.
  * Defined EC2 Launch Templates for recovered instances and successfully executed a non-disruptive Failover Drill, verifying the isolated provisioning of recovered web and database instances.

* **Operational Excellence:** Consistently followed the principle of least privilege and executed comprehensive resource cleanup (terminating instances, deleting clusters, and removing CloudFormation stacks) to prevent unexpected billing.