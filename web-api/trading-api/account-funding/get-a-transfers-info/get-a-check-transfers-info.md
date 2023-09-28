---
description: Retrieve information about a check transfer
---

# Get a Check Transfer's Info

### Overview

This GET endpoint enables you to retrieve detailed information about a check transfer.

{% swagger baseUrl="baseURL" path="/v{apiVersion}/transfers/check/{transferID}" method="get" summary="Get a Check Transfer's Info" %}
{% swagger-description %}
Returns the detailed information about the target transfer.
{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="number" %}
The version of the API. By default it's `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="transferId" type="integer" %}
The ID of the target check transfer.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" type="string" %}
The unique key of your app that identifies it when communicating with our service. Contact your administrator to get this key.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Authorization token. Must be provided in the following format: `Bearer token` (`Bearer` + 1 space + the token)
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful request, the check transfer's information is returned." %}
```javascript
{
  "transferId": "78c6c7cc-d046-4411-44ea-08d9098ea314",
  "amount": 10,
  "actualAmount": 0,
  "closeAccount": false,
  "memos": [
    "string"
  ],
  "deliveryMethod": "STANDARD",
  "iraDistribution": {
    "reason": "NORMAL",
    "federalTaxType": "FIXED",
    "stateTaxType": "FIXED",
    "federalTaxAmount": 0,
    "stateTaxAmount": 0
  }
}
```
{% endswagger-response %}

{% swagger-response status="409" description="Unable to find the transfer by its ID." %}
```
No response
```
{% endswagger-response %}
{% endswagger %}
