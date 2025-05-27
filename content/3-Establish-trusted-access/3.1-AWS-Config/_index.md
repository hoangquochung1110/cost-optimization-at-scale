---
title : "Enable trusted access between AWS Organizations and AWS Config"
date : "2025-05-14"
weight : 1
chapter : false
pre : " <b> 3.1. </b>"
---

#### Overview
This setup allows AWS Config to perform cross-account operations without requiring administrators to manually configure permission policies in each account.

The following steps include:

- enable the core AWS Config service integration
- enable multi-account deployment and aggregation features

#### Steps to follow

1. Sign in to the AWS Management Console as the management account and open AWS Config.

2. Open AWS CloudShell.
![Activate trusted access banner](/images/3.establish/001-cloudshell.png)

3. Execute the following two commands:

    ```bash
    aws organizations enable-aws-service-access --service-principal=config-multiaccountsetup.amazonaws.com
    ```

    ```bash
    aws organizations enable-aws-service-access --service-principal=config.amazonaws.com
    ```
