# Remove A Mobile UUID From A User

This DELETE endpoint enables you to unsubscribe a user from notifications by providing their `playerId` from OneSignal.

Learn more about subscribing users to notifications:

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

{% swagger method="delete" path="/v{version}/users/{userId}/subscriptions/settings/pushuid" baseUrl="baseURL" summary="Remove A Mobile UUID From A User" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="userID" required="true" type="Integer" %}
Internal ETNA Trader ID of the user.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" type="String" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="uid" required="true" type="String" %}
This is the identifier of the user in OneSignal (`playerId`).
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="Successful request. " %}
```javascript
```
{% endswagger-response %}
{% endswagger %}



