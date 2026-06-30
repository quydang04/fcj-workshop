---
title : "Prerequiste"
date : 2024-01-01 
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

Before starting the implementation steps of the workshop, we must complete the following prerequisite configurations:

### AWS Account & Permissions

An active AWS account with IAM administrative privileges. To obtain connection credentials on the local developer workstation, follow these steps:

- **Step 1 (On the AWS Console):** Log in to the AWS Management Console, navigate to the **IAM** (Identity and Access Management) -> **Users** service, select the IAM username, switch to the **Security credentials** tab, and locate the **Access keys** section. Click **Create access key**, choose the **Command Line Interface (CLI)** use-case, agree to the terms, and click confirm to generate a new pair of credentials containing the **Access Key ID** and **Secret Access Key**. Download the generated `.csv` file to save these secrets.
- **Step 2 (On the Local Workstation):** Open Terminal/Powershell on the workstation and run the `aws configure` command. Enter the Access Key ID and Secret Access Key generated in Step 1, set the **Default region name** to `ap-southeast-1`, and set the **Default output format** to `json`. These settings are written automatically to local configuration files in the user's home directory (`%USERPROFILE%\.aws\` on Windows, or `~/.aws/` on Linux/macOS).

![IAM Security credentials tab showing the Access keys section used to generate CLI credentials](/images/5-Workshop/5.2-Prerequiste/iam-access-key-creation.png?width=50pc&classes=shadow)

### Local Terminal Environment

Ensure the development workstation has **Node.js (version 20 or higher)**, **Java Development Kit (JDK 21)**, **Maven** build tool, and **Docker Desktop** installed to support local packaging and validation before pushing containers to AWS ECR. The local environment requires a stable internet connection to resolve Maven dependencies and download Docker base images.

### Target Cloud Region

The **ap-southeast-1 (Singapore)** region is selected as the default deployment region to minimize connection latency for end-users in the Southeast Asian market and ensure feature compatibility for all AWS services utilized in the architecture.
