# Unbind The Current Phone Number From A User

This endpoint enables you to unbind a user's phone number.&#x20;

{% swagger method="delete" path="/v{version}/users/{userId}/subscriptions/settings/phonenumber" baseUrl="baseURL" summary="Unbind The Current Phone Number From A User" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter type="Integer" in="path" name="userID" required="true" %}
Internal ETNA Trader ID of the user.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" type="String" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="Successful request, the phone number was successfully unbound." %}
```javascript
```
{% endswagger-response %}
{% endswagger %}
