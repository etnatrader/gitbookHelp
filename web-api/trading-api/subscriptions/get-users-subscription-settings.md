# Get User's Subscription Settings

This endpoint enables you to retrieve detailed information about a user's subscription settings.

{% swagger method="get" baseUrl="baseURL" path="/v{version}/users/{userId}/subscriptions" summary="Get A User's Subscription Settings" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" type="String" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="userId" type="Integer" required="true" %}
Internal ETNA Trader ID of the user.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="channelType" type="String" %}
You can specify a communication channel: Email, MobileText, MobilePush, WebPopupAlert, Disabled.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request, a collection of the user's subscriptions is returned." %}
```javascript
[
  {
    "Channel": "Email",
    "SubscriptionType": "OrderExecution",
    "State": "Suspended"
  },
  {
    "Channel": "Email",
    "SubscriptionType": "OrderForReview",
    "State": "Active"
  },
  {
    "Channel": "Email",
    "SubscriptionType": "OrderOnReview",
    "State": "Active"
  },
  {
    "Channel": "Email",
    "SubscriptionType": "OrderPlacement",
    "State": "Active"
  },
  {
    "Channel": "Email",
    "SubscriptionType": "OrderReplacement",
    "State": "Active"
  },
  {
    "Channel": "Email",
    "SubscriptionType": "PriceAlert",
    "State": "Active"
  },
  {
    "Channel": "MobileText",
    "SubscriptionType": "OrderExecution",
    "State": "Active"
  },
  {
    "Channel": "MobileText",
    "SubscriptionType": "OrderForReview",
    "State": "Active"
  },
  {
    "Channel": "MobileText",
    "SubscriptionType": "OrderOnReview",
    "State": "Active"
  },
  {
    "Channel": "MobileText",
    "SubscriptionType": "OrderPlacement",
    "State": "Active"
  },
  {
    "Channel": "MobileText",
    "SubscriptionType": "OrderReplacement",
    "State": "Active"
  },
  {
    "Channel": "MobileText",
    "SubscriptionType": "PriceAlert",
    "State": "Active"
  },
  {
    "Channel": "MobilePush",
    "SubscriptionType": "OrderExecution",
    "State": "Active"
  },
  {
    "Channel": "MobilePush",
    "SubscriptionType": "OrderForReview",
    "State": "Active"
  },
  {
    "Channel": "MobilePush",
    "SubscriptionType": "OrderOnReview",
    "State": "Active"
  },
  {
    "Channel": "MobilePush",
    "SubscriptionType": "OrderPlacement",
    "State": "Active"
  },
  {
    "Channel": "MobilePush",
    "SubscriptionType": "OrderReplacement",
    "State": "Active"
  },
  {
    "Channel": "MobilePush",
    "SubscriptionType": "PriceAlert",
    "State": "Active"
  },
  {
    "Channel": "WebPopupAlert",
    "SubscriptionType": "OrderExecution",
    "State": "Active"
  },
  {
    "Channel": "WebPopupAlert",
    "SubscriptionType": "OrderForReview",
    "State": "Suspended"
  },
  {
    "Channel": "WebPopupAlert",
    "SubscriptionType": "OrderOnReview",
    "State": "Active"
  },
  {
    "Channel": "WebPopupAlert",
    "SubscriptionType": "OrderPlacement",
    "State": "Active"
  },
  {
    "Channel": "WebPopupAlert",
    "SubscriptionType": "OrderReplacement",
    "State": "Active"
  },
  {
    "Channel": "WebPopupAlert",
    "SubscriptionType": "PriceAlert",
    "State": "Suspended"
  }
]
```
{% endswagger-response %}
{% endswagger %}

Upon a successful request, JSON data is returned, containing detailed information about the user's subscription settings.
