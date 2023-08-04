# Deposit / Withdraw Funds via ACH

This endpoint enables you to deposit or withdraw funds to/from an ACH-based banking account.&#x20;

{% hint style="info" %}
Deposits and withdrawals performed through ACH relationships will be reflected in trading account balances before the start of the following trading session (after ETNA Trader receives SOD files).
{% endhint %}

{% swagger baseUrl="baseURL" path="/v{version}/accounts/{accountId}/transfers/ach" method="post" summary="Send An ACH Transfer To The Clearing Firm" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of the API. By default it's 

`1.0`

.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="accountId" type="Integer" required="true" %}
ID of the trading account.
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
JSON object with the detailed information about a transfer.


{% endswagger-parameter %}

{% swagger-response status="200" description="Successful request, the ACH transfer was successfully sent to the clearing firm." %}
```
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "AccountId": 0,
  "ExternalId": "string",
  "Mechanism": "string",
  "IsDeposit": true,
  "Status": "string",
  "Comment": "string",
  "Amount": 0,
  "TotalAmount": 0,
  "TransferDate": "2023-08-04T10:18:53.817Z",
  "CreatedAt": "2023-08-04T10:18:53.817Z",
  "ClearingAccountNumber": "string"
}
```
{% endswagger-response %}
{% endswagger %}

#### Body Syntax

The body of the request represents a JSON file containing all required parameters for performing a funds transfer.

| Parameter         | Description                                                                                                                                        |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| AchRelationshipId | This is the ACH relationship through which the transfer will be performed.                                                                         |
| Amount            | This is the amount of funds to be transferred. The value must be provided in US dollars.                                                           |
| CloseAccount      | This boolean value indicates if the trading account must be closed after the transfer is performed. Only applicable to withdrawal operations.      |
| DaysToHoldFunds   | This is the number of days by which the transfer must be delayed.                                                                                  |
| IsIncoming        | This boolean value indicates the transaction type. To perform a deposit, set it to `true`. Conversely, to perform a withdrawal, set it to `false`. |

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
