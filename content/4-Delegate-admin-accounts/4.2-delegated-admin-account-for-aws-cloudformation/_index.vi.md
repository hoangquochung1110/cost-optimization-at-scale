---
title : "Kích hoạt tài khoản 'Quản trị viên được ủy quyền' cho AWS CloudFormation"
date : "2025-05-14" 
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

#### Các bước thực hiện
1. Đăng nhập truy cập giao diện quản trị dịch vụ (Console) bằng tài khoản kiểm toán (Audit account). Bạn có thể kiểm tra lại cấu trúc các tài khoản của tổ chức ở bước [Thiết lập Landing Zone](../../2-Prerequiste/2.1-setupmultiaccount/2.1.2-createlandingzone/)

2. Chạy lệnh sau:

    ```
    aws organizations register-delegated-administrator  --service-principal=member.org.stacksets.cloudformation.amazonaws.com  --account-id=$ACCOUNT_ID
    ```

3. Để kiểm tra tài khoản kiểm toán đã được thiết lập thành công như một quản trị viên được ủy quyền cho AWS Config, chạy lệnh sau:

    ```
    aws organizations list-delegated-administrators  --service-principal=member.org.stacksets.cloudformation.amazonaws.com
    ```