---
title : "Validate trusted access relationships"
date : "2025-05-14"
weight : 3
chapter : false
pre : " <b> 3.3. </b>"
---

Keep previous CloudShell session and verify the trusted relationships have been correctly established by running the following command:

```bash
aws organizations list-aws-service-access-for-organization
```

The output should include the following values:

```json
{
  "EnabledServicePrincipals": [
    {
      "ServicePrincipal": "config-multiaccountsetup.amazonaws.com",
      "DateEnabled": "2025-05-24T16:14:01.992000+07:00"
    },
    {
      "ServicePrincipal": "config.amazonaws.com",
      "DateEnabled": "2025-05-24T16:15:21.780000+07:00"
    },
    {
      "ServicePrincipal": "member.org.stacksets.cloudformation.amazonaws.com",
      "DateEnabled": "2025-05-24T16:22:41.608000+07:00"
    }
  ]
}
```