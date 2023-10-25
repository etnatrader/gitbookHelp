# Modify User's Subscription Settings

This endpoint enables you to modify user's subscription settings by providing an updated model in the request body.&#x20;

{% swagger method="put" path="/v{version}/users/{userId}" baseUrl="baseURL" summary="Modify Settings Of A Subscription" %}
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

{% swagger-parameter in="body" name="model" type="String" required="true" %}
{&#x20;

"Channel": "Email", "SubscriptionType": "Activation", "State": "NotLinked", "AccountId": 0 } \
\
You can obtain a list of subscription settings from [Get User's Subscription Settings](broken-reference) endpoint.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request." %}
```javascript
{
  "Id": 54967,
  "FirstName": "Daniil",
  "Middle": "",
  "LastName": "Safonov",
  "EmailAddress": "daniil.safonov@etnatrader.com",
  "Address": {
    "StreetAddress1": "",
    "StreetAddress2": "",
    "City": "",
    "State": 0,
    "PostalCode": "",
    "CountryId": 188
  },
  "Login": "danielSafonyan",
  "Salutation": "NoSalutation",
  "Suffix": "NoSuffix",
  "AddedDate": "2023-06-15T08:17:35.2984132Z",
  "Enabled": true,
  "Deleted": false,
  "TimeZoneInfoId": "Eastern Standard Time",
  "EntitlementsPhoneNumber": ""
}
```
{% endswagger-response %}
{% endswagger %}

#### Body Syntax

| Channel          | Communication channel through which the notification must be sent. Possible values: `Email`, `MobileText`, `MobilePush`, `WebPopupAlert`,`Disabled`.                                                                    |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SubscriptionType | <p>The event of which traders are notified.</p><p>Possible values: </p><ul><li>OrderExecution</li><li>OrderForReview</li><li>OrderOnReview</li><li>OrderPlacement</li><li>OrderReplacement</li><li>PriceAlert</li></ul> |
| State            | <p>The required state of the subscription.</p><p>Possible values: </p><ul><li>NotLinked = 0</li><li>Active = 1</li><li>Suspended = 2</li><li>NotVerified = 3</li></ul>                                                  |

In response, you'll receive a JSON file with the information on the updated subscription.

&#x20;

