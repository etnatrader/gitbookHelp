---
description: >-
  Deposit and withdraw funds to/from a specific trading account via ACH
  relationships
---

# Deposit / Withdraw Funds via ACH

### Overview

This POST endpoint enables you to deposit or withdraw funds to/from an ACH-based banking account. 

{% hint style="info" %}
Deposits and withdrawals performed through ACH relationships will be reflected in trading account balances before the start of the following trading session \(after ETNA Trader receives SOD files\).
{% endhint %}

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountId** \(path\). This is the [internal identifier](../../user-accounts/list-users-accounts/) of the trading account in ETNA Trader.
5. **model** \(body\). This is a JSON file containing detailed information about the funds transfer.

#### Body Syntax

The body of the request represents a JSON file containing all required parameters for performing a funds transfer.

| Parameter | Description |
| :--- | :--- |
| AchRelationshipId | This is the ACH relationship through which the transfer will be performed. |
| Amount | This is the amount of funds to be transferred. The value must be provided in US dollars. |
| CloseAccount | This boolean value indicates if the trading account must be closed after the transfer is performed. Only applicable to withdrawal operations. |
| DaysToHoldFunds | This is the number of days by which the transfer must be delayed. |
| IsIncoming | This boolean value indicates the transaction type. To perform a deposit, set it to `true`. Conversely, to perform a withdrawal, set it to `false`. |

For example:

```javascript
{
   "AchRelationshipId":"91fde713-6c64-4ef3-0606-08d7bacaad26",
   "Amount":50,
   "CloseAccount":false,
   "DaysToHoldFunds":0,
   "IsIncoming":true
}
```

Here's the final template for this API request:

```text
POST apiURL/v1.0/accounts/{accountId}/transfers/ach
```

### Response

In response to this API request, you will receive a JSON dictionary containing detailed information about the transfer.

```javascript
{
  "Id": "0306a11e-a13c-4741-6cec-08d7bc5cbf81",
  "AccountId": 0,
  "Mechanism": "ACH",
  "IsDeposit": true,
  "Status": "Submitted",
  "Amount": 50,
  "TotalAmount": 0,
  "CreatedAt": "2020-03-17T17:00:17.0566667Z",
  "ClearingAccountNumber": "5DP05506"
}
```

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to send a request to deposit or withdraw funds.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

