---
title : "Enable trusted access between AWS Organizations and AWS CloudFormation"
date : "2025-05-14"
weight : 2
chapter : false
pre : " <b> 3.2. </b>"
---

#### Overview
Enables CloudFormation StackSets to perform operations on member accounts without requiring individual permission configurations in each account.

#### Steps to follow

1. Sign in to the AWS Management Console as the management account and open AWS CloudFormation.

2. Open AWS CloudShell.
![Activate trusted access banner](/images/3.establish/001-cloudshell.png)

3. Execute the following command:

    ```bash
    aws organizations enable-aws-service-access --service-principal=member.org.stacksets.cloudformation.amazonaws.com
    ```

