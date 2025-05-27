---
title : "Deploy Conformance Pack"
date : "2025-05-14" 
weight : 1
chapter : false
pre : " <b> 5.1 </b>"
---

### Overview

We will use the Audit account to deploy resources in the solution using AWS CloudFormation, including:

- A CloudFormation StackSet: deploys a set of resources in bulk to multiple accounts
- A CloudFormation Stack: deploys supporting resources to help distribute the resources defined in the CloudFormation StackSet to the designated member accounts.

![Architecture Overview](/images/5.conformancepack/007-architecture-overview.png)

### Deployment

1. Download the CloudFormation template [here](https://github.com/aws-samples/aws-config-cost-optimization-conformance-pack/releases/download/26/template.yaml)

2. Sign in to the AWS CloudFormation management console using the Audit account

3. In the main console, open **CloudShell**, select Actions then Upload file

    ![Create a stack](/images/5.conformancepack/008-cloudformationstack.png)

4. Verify the CloudFormation template has been successfully uploaded

    ![Upload a template](/images/5.conformancepack/009-cloudformationstack.png)

5. Then enter the following command to deploy the Conformance Pack:

    ```bash
    aws cloudformation deploy --template-file AWS_Config_Cost_Optimization_Template.yaml --stack-name CostOptimizationConfPack --parameter-overrides DeployingInDelegatedAdminAccount=True --capabilities CAPABILITY_IAM
    ```

    ![fill stack name](/images/5.conformancepack/010-cloudformationstack.png)

6. After approximately 5–10 minutes, the deployment completes successfully
    ![fill role name](/images/5.conformancepack/011-cloudformationstack.png)
