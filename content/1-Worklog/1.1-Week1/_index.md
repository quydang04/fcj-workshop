---
title: "Week 1 Worklog"
date: 2026-04-20
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Week 1 Objectives:
- Get acquainted with the First Cloud Journey internship program and team members.
- Set up the AWS environment and understand foundational AWS services (IAM & VPC).

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
|-----|------|------------|-----------------|-------------------|
| 2 | - Read the full 3-month learning roadmap | 20/04/2026 | 20/04/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Install AWS CLI & configure environment |  |  |  |
|  | - Create AWS account (if not yet available) |  |  |  |
|  | - Enable MFA for root account |  |  |  |
|  | - Practice: Lab 000001 – Creating Your First AWS Account |  |  |  |
| 3 | - Learn IAM: User, Group, Policy | 21/04/2026 | 21/04/2026 | [https://000002.awsstudygroup.com](https://000002.awsstudygroup.com) |
|  | - Create Admin Group & Admin User |  |  |  |
|  | - Understand the Least Privilege principle |  |  |  |
|  | - Practice: Lab 000002 – Access Management with AWS IAM (Section 1.1–2.3) |  |  |  |
| 4 | - Learn IAM Role vs User | 22/04/2026 | 22/04/2026 | [https://000002.awsstudygroup.com](https://000002.awsstudygroup.com) |
|  | - Create Admin Role, OperatorUser |  |  |  |
|  | - Practice Switch Role on the console |  |  |  |
|  | - Practice: Lab 000002 (Section 3.1–5: Role, Switch Role, Clean up) |  |  |  |
| 5 | - Learn Amazon VPC: Public/Private Subnets, Route Table, IGW, NAT GW | 23/04/2026 | 23/04/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Learn Security Group vs Network ACL |  |  |  |
|  | - Practice: Lab 000003 – Amazon VPC (Section 1.1–3.6: Create VPC from scratch) |  |  |  |
| 6 | - Deploy EC2 into VPC, test connection | 24/04/2026 | 24/04/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Configure NAT Gateway, Reachability Analyzer |  |  |  |
|  | - Use Session Manager (SSH-less access) |  |  |  |
|  | - Set up CloudWatch Monitoring on EC2 |  |  |  |
|  | - Practice: Lab 000003 (Section 4.1–4.7) |  |  |  |
|  | - Clean up resources |  |  |  |

### Week 1 Achievements:
- Successfully created and secured an AWS account with MFA enabled on the root account.
- Understood the AWS Free Tier strategy and cost governance practices to avoid unexpected charges.
- Mastered IAM core concepts including:
  + Users, Groups, and Policy attachments
  + The Least Privilege principle
  + IAM Roles and the Switch Role workflow
  + Admin Group / Admin User / OperatorUser setup
- Built a complete Amazon VPC from scratch including:
  + Public and private subnets across availability zones
  + Internet Gateway and NAT Gateway
  + Route Tables configuration
  + Security Groups and Network ACLs
- Successfully deployed EC2 instances into the VPC and tested connectivity using Session Manager (no SSH key required).
- Configured CloudWatch basic monitoring on EC2 instances.
- Practiced resource cleanup to maintain cost control.
