---
title : "Introduction"
date : "2025-05-14"
weight : 1
chapter : false
pre : " <b> 1. </b> "
---

#### Overview

**AWS Config** is a service that continuously assesses, audits, and evaluates the configurations and relationships of AWS, on-premises, and multi-cloud resources. This guide shows how to enhance the value of AWS Config by deploying an organization-wide solution that automatically evaluates resources against cost optimization best practices using Conformance Packs.

A **Conformance Pack** is a collection of AWS Config rules and remediation actions that provides a comprehensive compliance framework to codify and deploy security, operational, or cost optimization checks within a single account and region or across an entire AWS Organization. These rules automatically monitor and assess resources to detect compliance against each rule's defined logic. AWS Config offers both **Managed Rules** (pre-built, customizable rules) and **Custom Rules** (allowing custom logic via **AWS Lambda** or AWS CloudFormation Guard—a policy-as-code language).

When a resource violates a rule's logic, it is marked **Noncompliant**. You can choose to remediate manually or automate remediation using **AWS Systems Manager** Automation—a central operations hub with built-in runbooks to automatically fix noncompliant resources or trigger event-driven workflows like alerting teams for action.

#### Solution Overview

This solution enables organizations already using AWS Config to maximize value by integrating automated cost optimization governance into their existing infrastructure. It provides three sample custom rules representing cost optimization best practices, continuously monitoring resource configurations and reporting compliance status to a centralized AWS Config Aggregator in the delegated administrator account for simplified monitoring and reporting.

![Architecture Overview](/images/5.conformancepack/007-architecture-overview.png)

The implementation includes the following governance rules:

- **Rule 1**: Detect gp2 EBS volumes  
  Remediation: Automatically convert to gp3 volumes  
- **Rule 2**: Detect unattached EBS volumes  
- **Rule 3**: Detect S3 buckets missing lifecycle policies  

When resources do not meet rule criteria, both the individual resource and the corresponding rule in the conformance pack are marked Noncompliant. Rule 1 integrates an on-demand or automated remediation by invoking an SSM Automation runbook to convert EBS gp2 volumes to gp3. This upgrade delivers independent IOPS and throughput without additional storage, yielding up to 20% cost savings per GB compared to gp2 volumes.

{{% notice info %}}
Important: AWS Config is a paid service—review pricing documentation to understand organization-level cost implications before a broad deployment if Config is not already in use.
{{% /notice %}}

This solution supports deployment across AWS Organizations regardless of AWS Control Tower status. AWS Control Tower provides an organization and governance framework for multi-account environments with established best practices. Figure 1 illustrates deploying the Cost Optimization Conformance Pack on a sample OU structure in a Control Tower environment with member accounts. The Security OU holds the auditing account, designated as the delegated administrator for both AWS Config and AWS CloudFormation. This designation provides the necessary permissions to deploy the Cost Optimization Conformance Pack and related resources via CloudFormation StackSets across accounts in the organization. The CloudFormation stack includes the custom Cost Optimization Conformance Pack rules, Lambda functions, and SSM documents referenced by those rules. Two custom IAM roles are provided through the StackSet to allow Lambda and SSM document execution. All organization-wide components are deployed from the central auditing account, simplifying solution management.

AWS Config evaluates resource compliance with conformance pack rules periodically or triggered by configuration changes. The AWS Config Aggregator in the auditing account consolidates and centralizes compliance data collected from member accounts, facilitating regional analysis and reporting.
