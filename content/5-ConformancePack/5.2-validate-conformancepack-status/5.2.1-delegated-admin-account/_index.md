---
title : "Delegated Administrator Account"
date : "2025-05-14" 
weight : 1
chapter : false
pre : " <b> 5.2.1 </b> "
---

1. Check AWS Lambda functions

    ![Lambda functions](/images/5.conformancepack/013-validate-lambda.png)

    We have 3 Lambda functions:
    
    - `CostOptimizationConfPack-GetOrgDetailsFunction` contains logic to list member accounts, excluding the administrator account from the CloudFormation deployment targets
    
    - `CostOptimizationConfPack-ShareDocumentFunction` contains logic to share the SSM Document created by the delegated administrator account, granting read access to member accounts
    
    - `CostOptimizationConformanceConfigRuleFunction` defines the evaluation logic for the custom AWS Config rule

2. Check AWS Systems Manager Document:

    - Navigate to the Systems Manager service page, then select "Documents" from the left navigation pane:

        ![Systems Manager overview](/images/5.conformancepack/014-systemsmanager.png)

    - Select the "Owned by me" tab and verify that there is a document named `CostOptimizationConfPack-EbsGp3Remediation`

        ![Systems Manager overview](/images/5.conformancepack/015-systemsmanager.png)

    - Select the document and view its content:

        This document takes an EBS volume ID as input and modifies the corresponding EBS volume type to gp3

        ![Systems Manager overview](/images/5.conformancepack/016-systemsmanager.png)

{{% notice note %}}
AWS Config Aggregator is a resource type that centrally collects AWS Config configuration and compliance data from multiple sources (cross-account, cross-Region)
{{% /notice %}}

3. Check AWS Config Aggregator

    3.1 Access the AWS Config service

    3.2 In the left navigation pane, select **Aggregator** and then **Conformance packs**

    📌 This is the dashboard that allows administrators to centrally monitor rules and compliance status of resources across accounts and the entire organization

    ![AWS Config Aggregator](/images/5.conformancepack/017-configaggregator.png)

    3.3 Depending on how many accounts are in your organization, you will have that many Conformance packs

    3.4 Check the rules included in the pack
        ![AWS Config Aggregator](/images/5.conformancepack/018-configaggregator.png)
