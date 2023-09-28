---
description: Approve an ACH relationship based on micro deposits
---

# Approve an ACH Relationship

This endpoint enables you to approve a new ACH relationship based on micro deposits (as opposed to Plaid-based ACH relationships).&#x20;

When you attempt to create such relationship, you will see two values in your banking account statement (e.g., `0.34` and `0.21`).&#x20;

Provide these two values in this endpoint to confirm the creation of the ACH relationship.

{% hint style="warning" %}
This endpoint cannot be used for approving Plaid-based ACH relationships, as they are automatically approved.
{% endhint %}

{% swagger baseUrl="baseURL" path="/v{version}/accounts/{accountId}/ach-relationships/{id}/approve" method="post" summary="Approve An ACH Relationship" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of the API. By default it's `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="accountId" type="Integer" required="true" %}
ID of the trading account.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" type="String" required="true" %}
The unique key of your app that identifies it when communicating with our service. Contact your administrator to get this key.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
Authorization token. Must be provided in the following format: `Bearer token` (`Bearer` + 1 space + the token)
{% endswagger-parameter %}

{% swagger-parameter in="path" name="id" type="String" required="true" %}
This is the ID of the ACH relationship in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="model" type="String" required="true" %}
JSON object containing two charges from the banking statement.



{&#x20;

"Amount1": 0.32, "Amount2": 0.19&#x20;

}


{% endswagger-parameter %}

{% swagger-response status="200" description="Successful request, the ACH relationship has been approved." %}
```
```
{% endswagger-response %}
{% endswagger %}
