---
title : "Tài khoản thành viên"
date : "2025-05-14" 
weight : 2
chapter : false
pre : " <b> 5.2.2 </b> "
---

Sử dụng một tài khoản thành viên để đăng nhập

![Member account](/images/5.conformancepack/019-memberaccount.png)

{{% notice info %}}
Ở đây, nhằm mục đích đơn giản hoá, chúng ta sẽ sử dụng tài khoản Log Archive
{{% /notice %}}

1. Kiểm tra AWS Lambda function
    Chúng ta có một function duy nhất đánh giá quy tắc AWS Config
    ![Lambda function](/images/5.conformancepack/020-lambda.png)

2. Kiểm tra AWS Systems Manager Document:
    Được chia sẻ một document nhằm thực hiện biện pháp khắc phụ nếu AWS Config phát hiện một sự kiện bất tuân thủ
    ![SSM Document](/images/5.conformancepack/021-ssm-document.png)

3. Kiểm tra AWS Config Conformance Pack
    ![Conformance Pack](/images/5.conformancepack/022-conformance-pack.png)

4. Chọn **View** để xem chi tiết
    ![Conformance Pack](/images/5.conformancepack/023-conformance-pack.png)
