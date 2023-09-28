# Get A Request's Investigation Details

{% swagger method="get" path="/v{version}/accounts/{clearingAccount}/investigations/{investigationId}/details" baseUrl="baseURL" summary="Get A Request's Investigation Details" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="clearingAccount" required="true" type="String" %}
ID of the trading account whose investigations must be returned.\

{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" type="String" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="investigationId" required="true" type="String" %}
ID of the investigation whose details must be returned.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request, JSON data containing details about the investigation is returned." %}
```javascript
```
{% endswagger-response %}
{% endswagger %}
