# Get All Accounts Of A User

## Overview

This endpoint enables you to list all trading accounts associated with the provided user id.

{% swagger method="get" path="/v{version}/users/{userId}/accounts" baseUrl="baseURL" summary="Get All Accounts Of A User" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="userID" required="true" %}
Internal ETNA Trader ID of the user.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request." %}
```javascript
[
  {
    "Id": 83267,
    "ClearingAccount": "83267",
    "AccessType": "Owner",
    "MarginType": "Margin",
    "OwnerType": "IndividualCustomer",
    "Enabled": true,
    "ClearingFirm": "PaperTrading",
    "IsAverageAccount": false,
    "Owners": [
      {
        "UserId": 54967,
        "FirstName": "Daniel",
        "MiddleName": "",
        "LastName": "Safonov",
        "Login": "danielSafonyan",
        "Email": "daniil.safonov@etnatrader.com",
        "Role": 0,
        "AddedDate": "2023-06-15T08:17:35.2984132Z",
        "Salutation": "NoSalutation",
        "Suffix": "NoSuffix"
      }
    ]
  }
]
```
{% endswagger-response %}
{% endswagger %}
