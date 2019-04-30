---
description: Update an existing trading account
---

# Update a Trading Account

### Overview

This PUT endpoint enables you to update an existing trading account. To avoid having conflicts with the clearing firm, please refrain from modifying critical parameters like _ClearingAccount_.

{% hint style="warning" %}
In order to modify an existing trading account, you must use an [authorization token]() of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request]().
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountId** \(path\). This is the internal identifier of the trading account that needs to be modified.
5. **accountModel** \(body\). This is a JSON file with the updated information about the modified trading account.

#### Request Body Sample

Following is a sample JSON file that contains information about the modified account:

```javascript
{
  "SubscriptionPlanId": 0,
  "ClearingAccount": "6689",
  "CreatedDate": "2019-03-11T10:37:02.671Z",
  "ModifiedDate": "2019-03-11T10:37:02.671Z",
  "Enabled": true,
  "IsChanged": true,
  "Cash": 10000, //adding some cash to the account
  "Currency": "string",
  "Status": "UnSpecified",
  "CommissionPlan": "string",
  "RepCode": "string",
  "MarginInterestRate": 0,
  "CashInterestRate": 0,
  "CloseEquity": 0,
  "OpenExcess": 0,
  "OptionLevel": 0,
  "MarginType": "Empty",
  "Permissions": "Empty",
  "BaseCash": 0,
  "Sweep": 0,
  "OwnerType": "IndividualCustomer",
  "DayTradingBuyingPower": 0,
  "DayTrades": 0,
  "SmaBalance": 0,
  "HouseCall": 0,
  "MaintenanceCall": 0,
  "EquityCall": 0,
  "InitialCall": 0,
  "DayTradeCall": 0,
  "TradeDayBalance": 0,
  "MoneyMarket": 0,
  "Cip": 0,
  "IsAverageAccount": true,
  "MarginEquity": 0,
  "ClearingFirm": "string",
  "ExcessEquity": 0
}
```

Here's the final template for this API request:

```text
PUT apiURL/v1.0/accounts
```

### Response

In response to this API request, you'll receive a JSON file with information about the updated trading account, confirming that the fields have been modified.

```javascript
{
  "Id": 6689,
  "SubscriptionPlanId": 0,
  "ClearingAccount": "6689",
  "CreatedDate": "2019-03-11T10:37:02.671Z",
  "ModifiedDate": "2019-03-11T15:36:59.9713282Z",
  "Enabled": true,
  "IsChanged": true,
  "Cash": 10000,
  "Currency": "str",
  "Status": "UnSpecified",
  "CommissionPlan": "string",
  "RepCode": "string",
  "MarginInterestRate": 0,
  "CashInterestRate": 0,
  "CloseEquity": 0,
  "OpenExcess": 0,
  "OptionLevel": 0,
  "MarginType": "Empty",
  "Permissions": "Empty",
  "BaseCash": 0,
  "Sweep": 0,
  "OwnerType": "IndividualCustomer",
  "DayTradingBuyingPower": 0,
  "DayTrades": 0,
  "SmaBalance": 0,
  "HouseCall": 0,
  "MaintenanceCall": 0,
  "EquityCall": 0,
  "InitialCall": 0,
  "DayTradeCall": 0,
  "TradeDayBalance": 0,
  "MoneyMarket": 0,
  "Cip": 0,
  "IsAverageAccount": true,
  "MarginEquity": 0,
  "ClearingFirm": "string",
  "ExcessEquity": 0
}
```

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to modify existing trading accounts.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for modifying existing trading accounts, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

So be sure to use the authorization token generated with an administrator's credentials.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```



