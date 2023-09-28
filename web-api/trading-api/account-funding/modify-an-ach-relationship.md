# Modify an ACH Relationship

This endpoint enables you to modify a bank name of the existing ACH relationship.

{% swagger baseUrl="baseURL" path="/v{version}/accounts/{accountId}/ach-relationships/{id}" method="put" summary="Update An ACH Relationship" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of the API. By default it's `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="accountId" type="Integer" required="true" %}
ID of the trading account.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" type="String" required="true" %}
The unique key of your app that identifies it when communicating with our service. Contact your administrator to get this key.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
Authorization token. Must be provided in the following format: `Bearer token` (`Bearer` + 1 space + the token)
{% endswagger-parameter %}

{% swagger-parameter in="path" name="id" type="String" required="true" %}
This is the ID of the ACH relationship in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="model" type="String" required="true" %}
JSON object containing the new name of the linked bank.



{ "Name": "string" }
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful request, updated ACH relationship is returned." %}
```javascript
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "AccountId": 0, // Internal id of the account on ETNA platform
  "ExternalId": "string", // An id of the relationship in APEX
  "RoutingNumber": "string",
  "AccountNumber": "string",
  "AccountOwnerName": "string",
  "Name": "string", // A new name of the bank
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
