---
title : "Activate Delegated Administrator Accounts"
date : "2025-05-14"
weight : 4
chapter : false
pre : " <b> 4. </b> "
---

In this step, we designate a member account (not the management account) to perform specific administrative tasks for designated AWS services across your organization.

{{% notice info %}}
The management account should be used only for organizational management tasks.
{{% /notice %}}

In this section, we will create an S3 bucket and configure session log storage to capture the details of commands used in a session.

### Why ?

- Separation of duties – Administrative responsibilities can be distributed to specialized teams using dedicated member accounts.
- Reduced management account access – Fewer individuals need access to the management account, improving security.
- Service specialization – Service administrators can manage their respective services organization-wide.
- Operational efficiency – Service administrators can work directly from their assigned accounts without switching to the management account.
- Compliance requirements – Meets compliance needs that require separation of duties.

### Contents

- [Register a delegated administrator for AWS Config](./4.1-delegated-admin-account-for-aws-config/)  
- [Register a delegated administrator for AWS CloudFormation](./4.2-delegated-admin-account-for-aws-cloudformation/)  
- [Create required IAM roles](./4.3-createrole/)