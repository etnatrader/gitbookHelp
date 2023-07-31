# Create Default Paperless Settings

This endpoint allows users to create default paperless settings for a specific trading account by the "accountId."&#x20;

Please note that when using this endpoint to create paperless settings, any existing settings for the specified account will be overridden.

{% swagger method="post" path="/v{version}/accounts/{accountId}/paperless/default" baseUrl="baseURL" summary="Create Default Paperless Settings" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="" required="true" %}
The version of API. By default, set it to 

`1.0`

.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="accountId" required="true" type="Integer" %}
Internal ETNA ID of the trading account.
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

{% swagger-response status="200: OK" description="Successful request. Response includes current settings." %}
```javascript
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "AccountNo": "54967",
  "Options": [
    {
      "Description": "Confirmations",
      "IsPaperless": false,
      "CategoryId": "00000000-0000-0000-0000-000000000000"
    },
    {
      "Description": "Statements",
      "IsPaperless": false,
      "CategoryId": "00000000-0000-0000-0000-000000000000"
    },
    {
      "Description": "Tax Documents",
      "IsPaperless": false,
      "CategoryId": "00000000-0000-0000-0000-000000000000"
    },
    {
      "Description": "Prospectus, Annual Reports and Proxies",
      "IsPaperless": false,
      "CategoryId": "00000000-0000-0000-0000-000000000000"
    }
  ]
}
```
{% endswagger-response %}
{% endswagger %}
