---
title : "Xác minh các mối quan hệ tin cậy đã được thiết lập"
date : "2025-05-14" 
weight : 3 
chapter : false
pre : " <b> 3.3. </b> "
---

Xác minh các mối quan hệ tin cậy đã được thiết lập chính xác bằng lệnh sau

```
aws organizations list-aws-service-access-for-organization
```

Đầu ra nên chứa các giá trị sau:

```
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