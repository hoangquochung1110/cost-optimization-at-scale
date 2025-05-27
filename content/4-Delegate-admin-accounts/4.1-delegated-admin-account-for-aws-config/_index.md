---
title : "Register delegated administrator account for AWS Config"
date : "2025-05-14" 
weight : 1 
chapter : false
pre : " <b> 4.1 </b>"
---

#### Steps to follow
1. Sign in to the AWS Management Console using the Audit account. You can verify the organization's account structure in the [Set up Landing Zone](../../2-Prerequiste/2.1-setupmultiaccount/2.1.2-createlandingzone/) step.

2. Run the following commands:

    ```bash
    aws organizations register-delegated-administrator --account-id $ACCOUNT_ID --service-principal config-multiaccountsetup.amazonaws.com
    ```

    and

    ```bash
    aws organizations register-delegated-administrator --account-id $ACCOUNT_ID --service-principal config.amazonaws.com
    ```

3. To verify that the Audit account has been successfully registered as a delegated administrator for AWS Config, run the following commands:

    ```bash
    aws organizations list-delegated-administrators --service-principal=config.amazonaws.com
    ```

    and

    ```bash
    aws organizations list-delegated-administrators --service-principal=config-multiaccountsetup.amazonaws.com
    ```