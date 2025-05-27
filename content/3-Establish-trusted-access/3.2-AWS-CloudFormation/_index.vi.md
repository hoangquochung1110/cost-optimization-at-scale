---
title : "Thiết lập truy cập tin cậy giữa AWS Organizations và AWS CloudFormation"
date : "2025-05-14" 
weight : 2 
chapter : false
pre : " <b> 3.2. </b> "
---

#### Ý nghĩa

Cho phép CloudFormation StackSets thực hiện các hoạt động trên các tài khoản thành viên mà không cần thiết lập quyền riêng trong từng tài khoản

#### Các bước thực hiện

1. Dùng tài khoản quản lí, truy cập giao diện quản trị dịch vụ

2. Mở AWS CloudShell
![Activate trusted access banner](/images/3.establish/001-cloudshell.png)

3. Thực thi lệnh sau

    ```
    aws organizations enable-aws-service-access --service-principal=member.org.stacksets.cloudformation.amazonaws.com
    ```

