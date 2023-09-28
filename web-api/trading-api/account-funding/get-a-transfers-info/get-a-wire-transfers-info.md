---
description: Retrieve information about a wire transfer
---

# Get a Wire Transfer's Info

### Overview

This GET endpoint enables you to retrieve detailed information about a wire transfer.

{% swagger baseUrl="baseURL" path="/v{apiVersion}/transfers/wire/{transferID}" method="get" summary="Get a Wire Transfer's Info" %}
{% swagger-description %}
Returns the detailed information about the target transfer.
{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="number" %}
The version of the API. By default it's `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="transferId" type="integer" %}
The ID of the target wire transfer.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" type="string" %}
The unique key of your app that identifies it when communicating with our service. Contact your administrator to get this key.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" %}
Authorization token. Must be provided in the following format: `Bearer token` (`Bearer` + 1 space + the token)
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful request, the wire transfer's information is returned." %}
```javascript
{
  "transferId": "7ba0f82c-c601-4ec8-e990-08d9098e14a4",
  "amount": 10,
  "actualAmount": 0,
  "closeAccount": false,
  "isDomesticWire": true,
  "recipient": {
    "routingNumber": "267084131",
    "address": {
      "streetAddress1": "assress"
    }
  },
  "intermediary": {
    "address": {
      "city": "Cansas"
    }
  },
  "beneficiary": {
    "accountNumber": "987654321",
    "name": "Test",
    "address": {
      "streetAddress1": "streeraddress"
    }
  },
  "iraDistribution": {
    "reason": "NORMAL",
    "federalTaxType": "Tax",
    "stateTaxType": "Tax",
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
