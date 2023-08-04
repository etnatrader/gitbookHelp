# Remove an ACH Relationship

### Overview

This endpoint enables you to delete an existing ACH relationship from a particular trading account.

{% swagger baseUrl="baseURL" path="/v{version}/accounts/{accountId}/ach-relationships/{id}" method="delete" summary="Remove An ACH Relationship" %}
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

{% swagger-parameter in="path" name="id" type="String" required="true" %}
This is the ID of the ACH relationship in ETNA Trader.
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful request, the ACH relationship has been removed." %}
```
{
  "Id": "40ee3617-7a67-45dd-0609-08d7bacaad26",
  "AccountId": 0,
  "ExternalId": "5e6f80963c3477ba9dc1f98a",
  "RoutingNumber": "051000017",
  "AccountNumber": "987654321222",
  "AccountOwnerName": "Eugeny",
  "Name": "Main Citi Bank Account",
  "Status": "Canceled",
  "CreatedAt": "2020-03-16T13:35:18.0133333Z",
  "CancelDate": "2020-03-16T17:53:54.4806035Z",
  "CancelReason": "Closed the banking account",
  "ApprovalMethod": "Instant",
  "Default": false
}
```
{% endswagger-response %}
{% endswagger %}
