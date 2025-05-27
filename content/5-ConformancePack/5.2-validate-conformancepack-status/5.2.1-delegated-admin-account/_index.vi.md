---
title : "Tài khoản Quản trị viên được uỷ quyền"
date : "2025-05-14" 
weight : 1
chapter : false
pre : " <b> 5.2.1 </b> "
---

1. Kiểm tra AWS Lambda function

    ![Lambda functions](/images/5.conformancepack/013-validate-lambda.png)

    Chúng ta có 3 lambda function:
    
    - `CostOptimizationConfPack-GetOrgDetailsFunction` chứa logic để liệt kê các tài khoản thành viên, loại trừ tài khoản quản trị khỏi mục tiêu triển khai của CloudFormation
    
    - `CostOptimizationConfPack-ShareDocumentFunction` chứa logic để chia sẻ SSM Document tạo bởi tài khoản Quản trị viên được uỷ quyền, chia sẻ quyền đọc đến tài khoản thành viên
    
    - `CostOptimizationConformanceConfigRuleFunction` định nghĩa logic đánh giá quy tắc custom của AWS Config

2. Kiểm tra AWS Systems Manager Document:

    - Di chuyển đến trang dịch vụ Systems Manager, rồi chọn mục "Documents" bên thanh điều hướng trái:

        ![Systems Manager overview](/images/5.conformancepack/014-systemsmanager.png)

    - Chọn tab "Owned by me" và kiểm tra chúng ta đã có một document có tên `CostOptimizationConfPack-EbsGp3Remediation`

        ![Systems Manager overview](/images/5.conformancepack/015-systemsmanager.png)

    - Chọn document và xem nội dung document:

        Document này nhận đầu vào là một EBS volume id và thực hiện chỉnh sửa volume type của EBS volume tương ứng sang gp3

        ![Systems Manager overview](/images/5.conformancepack/016-systemsmanager.png)

{{% notice note %}}
AWS Config Aggregator là một loại tài nguyên thu thập tập trung các cấu hình AWS Config và dữ liệu tuân thủ từ nhiều nguồn (chéo tài khoản, chéo Region)
{{% /notice %}}

3. Kiểm tra AWS Config Aggregator

    3.1 Truy cập dịch vụ AWS Config

    3.2 Ở thanh điều hướng trái, chọn **Aggregator** rồi chọn **Conformance packs**

    📌 Đây là bảng điều khiển giúp quản trị viên giám sát tập trung các quy tắc và tình trạng đáp ứng của các tài nguyên chéo tài khoản, toàn tổ chức

    ![AWS Config Aggregator](/images/5.conformancepack/017-configaggregator.png)

    3.3 Tuỳ thuộc vào có bao nhiêu tài khoản trong tổ chức của bạn mà bạn sẽ có bấy nhiêu Bộ Quy tắc tuân thủ (Conformance pack)

    3.4 Kiểm tra các quy tắc có trong bộ
        ![AWS Config Aggregator](/images/5.conformancepack/018-configaggregator.png)
