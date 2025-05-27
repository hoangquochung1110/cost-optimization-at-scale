---
title : "Triển khai Conformance Pack"
date : "2025-05-14" 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

### Tổng quan

Chúng ta sẽ sử dụng tài khoản kiểm toán để triển khai các tài nguyên trong giải pháp tận dụng dịch vụ AWS CloudFormation, bao gồm:

- Một CloudFormation Stackset: giúp triển khai hàng loạt một bộ các tài nguyên lên nhiều tài khoản
- Một CloudFormation Stack: khiển khai một số tài nguyên hỗ trợ, giúp phân bổ các tài nguyên được định nghĩa trong CloudFormation Stackset đến các tài khoản thành viên được chỉ định.

![Architecture Overview](/images/5.conformancepack/007-architecture-overview.png)

### Triển khai

1. Tải CloudFormation template [tại đây](https://github.com/aws-samples/aws-config-cost-optimization-conformance-pack/releases/download/26/template.yaml)

2. Đăng nhập giao diện quản trị dịch vụ [AWS CloudFormation](console.aws.amazon.com/cloudformation/) sử dụng tài khoản kiểm toán 

3. Ở giao diện chính, mở **CloudShell**, chọn ô Action rồi Upload file

    ![Create a stack](/images/5.conformancepack/008-cloudformationstack.png)

4. Kiểm tra CloudFormation template đã được tải lên thành công

    ![Upload a template](/images/5.conformancepack/009-cloudformationstack.png)

5. Tiếp theo nhập lệnh sau để triển khai CloudFormation:

    ```bash
    aws cloudformation deploy --template-file AWS_Config_Cost_Optimization_Template.yaml --stack-name CostOptimizationConfPack --parameter-overrides DeployingInDelegatedAdminAccount=True --capabilities CAPABILITY_IAM
    ```

    ![fill stack name](/images/5.conformancepack/010-cloudformationstack.png)

6. Sau khoảng 5-10 phút, việc triển khai thành công
    ![fill role name](/images/5.conformancepack/011-cloudformationstack.png)
