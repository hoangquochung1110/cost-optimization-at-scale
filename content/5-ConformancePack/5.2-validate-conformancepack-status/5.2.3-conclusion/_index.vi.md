---
title : "Kết luận"
date : "2025-05-14" 
weight : 3
chapter : false
pre : " <b> 5.2.3 </b> "
---

Như vậy chúng ta đã triển khai hàng loạt AWS Config Conformance Pack lên các tài khoản thành viên.

Conformance pack bao gồm các quy tắc sau:

1. `CostOpt-S3-WithoutLifecycle`: phát hiện những S3 buckets không được cấu hình chính sách vòng đời.

2. `CostOpt-Ebs-Gp3`: nhận biết ổ cứng EBS mà không sử dụng loại ổ cứng gp3.

3. `CostOpt-Ebs-Unattached`: nhận biết các ổ cứng EBS không được gán (vào máy chủ EC2) có thể gây phát sinh chi phí không cần thiết.

Đây là đều là các quy tắc custom được định nghĩa logic đánh giá thông qua Lambda function. Trong số ba quy tắc này, chúng ta cũng cài đặt một hành động khắc phục sử dụng SSM Document `CostOptimizationConfPack-EbsGp3Remediation` để chuyển đổi một ổ cứng EBS bất kì sử dụng gp2 sang loại tiết kiệm chi phí gp3.

Tất cả các tài nguyên trên được tự động hoá thông qua dịch vụ CloudFormation