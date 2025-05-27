---
title : "Thiết lập mối quan hệ tin cậy trong AWS Organizations"
date : "2025-05-14" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

Trong bước này, chúng ta sẽ thực hiện tạo mối quan hệ tin cậy giữa AWS Organizations và các service principals cho AWS CloudFormation và AWS Config

Việc thiết lập này giúp:

- Chức năng đa tài khoản - Quyền truy cập tin cậy cho phép các dịch vụ AWS hoạt động
trên nhiều tài khoản trong tổ chức của bạn mà không cần phải cấu hình
quyền thủ công trong từng tài khoản

- Quản lý tập trung - Các dịch vụ như AWS Config, CloudTrail và Security
Hub có thể được triển khai và quản lý trên toàn tổ chức từ tài khoản quản lý

- Service-linked roles - Quyền truy cập tin cậy tự động tạo các vai trò liên kết dịch vụ cần thiết trong các tài khoản thành viên


### Nội dung
3.1. [Kích hoạt quyền truy cập tin cậy cho AWS Config](3.1-AWS-Config/) \
3.2. [kích hoạt quyền truy cập tin cậy cho AWS CloudFormation](3.2-AWS-CloudFormation/) 
