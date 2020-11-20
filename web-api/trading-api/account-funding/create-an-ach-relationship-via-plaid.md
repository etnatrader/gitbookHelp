---
description: Establish an ACH relationship and bind it to a trading account via Plaid
---

# Establish an ACH Relationship via Plaid

### Overview

This POST endpoint enables you to establish an ACH relationship via Plaid. Unlike the regular endpoint for [establishing ACH relationships](create-an-ach-relationship.md), this endpoint accepts parameters provided by Plaid after the user went through the Plaid's UI. 

After an ACH relationship is established, it'll take some time for the clearing firm to approve it. For Velox, If the data provided via this API request matches their data \(name, etc.\), the relationships will be established immediately. However, if there is a mismatch in the name, It will need to be review by the Correspondent via the Velox Portal. From the Velox portal the Correspondent can reject the request or approve it, depending on the mismatch. A bank statement my be required for validation.

Note that some clearing firms put limitations on the number of ACH relationships that can be established for one trading account. For Velox, you can establish up to **two** ACH relationships per trading account.

{% hint style="info" %}
Establishment of ACH relationships is available only for real trading accounts. If you attempt to establish an ACH relationship for a paper trading account, the request will fall through.
{% endhint %}

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountId** \(path\). This is the [internal identifier](../user-accounts/list-users-accounts/) of the trading account in ETNA Trader.
5. **model** \(body\). This is a JSON dictionary that contains detailed information about the new ACH relationship.

### Request Body

The body of this request represents the information about the to-be-established ACH relationship. It must be sent in the JSON format with the parameters described in the following table:

| Parameter | Description |
| :--- | :--- |
| Accounts | This is the account number provided by Plaid. |
| BankName | This is the name of the target bank provided by Plaid. For example: **Citi Bank**. |
| PublicToken | This is a token provided by Plaid. |

```javascript
{
  "Accounts": [
    "aGdSP4Lj71QRqIenrpvs"
  ],
  "BankName": "Bank of America",
  "PublicToken": "public-sandbox-someToken"
}
```

Here's the final template for this API request:

```text
POST apiURL/v1.0/accounts/{accountId}/ach-relationships/plaid
```

### Response

In response to this API request, you will receive a JSON dictionary containing detailed information about the newly established ACH relationship.

```javascript
{
  "Id": "someID-da10-40bc-060a-08d7bacaad26",
  "AccountId": 0,
  "RoutingNumber": "051000017",
  "AccountNumber": "987654321222",
  "AccountOwnerName": "Eugeny",
  "Name": "Citi Bank",
  "Status": "Pending",
  "CreatedAt": "2020-03-16T15:38:41.5766667Z",
  "ApprovalMethod": "Instant",
  "Default": false
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal identifier of the newly established ACH relationship in ETNA Trader. |
| AccountId | This is an ETNA Trader's trading account to which the ACH relationship. |
| RoutingNumber | This is the routing number of the bank who opened the banking account. You can view sample routing number on [this page](https://bankorganizer.com/list-of-routing-numbers/#bank-of-america). |
| AccountNumber | This is the number of the banking account in the target bank. For example: **987654321222**. |
| AccountOwnerName | This is the name of the banking account owner. For example: **Robert**. |
| Name | This is the name of the target bank. For example: **Citi Bank**. |
| Status | This is the status of the ACH relationship. |
| CreatedAt | This is the precise time and date at which the ACH relationship was established. |
| ApprovalMethod | This is the approval method. The value of this parameter can be either **Instant** \(Plaid\) or **Manual** \(Micro deposits\). |
| Default | This boolean value indicates if this ACH relationship is the default one for this trading account. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to send a request to establish a new ACH relationship. 

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Failing to Specify All Body Parameters

Another common mistake when making this request is failing to specify all of the required body parameters. Doing so will result in the 500 status code and the following error message:

```javascript
{
    "message": "An error occurred while processing your request",
    "error": "Unexpected server error"
}
```

