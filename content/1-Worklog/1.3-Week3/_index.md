---
title: "Week 3 Worklog"
date: 2026-04-20
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:
- Complete EC2 advanced operations: resize, snapshots, AMI, and application deployment.
- Learn Amazon RDS, Amazon S3 static hosting, and CloudWatch monitoring.

### Tasks to be carried out this week:

| Day | Task | Start Date | Completion Date | Reference Material |
|-----|------|------------|-----------------|-------------------|
| 2 | - Resize EC2 Instance Type | 04/05/2026 | 04/05/2026 | [https://000004.awsstudygroup.com](https://000004.awsstudygroup.com) |
|  | - Create and manage EBS Snapshots |  |  |  |
|  | - Create Custom AMI and launch from it |  |  |  |
|  | - Recover access to Linux & Windows instances |  |  |  |
|  | - Practice: Lab 000004 (Section 5.1–5.6) |  |  |  |
| 3 | - Install LAMP Server & Node.js on Amazon Linux 2023 | 05/05/2026 | 05/05/2026 | [https://000004.awsstudygroup.com](https://000004.awsstudygroup.com) |
|  | - Deploy Node.js app on EC2 (Linux & Windows) |  |  |  |
|  | - Learn AWS CLI basics: ec2, s3, iam commands |  |  |  |
|  | - Create AWS Budgets alert |  |  |  |
|  | - Practice: Lab 000004 (Deploy) + Lab 000011 + Lab 000007 |  |  |  |
|  | - Terminate EC2 instances at end of day |  |  |  |
| 4 | - Create VPC + Security Group for RDS | 06/05/2026 | 06/05/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Launch RDS MySQL managed instance |  |  |  |
|  | - Deploy application connecting to RDS |  |  |  |
|  | - Backup & Restore RDS snapshot |  |  |  |
|  | - Practice: Lab 000005 – Amazon RDS |  |  |  |
| 5 | - Create S3 bucket and configure Public Access | 07/05/2026 | 07/05/2026 | [https://cloudjourney.awsstudygroup.com/](https://cloudjourney.awsstudygroup.com/) |
|  | - Upload static website (HTML/CSS) |  |  |  |
|  | - Configure Bucket Policy, Versioning |  |  |  |
|  | - Test Pre-signed URLs |  |  |  |
|  | - Practice: Lab 000057 – Static Website Hosting with S3 |  |  |  |
|  | - Clean up resources at end of week |  |  |  |
| 6 | - Learn CloudWatch Metrics, Dashboards | 08/05/2026 | 08/05/2026 | [https://000008.awsstudygroup.com](https://000008.awsstudygroup.com) |
|  | - Set up Alarm: CPU >80% → SNS email notification |  |  |  |
|  | - Configure Log Groups + Log Insights |  |  |  |
|  | - Install CloudWatch Agent on EC2 |  |  |  |
|  | - Practice: Lab 000008 – Monitoring with Amazon CloudWatch |  |  |  |

### Week 3 Achievements:
- Mastered EC2 advanced operations:
  + Resized instance type without data loss
  + Created and restored EBS Snapshots
  + Built and launched instances from Custom AMI
  + Recovered access to locked Linux & Windows instances
- Deployed a full LAMP stack and Node.js application on EC2.
- Used AWS CLI to manage EC2, S3, and IAM resources from the command line.
- Set up AWS Budgets with cost alert notifications.
- Launched and configured a managed Amazon RDS MySQL instance:
  + DB Subnet Group, Multi-AZ awareness
  + Connected application to RDS endpoint
  + Performed backup and snapshot restore
- Hosted a static website on Amazon S3 with:
  + Bucket Policy for public access
  + Versioning enabled
  + Pre-signed URLs for secure access
- Configured Amazon CloudWatch monitoring including CPU alarms, SNS email alerts, Log Groups, and CloudWatch Agent.
