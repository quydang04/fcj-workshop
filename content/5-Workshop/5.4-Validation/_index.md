---
title : "Validation & Analysis"
date : 2024-01-01
weight : 4
chapter : false
pre : " <b> 5.4. </b> "
---

We conducted practical testing procedures to validate the integrity and performance of the deployed cloud architecture, covering private DNS routing through the VPC Endpoints, S3 access control, DynamoDB/SQS integration, CloudWatch monitoring, and overall application behavior end-to-end against the live EC2/ALB backend.

### Web Application Walkthrough

The recording below walks through the full **Web** application flow running on the deployed infrastructure: DNS routing to the private S3 endpoint, monthly report export/download via S3, the Nova Money AI assistant with DynamoDB-backed chat history, asynchronous transaction processing through SQS, and the CloudWatch monitoring dashboard.

{{< youtube oCs0s21PJMw >}}

> **Mobile validation:** A YouTube walkthrough video for the Mobile app (React Native Expo) will be added in a future update. Below is a set of screenshots captured while testing directly on the Mobile app.

### Live request testing

Visiting the domain `botdevgroup.me` confirms the DNS record resolves correctly and the Money Manager homepage loads successfully through the deployed ALB/EC2 infrastructure.

> **Web:** [Trải nghiệm tại đây](https://botdevgroup.me)

<div align="center">

![Money Manager homepage loading successfully through the botdevgroup.me domain](/images/5-Workshop/5.4-Validation/dns-routing-site-loaded.png?width=60pc&classes=shadow)

***Figure 25. Money Manager homepage loading successfully through the botdevgroup.me domain***

</div>

Sending a test message to the Nova Money AI assistant confirms the chat flow works correctly and returns a relevant suggestion.

<div align="center">

![Testing a conversation with the Nova Money AI assistant](/images/5-Workshop/5.4-Validation/nova-money-chat-test.png?width=60pc&classes=shadow)

***Figure 26. Testing a conversation with the Nova Money AI assistant***

</div>

After chatting, a direct Scan query on the `chat_messages` table in the DynamoDB console confirms all 6 messages from the test session (`role: user/assistant`) were recorded correctly, proving the DynamoDB-backed chat history flow works as expected.

<div align="center">

![Scan result on the chat_messages DynamoDB table confirming chat history was saved](/images/5-Workshop/5.4-Validation/dynamodb-chat-messages-scan.png?width=60pc&classes=shadow)

***Figure 27. Scan result on the chat_messages DynamoDB table confirming chat history was saved***

</div>

Triggering "Export to Excel" on the Reports page tests the asynchronous processing flow (EC2 API pushes a job to SQS -> Worker processes it -> Lambda generates the file -> stored in S3). The browser successfully receives and downloads the file `report-2026-6-59ffa92d.xlsx`.

<div align="center">

![Excel report file exported and downloaded successfully after processing through SQS + Lambda](/images/5-Workshop/5.4-Validation/s3-export-notification.png?width=60pc&classes=shadow)

***Figure 28. Excel report file exported and downloaded successfully after processing through SQS + Lambda***

</div>

Opening the downloaded Excel file to cross-check the data: the content matches exactly with the "Lương tháng" (Monthly salary) transaction (5,000,000 VND, dated 2026-06-30) entered in the system.

<div align="center">

![Content of the exported Excel file matching the transaction data in the system](/images/5-Workshop/5.4-Validation/s3-exported-report-content.png?width=30pc&classes=shadow)

***Figure 29. Content of the exported Excel file matching the transaction data in the system***

</div>

### Checking logs & metrics via CloudWatch

In the CloudWatch console, the `EC2ErrorAlarm` alarm (based on a Metric Filter reading error logs from the `/aws/ec2/moneymanager-app` log group) is actively being monitored.

<div align="center">

![List of CloudWatch Alarms, showing the EC2ErrorAlarm being monitored](/images/5-Workshop/5.4-Validation/cloudwatch-alarms-list.png?width=60pc&classes=shadow)

***Figure 30. List of CloudWatch Alarms, showing the EC2ErrorAlarm being monitored***

</div>

Viewing the detailed `EC2ErrorCount` metric graph for the alarm over the last 3 hours: the alarm threshold is configured as "EC2ErrorCount >= 1 for 1 datapoint within 5 minutes". The alarm shows an **Insufficient data** state because no error lines were logged during the testing window (no datapoints to evaluate), confirming the Metric Filter and Alarm are correctly configured and ready to switch to the ALARM state and notify via SNS as soon as an actual error is logged.

<div align="center">

![Detailed EC2ErrorCount metric graph for the EC2ErrorAlarm alarm](/images/5-Workshop/5.4-Validation/cloudwatch-alarm-detail-graph.png?width=60pc&classes=shadow)

***Figure 31. Detailed EC2ErrorCount metric graph for the EC2ErrorAlarm alarm***

</div>

### Mobile app testing

Using the same dataset and backend tested above, the **Mobile** app (React Native Expo) was tested directly on-device to confirm the core business flows behave consistently with the Web version.

> **Mobile:** [Trải nghiệm tại đây](https://mobile.botdevgroup.me)<br>
> **Link dự phòng:** [Trải nghiệm tại đây](https://notvnt.github.io/BotDEV/)

{{< youtube riegCGswCls >}}

<div align="center">

![Mobile Overview screen showing balance, income/expense and the monthly financial chart for June 2026](/images/5-Workshop/5.4-Validation/Mobile/mobile-dashboard-overview.jpg?width=22pc&classes=shadow)

***Figure 32. Mobile Overview screen showing balance, income/expense and the monthly financial chart***

</div>

<div align="center">

![Mobile Add Category screen for classifying income/expense transactions](/images/5-Workshop/5.4-Validation/Mobile/mobile-add-category.jpg?width=22pc&classes=shadow)

***Figure 33. Mobile Add Category screen for classifying income/expense transactions***

</div>

<div align="center">

![Mobile Expense History screen with an overview chart and the add-transaction button](/images/5-Workshop/5.4-Validation/Mobile/mobile-expense-history.jpg?width=22pc&classes=shadow)

***Figure 34. Mobile Expense History screen with an overview chart and the add-transaction button***

</div>

<div align="center">

![Mobile Income History screen with the corresponding overview chart](/images/5-Workshop/5.4-Validation/Mobile/mobile-income-history.jpg?width=22pc&classes=shadow)

***Figure 35. Mobile Income History screen with the corresponding overview chart***

</div>

<div align="center">

![Mobile monthly transaction calendar screen, marking days with recorded expenses](/images/5-Workshop/5.4-Validation/Mobile/mobile-history-calendar.jpg?width=22pc&classes=shadow)

***Figure 36. Mobile monthly transaction calendar screen, marking days with recorded expenses***

</div>

<div align="center">

![Mobile Budget screen for setting spending limits by category and by month](/images/5-Workshop/5.4-Validation/Mobile/mobile-budget-limits.jpg?width=22pc&classes=shadow)

***Figure 37. Mobile Budget screen for setting spending limits by category and by month***

</div>

<div align="center">

![Mobile Forecast screen showing next month's projected spending versus the historical average](/images/5-Workshop/5.4-Validation/Mobile/mobile-forecast.jpg?width=22pc&classes=shadow)

***Figure 38. Mobile Forecast screen showing next month's projected spending versus the historical average***

</div>

<div align="center">

![Chat screen with the Nova Money AI assistant on Mobile](/images/5-Workshop/5.4-Validation/Mobile/mobile-nova-money-chat.jpg?width=22pc&classes=shadow)

***Figure 39. Chat screen with the Nova Money AI assistant on Mobile***

</div>

<div align="center">

![Mobile Account screen showing user information and financial management options](/images/5-Workshop/5.4-Validation/Mobile/mobile-settings-account.jpg?width=22pc&classes=shadow)

***Figure 40. Mobile Account screen showing user information and financial management options***

</div>

<div align="center">

![Mobile Settings screen with notification options and sign-out](/images/5-Workshop/5.4-Validation/Mobile/mobile-settings-notifications.jpg?width=22pc&classes=shadow)

***Figure 41. Mobile Settings screen with notification options and sign-out***

</div>

Testing the Excel report export feature on Mobile: on the Income History screen, selecting the "All" time range and exporting the file `income_report_all_months.xlsx` correctly triggers the native share/open sheet.

<div align="center">

![Mobile income report export screen with the income_report_all_months.xlsx file](/images/5-Workshop/5.4-Validation/Mobile/mobile-export-income-report.png?width=22pc&classes=shadow)

***Figure 42. Mobile income report export screen with the income_report_all_months.xlsx file***

</div>

Similarly, on the Expense History screen, selecting the "This month" time range and exporting the file `expense_report_7_2026.xlsx` confirms the expense report export flow works correctly on Mobile.

<div align="center">

![Mobile expense report export screen with the expense_report_7_2026.xlsx file](/images/5-Workshop/5.4-Validation/Mobile/mobile-export-expense-report.png?width=22pc&classes=shadow)

***Figure 43. Mobile expense report export screen with the expense_report_7_2026.xlsx file***

</div>

Result: the Overview, Categories, Income/Expense History, Calendar, Budget, Forecast, Nova Money AI assistant, and Account screens on Mobile all render correctly and stay in sync with the shared backend deployed on AWS.

### Expected results

All of the tests above (DNS routing through the VPC Endpoint, AI chat with DynamoDB-backed history, asynchronous report export through SQS/Lambda/S3, log/metric monitoring through CloudWatch, and the core Mobile screens) produced results matching the design, confirming the infrastructure deployed in section 5.3 runs stably end-to-end across both the Web and Mobile platforms.
