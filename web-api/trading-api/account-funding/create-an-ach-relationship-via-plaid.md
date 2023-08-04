---
description: Establish an ACH relationship and bind it to a trading account via Plaid
---

# Create an ACH Relationship via Plaid

### Overview

This POST endpoint enables you to establish an ACH relationship via Plaid. Unlike the regular endpoint for [establishing ACH relationships](create-an-ach-relationship.md), this endpoint accepts parameters provided by Plaid after the user went through the Plaid's UI.&#x20;

After an ACH relationship is established, it'll take some time for the clearing firm to approve it. For Velox, If the data provided via this API request matches their data (name, etc.), the relationships will be established immediately. However, if there is a mismatch in the name, It will need to be review by the Correspondent via the Velox Portal. From the Velox portal the Correspondent can reject the request or approve it, depending on the mismatch. A bank statement my be required for validation.

Note that some clearing firms put limitations on the number of ACH relationships that can be established for one trading account. For Velox, you can establish up to **two** ACH relationships per trading account.

{% hint style="info" %}
Establishment of ACH relationships is available only for real trading accounts. If you attempt to establish an ACH relationship for a paper trading account, the request will fall through.
{% endhint %}

{% swagger baseUrl="baseURL" path="/v{version}/accounts/{accountId}/ach-relationships/plaid" method="post" summary="Create ACH Relationships From A PLAID Link" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of the API. By default it's 

`1.0`

.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="accountId" type="Integer" required="true" %}
ID of the trading account to which the new ACH relationship will be bound.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" type="String" required="true" %}
The unique key of your app that identifies it when communicating with our service. Contact your administrator to get this key.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
Authorization token. Must be provided in the following format: 

`Bearer token`

 (

`Bearer`

 \+ 1 space + the token)
{% endswagger-parameter %}

{% swagger-parameter in="body" name="model" type="String" required="true" %}
JSON object containing PLAID data to identify the bank and accounts.
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful request, ACH relationships have been created." %}
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

| Parameter   | Description                                                                        |
| ----------- | ---------------------------------------------------------------------------------- |
| Accounts    | This is the account number provided by Plaid.                                      |
| BankName    | This is the name of the target bank provided by Plaid. For example: **Citi Bank**. |
| PublicToken | This is a token provided by Plaid.                                                 |
| AccountId   | ID of the trading account to which the new ACH relationship will be bound.         |

```javascript
{
  "Accounts": [
    "aGdSP4Lj71QRqIenrpvs"
  ],
  "BankName": "Bank of America",
  "PublicToken": "public-sandbox-someToken",
  "AccountId": "54312"
}
```
