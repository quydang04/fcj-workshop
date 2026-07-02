---
title : "Cleanup"
date : 2024-01-01
weight : 5
chapter : false
pre : " <b> 5.5. </b> "
---

After completing the technical workshop session, clean up the testing infrastructure resources to avoid recurring charges on the AWS account:

- Delete all temporary testing objects uploaded to S3 bucket `botdevgroup-documents` to eliminate monthly storage fees.
- Delete the **Interface VPC Endpoint** `vpce-s3-interface` to release the ENIs and halt the hourly instance charges associated with AWS PrivateLink.
- Detach the **S3 Gateway VPC Endpoint** from the Private Subnet Route Tables to revert the routing configuration of the VPC.
- Remove testing Inbound/Outbound DNS Resolver Rules and associated Security Group rules from the configurations.
- Execute the Docker system prune command (`docker system prune -af`) on the EC2 instance to reclaim unused EBS disk storage space.
- Delete the CloudWatch Log Groups `/aws/ec2/moneymanager-app` and `/aws/rds/moneymanager-db`, along with the `EC2ErrorAlarm` alarm, to avoid recurring log storage and alarm evaluation charges.
