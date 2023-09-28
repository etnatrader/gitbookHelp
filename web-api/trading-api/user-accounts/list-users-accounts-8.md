# Update Alias Account For Current User

## Overview

This endpoint enables users to add or update an alias for a trading account.&#x20;

An alias serves as a nickname or custom label for the account, providing an alternative name for easier identification and navigation.&#x20;

For instance, if a client shares an account with their spouse, they can add an alias like "Family Account" to refer to it instead of using the account number.

{% swagger method="put" path="/v{version}/accounts/{accountId}/alias/{alias}" baseUrl="baseURL" summary="Update Alias Account For Current User" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="accountId" required="true" type="integer" %}
The internal ID of the trading account to which the alias will be assigned.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="path" required="true" name="alias" %}
The custom name (alias) that the user wants to assign to the trading account.\

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request, the alias is assigned to the specified account." %}

{% endswagger-response %}
{% endswagger %}
