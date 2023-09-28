# Get Balance Information For A User

## Overview

This endpoint enables you to retrieve aggregated balance information of group of accounts linked to a particular user.

{% swagger method="get" path="/v{version}/users/{userId}/balance-info" baseUrl="baseURL" summary="Get Balance Information For A User" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter type="Integer" in="path" name="userID" required="true" %}
Internal ETNA Trader ID of the user.
{% endswagger-parameter %}

{% swagger-parameter type="String" in="header" name="Authorization" required="true" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter type="String" in="header" name="Et-App-Key" required="true" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request, JSON data with balance information of the specified trading account is returned." %}
```javascript
```
{% endswagger-response %}
{% endswagger %}

