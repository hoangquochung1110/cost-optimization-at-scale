---
title : "Conclusion"
date : "2025-05-14" 
weight : 3
chapter : false
pre : " <b> 5.2.3 </b> "
---

Thus, we have deployed a series of AWS Config Conformance Packs to the member accounts.

The conformance pack includes the following rules:

1. `CostOpt-S3-WithoutLifecycle`: detects S3 buckets that are not configured with a lifecycle policy.

2. `CostOpt-Ebs-Gp3`: identifies EBS volumes that are not using the gp3 volume type.

3. `CostOpt-Ebs-Unattached`: identifies unattached EBS volumes (not attached to EC2 instances) that may incur unnecessary costs.

These are all custom rules with evaluation logic defined via Lambda functions. Among these three rules, we also implement a remediation action using the SSM Document `CostOptimizationConfPack-EbsGp3Remediation` to convert any EBS volume using gp2 to the cost-saving gp3 type.

All of the above resources are automated through the CloudFormation service.