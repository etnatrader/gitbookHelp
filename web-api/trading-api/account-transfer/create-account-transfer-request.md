---
description: This endpoint enables you to create an account transfer request.
---

# Create Account Transfer Request

{% swagger method="post" path="/v{version}/account-transfer-requests/{accountId}" baseUrl="baseURL" summary="Create Account Transfer Request" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="accountId" required="true" type="Integer" %}
Internal ETNA Trader ID of the trading account that needs to be transferred.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" type="String" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request, the account transfer request was successfully created." %}
```javascript
```
{% endswagger-response %}
{% endswagger %}
