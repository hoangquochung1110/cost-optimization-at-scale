---
title : "Thiết lập truy cập tin cậy giữa AWS Organizations và AWS Config"
date : "2025-05-14" 
weight : 1 
chapter : false
pre : " <b> 3.1. </b> "
---

#### Ý nghĩa
Thiết lập này cho phép dịch vụ AWS Config thực hiện các hoạt động xuyên tài khoản mà không cần yêu cầu nhà quản trị cấu hình chính sách quyền một cách thủ công ở từng tài khoản riêng lẻ

Các bước thiết lập sau sẽ bao gồm:

- kích hoạt tích hợp dịch vụ Config cốt lõi

- kích hoạt các tính năng triển khai và tổng hợp đa tài khoản

#### Các bước thực hiện

1. Dùng tài khoản quản lí, truy cập giao diện quản trị dịch vụ

2. Mở AWS CloudShell
![Activate trusted access banner](/images/3.establish/001-cloudshell.png)

3. Thực thi hai lệnh sau

    ```
    aws organizations enable-aws-service-access --service-principal=config-multiaccountsetup.amazonaws.com
    ```

    ```
    aws organizations enable-aws-service-access --service-principal=config.amazonaws.com
    ```
