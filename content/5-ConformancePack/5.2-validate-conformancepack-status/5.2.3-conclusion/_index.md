---
title : "Kết luận"
date : "2025-05-14" 
weight : 3
chapter : false
pre : " <b> 5.3.3 </b> "
---

Như vậy chúng ta đã triển khai hàng loạt AWS Config Conformance Pack lên các tài khoản thành viên.

Conformance pack bao gồm các quy tắc sau:

1. CostOpt-S3-WithoutLifecycle: phát hiện những S3 buckets không được cấu hình chính sách vòng đời.

2. CostOpt-Ebs-Gp3: nhận biết ổ cứng EBS mà không sử dụng loại ổ cứng gp3.

3. CostOpt-Ebs-Unattached: nhận biết các ổ cứng EBS không được gán (vào máy chủ EC2) có thể gây phát sinh chi phí không cần thiết.

Trong số ba quy tắc này, chúng ta cũng cài đặt một hành động khắc phục sử dụng SSM Document `CostOptimizationConfPack-EbsGp3Remediation` to convert eligible EBS volumes from other types (
like gp2) to the more cost-effective gp3 type without changing other volume
attributes.