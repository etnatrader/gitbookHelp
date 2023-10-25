# Complete Phone Number Binding

The **Complete Phone Number Binding** endpoint is the second step in binding a phone number to a user. To use this endpoint you need a SMS code and a token from the [Broken link](broken-reference "mention") endpoint.

{% swagger method="put" path="/v{version}/users/{userId}/subscriptions/settings/phonenumber/token/{tokenId}" baseUrl="baseURL" summary="Complete Phone Number Binding " %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" type="String" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="userId" type="Integer" required="true" %}
Internal ETNA Trader ID of the user.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="tokenId" type="Integer" required="true" %}
Token received from Bind A Phone Number To a User in m\_Item2 field.
{% endswagger-parameter %}

{% swagger-parameter required="true" in="query" name="tokenValue" type="String" %}
Code recevied via SMS.
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

Upon a successful request, the phone number will be both bound to the user's account and verified.
