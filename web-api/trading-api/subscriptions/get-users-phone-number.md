# Get User's Phone Number

This endpoint enables you to request a user's phone number by a unique ETNA Trader ID. In response, you'll receive JSON data with the user's phone number.

{% swagger method="get" path="/v{version}/users/{userId}/subscriptions/settings/phonenumber" baseUrl="baseURL" summary="Get A User's Phone Number" %}
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

{% swagger-response status="200: OK" description="Successful request, the phone number and the linking state are returned." %}
```javascript
{
  "PhoneNumber": "+34635952910",
  "PhoneNumberState": "Active"
}
```
{% endswagger-response %}
{% endswagger %}
