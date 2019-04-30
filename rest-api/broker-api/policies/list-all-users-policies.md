---
description: List security policies applicable to a particular user
---

# List All User's Policies

### Overview

This GET endpoint enables you to list all security policies that apply to the user whose authorization token is used in the request header. 

In ETNA Trader, each [user group](../../../administrator-guide/administrators-widgets/managing-user-groups.md) must have a [**security policy**](../../../administrator-guide/administrators-widgets/system-security-policies.md) that defines various security-related settings like minimum password length, two-factor authentication, and so forth. These security policies can be configured in the **System Security Policies** widget \(only available to administrators\).

There are three required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".

Here's the final template for this API request:

```text
GET apiURL/v1.0/policies
```

### Response

In response to this API request, you'll receive a JSON file with a list of the security policies that apply to this user.

```javascript
[
    {
        "Id": 1,
        "Name": "SecurityPolicy",
        "Date": "2016-08-04T10:40:13.527Z",
        "Rules": [
            {
                "Id": 5,
                "Name": "PasswordExpiration",
                "Attributes": {
                    "duration": "120"
                }
            },
            {
                "Id": 14,
                "Name": "SmsPassword",
                "Attributes": {}
            },
            {
                "Id": 16,
                "Name": "UserExpiration",
                "Attributes": {
                    "daysToExpiration": "0"
                }
            }
        ]
    }
]
```

where:

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal identifier of the security policy. |
| Name | This is the security policy's name. |
| Date | This is the date on which the security policy was created. |
| Rules | This is an array with the rules that define this security policy. |
| Id \(Rules\) | This is the internal identifier of the rule. |
| Name | This is the name of the rule. Usually it indicates the rule's purpose. |
| Attributes | This is an array of the rule's attributes. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve the list of a user's policies.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

