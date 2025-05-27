+++
title = "Dọn dẹp tài nguyên  "
date = 2021
weight = 7
chapter = false
pre = "<b>7. </b>"
+++

Chúng ta sẽ tiến hành các bước sau để xóa các tài nguyên chúng ta đã tạo trong bài thực hành này.

#### Dọn dẹp tất cả tài nguyên tạo bởi CloudFormation

1. Truy cập [giao diện quản trị dịch vụ CloudFormation](https://console.aws.amazon.com/cloudformation) sử dụng tài khoản Quản trị viên được uỷ quyền.
  - Mở CloudShell và nhập lệnh sau: `aws cloudformation delete-stack --stack-name CostOptimizationConfPack`
      ![CloudFormation stack delete](/images/7.clean/001-clean.png)
  - Chờ chốc lát và quan sát đảm bảo tất cả các stack đều được xoá
      ![CloudFormation stack delete](/images/7.clean/002-clean.png)


2. Tiếp dụng sử dụng phiên CloudShell trên để huỷ cấp quyền quản trị cho tài khoản kiểm toán. Nhập hai lệnh sau:
    - `aws organizations deregister-delegated-administrator --account-id $ACCOUNT_ID --service-principal config-multiaccountsetup.amazonaws.com`

    - `aws organizations deregister-delegated-administrator --account-id 123412341234 --service-principal config.amazonaws.com`

#### Xoá ổ cứng EBS

1. Truy cập [giao diện quản trị dịch vụ EC2](https://console.aws.amazon.com/ec2) sử dụng tài khoản tài khoản thành viên

2. Thực hiện xoá ổ cứng
    ![EBS volume delete](/images/7.clean/003-clean.png)

