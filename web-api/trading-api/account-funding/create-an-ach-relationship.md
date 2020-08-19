---
description: Bind an ACH relationship to a trading account
---

# Create an ACH Relationship

### Overview

After a trader has created a new [trading account](../trading-accounts/open-a-new-trading-account.md), they should proceed to deposit funds into it. ETNA Trader provides native functionality for managing deposits and withdrawals by means of ACH relationships. Essentially, a trader must establish an ACH relationship with their banking account and, once it's done, use it to deposit and withdraw funds to/from their banking account through ETNA Trader's web terminal and iOS apps.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountId** \(path\). This is the [internal identifier](../user-accounts/list-users-accounts/) of the trading account in ETNA Trader.
5. **model** \(body\). This is a JSON dictionary that contains detailed information about the new ACH relationship.

### Request Body

The body of this request represents the information about the to-be-created ACH relationship. It must be sent in the JSON format with the parameters described in the following table:

| Parameter | Description |
| :--- | :--- |
| RoutingNumber | This is the routing number of the bank who opened the banking account. You can view sample routing number on [this page](https://bankorganizer.com/list-of-routing-numbers/#bank-of-america). |
| AccountNumber | This is the number of the banking account in the target bank. For example: **987654321222**. |
| AccountOwnerName | This is the name of the banking account owner. For example: **Robert**. |
| Name | This is the name of the target bank. For example: **Citi Bank**. |
| ApprovalMethod | This is the approval method. The value of this parameter can be either **Instant** \(Plaid\) or **Manual** \(Micro deposits\). |

```javascript
{
  "RoutingNumber": "051000017",
  "AccountNumber": "987654321222",
  "AccountOwnerName": "Eugeny",
  "Name": "Citi Bank",
  "ApprovalMethod": "Instant"
}
```

Here's the final template for this API request:

```text
POST apiURL/v1.0/accounts/{accountId}/ach-relationships
```

### Response

In response to this API request, you will receive a JSON dictionary containing detailed information about the newly created ACH relationship.

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
| Id | This is the internal identifier of the newly created ACH relationship in ETNA Trader. |
| AccountId | This is an ETNA Trader's trading account to which the ACH relationship. |
| RoutingNumber | This is the routing number of the bank who opened the banking account. You can view sample routing number on [this page](https://bankorganizer.com/list-of-routing-numbers/#bank-of-america). |
| AccountNumber | This is the number of the banking account in the target bank. For example: **987654321222**. |
| AccountOwnerName | This is the name of the banking account owner. For example: **Robert**. |
| Name | This is the name of the target bank. For example: **Citi Bank**. |
| Status | This is the status of the ACH relationship. |
| CreatedAt | This is the precise time and date at which the ACH relationship was created. |
| ApprovalMethod | This is the approval method. The value of this parameter can be either **Instant** \(Plaid\) or **Manual** \(Micro deposits\). |
| Default | This boolean value indicates if this ACH relationship is a default one for this trading account. |

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

