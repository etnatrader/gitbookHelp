---
description: Establish and bind an ACH relationship to a trading account.
---

# Create A New ACH Relationship

### Overview

After a trader has created a new [trading account](../trading-accounts/open-a-new-trading-account.md), they should proceed to deposit funds into it. ETNA Trader provides native functionality for managing deposits and withdrawals by means of ACH relationships. Essentially, a trader must establish an ACH relationship with their banking account and, once it's done, use it to deposit and withdraw funds to/from their banking account through ETNA Trader's web terminal and iOS apps.

After an ACH relationship is established, it'll take some time for the clearing firm to approve it. For Velox, If the data provided via this API request matches their data (name, etc.), the relationships will be established immediately. However, if there is a mismatch in the name, It will need to be review by the Correspondent via the Velox Portal. From the Velox portal the Correspondent can reject the request or approve it, depending on the mismatch. A bank statement my be required for validation.

Note that some clearing firms put limitations on the number of ACH relationships that can be established for one trading account. For Velox, you can establish up to **two** ACH relationships per trading account.

{% hint style="info" %}
Establishment of ACH relationships is available only for real trading accounts. If you attempt to establish an ACH relationship for a paper trading account, the request will fall through.
{% endhint %}

{% swagger baseUrl="baseURL" path="/v{version}/accounts/{accountId}/ach-relationships" method="post" summary="Create A New ACH Relationship" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of the API. By default it's `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="accountId" type="Integer" required="true" %}
ID of the trading account to which the new ACH relationship will be bound.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" type="String" required="true" %}
The unique key of your app that identifies it when communicating with our service. Contact your administrator to get this key.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
Authorization token. Must be provided in the following format: `Bearer token` (`Bearer` + 1 space + the token)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="model" type="String" required="true" %}
JSON object containing all parameters required for a new ACH relationship.
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful request, a new ACH relationship has been created." %}
```javascript
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "AccountId": 0, // Internal id of the account on ETNA platform
  "ExternalId": "string", // An id of the relationship in APEX
  "RoutingNumber": "string",
  "AccountNumber": "string",
  "AccountOwnerName": "string",
  "Name": "string", // A name of the target bank
  "Status": "string", // Status of the ACH relationship
  "CreatedAt": "2023-08-04T10:18:52.957Z",
  "CancelDate": "2023-08-04T10:18:52.957Z",
  "CancelReason": "string",
  "ApprovalMethod": "string", // Can be instant (Plaid) or Manual (Micro deposits)
  "Default": true, // Whether the ACH relationship is the default one for this trading account
  "BankAccountType": "string"
}
```
{% endswagger-response %}
{% endswagger %}

### Request Body

The body of this request represents the information about the to-be-established ACH relationship. It must be sent in the JSON format with the parameters described in the following table:

| Parameter        | Description                                                                                                                                                                                   |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RoutingNumber    | This is the routing number of the bank who opened the banking account. You can view sample routing number on [this page](https://bankorganizer.com/list-of-routing-numbers/#bank-of-america). |
| AccountNumber    | This is the number of the banking account in the target bank. For example: **987654321222**. The number of digits must not be lower than ten.                                                 |
| AccountOwnerName | This is the name of the banking account owner. For example: **Robert**.                                                                                                                       |
| Name             | This is the name of the target bank. For example: **Citi Bank**.                                                                                                                              |
| ApprovalMethod   | This is the approval method. The value of this parameter can be either **Instant** (Plaid) or **Manual** (Micro deposits).                                                                    |
| BankAccountType  | The type of a bank account. It can have one of two possible values: **Checking** or **Savings**.                                                                                              |

```javascript
{
  "RoutingNumber": "051000017",
  "AccountNumber": "987654321222",
  "AccountOwnerName": "Eugeny",
  "Name": "Citi Bank",
  "ApprovalMethod": "Instant",
  "BankAccountType": "Checking"
}
```

