# Accept A New Appeal

{% swagger method="post" path="/v{version}/accounts/{clearingAccount}/investigations/{investigationId}/accept" baseUrl="baseURL" summary="Accept A New Appeal" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to `1.0`.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="clearingAccount" required="true" type="String" %}
ID of the trading account.\

{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
This is the authorization token from the token request. The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" type="String" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="investigationId" required="true" type="String" %}
ID of the investigation whose appeal is being accepted.
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" type="String" name="resource" %}
JSON data required for the appeal acceptance.
{% endswagger-parameter %}

{% swagger-response status="204: No Content" description="Successful request, the acceptance request was successfully sent." %}
```javascript
```
{% endswagger-response %}
{% endswagger %}

### Resource Model

```
{
  "Comment": "string",
  "Vendors": [
    "string"
  ],
  "Documentation": [
    "string"
  ],
  "SnapIds": [
    "string"
  ]
}
```
