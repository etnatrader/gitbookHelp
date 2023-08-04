---
description: Retrieve information about an ACH transfer
---

# Get an ACH Transfer's Info

### Overview

This endpoint enables you to retrieve detailed information about an ACH transfer.

{% swagger baseUrl="baseURL" path="/v{apiVersion}/transfers/ach/{transferID}" method="get" summary="Get an ACH Transfer's Info" %}
{% swagger-description %}
Returns the detailed information about the target transfer.
{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="number" %}
The version of the API. By default it's 

`1.0`

.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="transferId" type="integer" %}
The ID of the target ACH transfer.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" type="string" %}
The unique key of your app that identifies it when communicating with our service. Contact your administrator to get this key.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Authorization token. Must be provided in the following format: 

`Bearer token`

 (

`Bearer`

 \+ 1 space + the token)
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful request, the ACH transfer's information is returned." %}
```javascript
{
  "transferId": "62dac03d-f41f-4c2b-eca1-08d90984e4ba",
  "amount": 10,
  "actualAmount": 10,
  "achRelationshipId": "08947f4a-b9db-403c-5870-08d905847e9d",
  "closeAccount": false,
  "isDeposit": false,
  "iraDistribution": {​
    "reason": "RECHARACTERIZATION",
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
