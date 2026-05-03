---
title: "Chạy Lambda Shipper"
date: 2026-05-02
weight: 11
chapter: false
pre: "<b> 4.4.2 </b>"
---

## 4.4.2 Chạy Lambda Shipper

### Mục tiêu

Kiểm tra luồng ingest log từ CloudWatch đến hệ thống xử lý thông qua Lambda Shipper.

### Các bước thực hiện

Sau khi cấu hình hoàn tất, tiến hành tạo log để mô phỏng dữ liệu đầu vào từ hệ thống.

1. Tạo log trong CloudWatch  

![Create log](/images/4-Workshop/4.4--log-ingestion/4.4.2--shipper-test/create-log.png)  


2. Lambda Shipper tiếp nhận và xử lý log  

![Shipper run](/images/4-Workshop/4.4--log-ingestion/4.4.2--shipper-test/shipper.png)  


3. Message được đẩy vào SQS để tiếp tục xử lý  

![SQS message](/images/4-Workshop/4.4--log-ingestion/4.4.2--shipper-test/sqs2.png)  


4. Kiểm tra dữ liệu sau khi xử lý  

- Dữ liệu log được lưu vào S3  
- Dữ liệu được ghi nhận trong DynamoDB  
- Email thông báo được gửi thành công  

![DynamoDB result](/images/4-Workshop/4.4--log-ingestion/4.4.2--shipper-test/dynamodb2.png)  


### Mô tả luồng hoạt động

- Log được tạo trong hệ thống và gửi đến CloudWatch  
- Lambda Shipper được kích hoạt để xử lý và đẩy dữ liệu vào SQS  
- Lambda Processor lấy dữ liệu từ SQS để tiếp tục xử lý  
- Kết quả được lưu vào S3, DynamoDB  

- Thông báo được gửi qua SNS (Email Subscription):
  - Email nhận thông báo phải **subscribe và xác nhận (confirm)** trước  
  - Nếu chưa xác nhận, SNS sẽ gửi email yêu cầu xác nhận subscription  
  - Chỉ sau khi confirm, email mới nhận được các thông báo tiếp theo  

### Kết luận

Kết quả cho thấy luồng ingest log hoạt động ổn định, dữ liệu được chuyển từ CloudWatch đến hệ thống xử lý một cách chính xác.
