---
title: "Lambda Processor"
date: 2026-05-02
weight: 8
chapter: false
pre: "<b> 4.3 </b>"
---
## Nội dung

[4.3.1 Kiểm tra tài nguyên](./4.3.1--resource-check/_index.vi.md)  
[4.3.2 Processor Test](./4.3.2--processor-test/_index.vi.md)  

## Tổng quan

Trong hệ thống giám sát log, việc xử lý dữ liệu theo thời gian thực đóng vai trò quan trọng nhằm phát hiện sớm các sự cố. Do đó, phần này tập trung xây dựng một pipeline xử lý log sử dụng SQS và Lambda.


## Kiến trúc tổng quát
![Struct](/images/4-Workshop/4.3--lambda-processor/4.3_struct.png)  

## Mô tả kiến trúc

Trong kiến trúc này, SQS đóng vai trò là hàng đợi trung gian tiếp nhận các message log. Lambda Processor sẽ quan sát, kéo tin nhắn từ SQS để xử lý rồi tin nhắn sẽ được xoá khỏi SQS. Sau đó, dữ liệu được lưu trữ vào DynamoDB, S3 và đồng thời gửi thông báo thông qua SNS.

## Vai trò của Lambda Processor

- Nhận message từ SQS  
- Xử lý dữ liệu log  
- Lưu trữ dữ liệu và gửi thông báo  

## Kết quả

Hệ thống xử lý log hoạt động xuyên suốt (end-to-end), đảm bảo dữ liệu được tiếp nhận, xử lý và lưu trữ đầy đủ.
