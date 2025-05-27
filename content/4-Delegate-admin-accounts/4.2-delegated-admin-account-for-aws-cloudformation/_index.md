---
title : "Register delegated administrator account for AWS CloudFormation"
date : "2025-05-14" 
weight : 2
chapter : false
pre : " <b> 4.2 </b>"
---

#### Steps to follow
1. Sign in to the AWS Management Console using the Audit account. You can verify the organization's account structure in the [Set up Landing Zone](../../2-Prerequiste/2.1-setupmultiaccount/2.1.2-createlandingzone/) step.

2. Run the following command:

    ```bash
    aws organizations register-delegated-administrator --service-principal=member.org.stacksets.cloudformation.amazonaws.com --account-id=$ACCOUNT_ID
    ```

3. To verify that the Audit account has been successfully registered as a delegated administrator for AWS CloudFormation, run the following command:

    ```bash
    aws organizations list-delegated-administrators --service-principal=member.org.stacksets.cloudformation.amazonaws.com
    ```