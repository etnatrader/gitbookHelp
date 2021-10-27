---
description: Validate an existing order by providing its ID
---

# Validate Order by ID

## Overview

This GET endpoint enables to you to validate an existing order by providing its ID as well as the ID of the trading account from which the order was placed.

{% swagger method="get" path="/v{apiVersion}/accounts/{accountID}/verified/orders/{orderID}" baseUrl="baseURL" summary="Returns the validation results for the order." %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
This is the authorization token from the very first token request. The value of this header must have the following format: 

`Bearer BQ898r9fefi`

 (

`Bearer`

 \+ 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" type="String" %}
This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="apiVersion" required="true" type="String" %}
The version of the API. Unless necessary, leave it at 

`1.0`

.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="accountID" type="String" required="true" %}
The ID of the trading account from which the order was placed.
{% endswagger-parameter %}

{% swagger-parameter in="path" required="true" name="orderID" type="String" %}
The ID of the order that is to be validated.
{% endswagger-parameter %}
{% endswagger %}
