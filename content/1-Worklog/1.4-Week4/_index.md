---
title: "Week 4 Worklog"
date: 2026-10-09
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
### Week 4 Objectives:

* Master advanced AWS compute and database services (Auto Scaling, ELB, DynamoDB).
* Implement hybrid network architectures (Route 53 Resolver, AWS Managed Microsoft AD).
* Gain proficiency in managing AWS resources via the Management Console, AWS CLI, and Python (Boto3) SDK.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 1 | - **Auto Scaling & ELB**: Deployed FCAJ app infrastructure (VPC, EC2, RDS), created AMI/Launch Template, configured ALB, and tested Manual, Scheduled, Dynamic, and Predictive scaling policies. | 10/05/2026 | 10/05/2026 | <https://000006.awsstudygroup.com/> |
| 2 | - **Hybrid DNS**: Deployed AWS Managed Microsoft AD, configured Route 53 Inbound/Outbound Endpoints, created Resolver Rules, and verified bidirectional DNS resolution via RDGW. | 10/06/2026 | 10/06/2026 | <https://000010.awsstudygroup.com/> |
| 3 | - **Amazon DynamoDB (Console & CLI)**: Studied core concepts (keys, indexes, consistency). Practiced table creation, CRUD operations, querying, and GSI management via AWS Console and CloudShell. | 10/09/2026 | 10/09/2026 | <https://000060.awsstudygroup.com/> |
| 4 | - **Amazon DynamoDB (Python SDK)**: Configured Boto3, automated table creation, data ingestion (bulk load), advanced querying, scanning, and resource cleanup using Python scripts. | 10/09/2026 | 10/09/2026 | <https://000060.awsstudygroup.com/> |

### Week 4 Achievements:

* Successfully designed and tested a highly available, scalable architecture using Application Load Balancer (ALB) and EC2 Auto Scaling Groups, validating Manual, Scheduled, Dynamic (Target Tracking), and Predictive scaling behaviors.
* Built a functional hybrid DNS environment connecting a simulated on-premises Active Directory with AWS Route 53 Resolver using Inbound/Outbound endpoints and conditional forwarding rules.
* Mastered NoSQL database concepts in Amazon DynamoDB, including partition/sort keys, read consistency models (Eventually vs. Strongly Consistent), and capacity modes (Provisioned vs. On-Demand).
* Successfully executed end-to-end data operations (CRUD, Query, Scan, Global Secondary Indexes) using three different methods: AWS Management Console, AWS CLI (CloudShell), and Python (Boto3 SDK).
* Reinforced infrastructure automation skills by scripting database seeding, bulk JSON data loading, and comprehensive resource cleanup to ensure cost-effective lab management.