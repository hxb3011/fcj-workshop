---
title: "Lambda Shipper Test"
date: 2026-05-02
weight: 11
chapter: false
pre: "<b> 4.4.2 </b>"
---

## 4.4.2 Lambda Shipper Test

### Objective

Validate the log ingestion flow from CloudWatch to the processing system via Lambda Shipper.


### Implementation Steps

After completing the configuration, logs are generated to simulate input data from the system.

1. Create logs in CloudWatch  

![Create log](/images/4-Workshop/4.4--log-ingestion/4.4.2--shipper-test/create-log.png)  


2. Lambda Shipper receives and processes the logs  

![Shipper run](/images/4-Workshop/4.4--log-ingestion/4.4.2--shipper-test/shipper.png) 


3. Messages are pushed to SQS for further processing  

![SQS message](/images/4-Workshop/4.4--log-ingestion/4.4.2--shipper-test/sqs2.png)  


4. Verify processing results  

- Log data is stored in S3  
- Data is recorded in DynamoDB  
- Email notifications are successfully sent  

![DynamoDB result](/images/4-Workshop/4.4--log-ingestion/4.4.2--shipper-test/dynamodb2.png)  


### Workflow Description

- Logs are generated in the system and sent to Amazon CloudWatch  
- Lambda Shipper is triggered to process logs and push data into Amazon SQS  
- Lambda Processor consumes messages from SQS for further processing  
- Results are stored in Amazon S3 and Amazon DynamoDB  

- Notifications are sent via Amazon SNS (Email Subscription):
  - The email must be subscribed and confirmed  
  - If not confirmed, SNS will send a subscription confirmation request  
  - Only confirmed emails will receive subsequent notifications  

### Conclusion

The ingestion pipeline operates reliably, ensuring that logs are correctly transferred from CloudWatch to the processing system.
