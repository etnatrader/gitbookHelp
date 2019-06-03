---
description: Deposit funds into an existing trading account
---

# Deposit Funds into an Account

## Overview

This POST endpoint enables you to deposit funds into a trading account. These funds are added to the Cash parameter and by extension affect the stock and options buying power.

{% hint style="warning" %}
In order to deposit funds into an existing trading account, you must use an [authorization token]() of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request]().
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountId** \(path\). This is the internal identifier of the trading account into which the funds must be deposited.
5. **depositValue** \(query\). This is the amount of funds that need to be deposited into the trading account.

Here's the final template for this API request:

```text
POST apiURL/v1.0/accounts/{accountID}/deposit
```

## Response

In response to this API request, you'll receive a JSON file confirming that the funds have been successfully deposited:

```javascript
{
  "Amount": 20000,
  "CreateDate": "2019-03-11T17:03:37.1243053Z",
  "Description": ""
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Amount | The amount of funds deposited \(in USD\). |
| CreateDate | The date on which the funds were deposited. |
| Description | Any additional information that might be relevant to the operation. |

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to deposit funds into an existing trading account.

### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for depositing funds into trading accounts, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

So be sure to use the authorization token generated with an administrator's credentials.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

In the following article we provide in-depth coverage of the syntax for this API request.

