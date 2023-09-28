# Get Account Info

## Overview

The endpoint allows you to retrieve detailed information about an account. The response will include various account-related data, such as he unique identifier of the account, the timestamp indicating when the account was created, the account provider and etc.

{% swagger method="get" path="/v{version}/accounts/{accountId}/details" baseUrl="baseURL" summary="Get Account Info" %}
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
{
  "Id": "cd61a3a4-5380-42ba-330b-08db6b48ce67",
  "CreatedAt": "2023-06-15T09:04:43.3512813Z",
  "AccountProvider": "PaperTrading",
  "FormType": "Direct",
  "User": "54967",
  "ClearingAccountNumber": "83267",
  "IsOpened": true,
  "FormDataReference": "{\"marginType\":\"DayTrader\",\"cash\":\"100000\"}",
  "CustomerType": "Individual"
}
```
{% endswagger-response %}
{% endswagger %}
