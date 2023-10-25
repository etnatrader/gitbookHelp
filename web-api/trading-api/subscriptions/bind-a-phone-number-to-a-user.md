# Bind A Phone Number To a User

Assigning a phone number to a user is a two-step process.&#x20;

First, you should add a phone number to a user via the **Bind A Phone Number To a User** endpoint.&#x20;

Next, you should verify the phone number using a token and a code from SMS via the [Broken link](broken-reference "mention") endpoint.

{% swagger method="put" path="/v{version}/users/{userId}/subscriptions/settings/phonenumber" baseUrl="baseURL" summary="Bind A Phone Number To a User" %}
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

{% swagger-parameter required="true" in="query" name="phoneNumber" type="String" %}
The phone number should be in the full format, including the country code, like this: "+13108904569".
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request, the phone number, the linking state, and a generated token identifier are returned." %}
```javascript
{
  "m_Item1": {
    "PhoneNumber": "+34635952910",
    "PhoneNumberState": "NotVerified"
  },
  "m_Item2": 1925 // token
}
```
{% endswagger-response %}
{% endswagger %}

Upon a successful request, you will receive a **token**, and an **SMS code** will be sent to the specified phone number.&#x20;

Use that token and SMS code in the [Broken link](broken-reference "mention") endpoint.
