# Add Account To User

## Overview

This API endpoint enables you to bind a new or an existing trading account to an existing user.



{% swagger method="put" path="/v{version}/accounts/{accountId}/users/{userId}" baseUrl="baseURL" summary="Add Account To User" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="" required="true" %}
The version of API. By default, set it to 

`1.0`

.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="accountId" required="true" type="integer" %}
This is the internal identifier of the trading account which is to be bound to an existing user.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
This is the authorization token from the token request. The value of this header must have the following format: 

`Bearer BQ898r9fefi`

 (

`Bearer`

 \+ 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="path" required="true" name="userId	" %}
This is the internal identifier of the user to whom an existing trading account must be bound.
{% endswagger-parameter %}

{% swagger-parameter in="query" required="true" name="accessType" %}
This is the access level the user should have to this trading account. Available values: Full, ReadOnly, ClosePositionsOnly, Owner.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request, JSON data is returned, containing updated information about the user and trading accounts." %}
```javascript
{
  "UserModel": {
    "UserId": 0,
    "FirstName": "string",
    "MiddleName": "string",
    "LastName": "string",
    "Login": "string",
    "Email": "string",
    "Role": 0,
    "AddedDate": "2023-07-28T14:00:07.136Z",
    "Salutation": "NoSalutation",
    "Suffix": "NoSuffix"
  },
  "AccountAccessType": "Full"
}
```
{% endswagger-response %}
{% endswagger %}
