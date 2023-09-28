---
description: This endpoint enables you to submit an account transfer request.
---

# Submit Account Transfer Request

{% swagger method="put" path="/v{version}/account-transfer-requests/{requestId}/submit" baseUrl="baseURL" summary="Submit Account Transfer Request" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="requestId" required="true" type="Integer" %}
ID of the request that needs to be submitted.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" type="String" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="model" required="true" type="String" %}
JSON data containing information about the submitted request.



{&#x20;

"FormDataReference": "string",&#x20;

"SyncProcessing": true&#x20;

}
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="Successful request, the account transfer request was successfully submitted." %}
```javascript
```
{% endswagger-response %}
{% endswagger %}
