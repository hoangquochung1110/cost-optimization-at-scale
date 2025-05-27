---
title : "Member Accounts"
date : "2025-05-14" 
weight : 2
chapter : false
pre : " <b> 5.2.2 </b> "
---

Log in using a member account

![Member account](/images/5.conformancepack/019-memberaccount.png)

{{% notice info %}}
Here, for the sake of simplicity, we will use the Log Archive account
{{% /notice %}}

1. Check AWS Lambda function
    We have a single function that evaluates the AWS Config rule
    ![Lambda function](/images/5.conformancepack/020-lambda.png)

2. Check AWS Systems Manager Document:
    A document is shared to perform remediation if AWS Config detects a non-compliance event
    ![SSM Document](/images/5.conformancepack/021-ssm-document.png)

3. Check AWS Config Conformance Pack
    ![Conformance Pack](/images/5.conformancepack/022-conformance-pack.png)

4. Select **View** to see details
    ![Conformance Pack](/images/5.conformancepack/023-conformance-pack.png)
