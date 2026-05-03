---
title: "Lambda Processor Overview"
date: 2026-05-02
weight: 8
chapter: false
pre: "<b> 4.3 </b>"
---

## Content

[4.3.1 Check resource](./4.3.1--resource-check/_index.md)  
[4.3.2 Processor Test](./4.3.2--processor-test/_index.md)  

### Overview

In a log monitoring system, real-time data processing plays a crucial role in early detection of potential issues. Therefore, this section focuses on building a log processing pipeline using SQS and Lambda.

### Architecture

![Struct](/images/4-Workshop/4.3--lambda-processor/4.3_struct.png)  

### Architecture Description

In this architecture, SQS acts as a message queue that receives log data. The Lambda Processor observes and retrieves messages from the SQS for processing, after which the messages are deleted from the SQS. The processed data is then stored in DynamoDB and S3, while notifications are sent via SNS.

### Role of Lambda Processor

- Receive messages from SQS  
- Process log data  
- Store data and send notifications  

### Result

The log processing system operates in an end-to-end manner, ensuring that data is reliably received, processed, and stored.
