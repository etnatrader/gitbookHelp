# Get All Users Of An Account

## Overview

This API endpoint enables you to retrieve the list of users who have access to a specific trading account.

{% swagger method="get" path="/v{version}/accounts/{accountId}/users" baseUrl="baseURL" summary="Get Account Users" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="accountId" required="true" type="integer" %}
Internal ETNA Trader ID of the trading account.
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
    "UserModel": {
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
    },
    "AccountAccessType": "Owner"
  }
]
```
{% endswagger-response %}
{% endswagger %}
