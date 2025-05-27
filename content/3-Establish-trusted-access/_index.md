---
title : "Establish Trusted Access in AWS Organizations"
date : "2025-05-14"
weight : 3
chapter : false
pre : " <b> 3. </b> "
---

In this step, we will create a trusted relationship between AWS Organizations and the service principals for AWS CloudFormation and AWS Config.

This setup enables:

- Multi-account capabilities – Trusted access allows AWS services to operate across multiple accounts in your organization without manually configuring permissions in each account.
- Centralized management – Services like AWS Config, CloudTrail, and Security Hub can be deployed and managed organization-wide from the management account.
- Service-linked roles – Trusted access automatically creates the service-linked roles required in member accounts.

### Contents

3.1. [Enable trusted access for AWS Config](3.1-AWS-Config/)  
3.2. [Enable trusted access for AWS CloudFormation](3.2-AWS-CloudFormation/)