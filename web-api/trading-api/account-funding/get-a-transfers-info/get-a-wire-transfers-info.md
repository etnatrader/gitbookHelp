---
description: Retrieve information about a wire transfer
---

# Get a Wire Transfer's Info

### Overview

This GET endpoint enables you to retrieve detailed information about a wire transfer.

{% api-method method="get" host="baseURL" path="/v{apiVersion}/transfers/wire/{transferID}" %}
{% api-method-summary %}
Get a Wire Transfer's Info
{% endapi-method-summary %}

{% api-method-description %}
Returns the detailed information about the target transfer.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="apiVersion" required=true type="number" %}
The version of the API. By default it's `1.0`.
{% endapi-method-parameter %}

{% api-method-parameter name="transferId" required=true type="integer" %}
The ID of the target wire transfer.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Et-App-Key" type="string" required=true %}
The unique key of your app that identifies it when communicating with our service. Contact your administrator to get this key.
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
Authorization token. Must be provided in the following format: `Bearer token` \(`Bearer` + 1 space + the token\)
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful request, the wire transfer's information is returned.
{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}

{% api-method-response-example httpCode=409 %}
{% api-method-response-example-description %}
Unable to find the transfer by its ID.
{% endapi-method-response-example-description %}

```
No response
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

