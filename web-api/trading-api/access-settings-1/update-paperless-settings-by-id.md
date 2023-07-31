# Update Paperless Settings By Id

This endpoint enables users to update paperless settings, specifying their preferences for electronic document notifications.

{% swagger method="put" path="/v{version}/accounts/paperless" baseUrl="baseURL" summary="Update Paperless Settings By Id" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to 

`1.0`

.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" required="true" type="String" %}
This is the authorization token from the token request. The value of this header must have the following format: 

`Bearer BQ898r9fefi`

 (

`Bearer`

 \+ 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" required="true" type="String" %}
This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="deliveryInformationOnUpdate" required="true" type="Object" %}
Paperless settings to be updated, find the description below.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request, a list of paperless settings is returned." %}
```javascript
```
{% endswagger-response %}
{% endswagger %}

### **deliveryInformationOnUpdate**

```
{
  "Id": "00000000-0000-0000-0000-000000000000",
  "Email": "string", // primary email
  "AccountNo": "string", // account to be updated
  "SupplementEmail": "string", // secondary email
  "Options": [ // list of paperless settings, find available options below
    {
      "Description": "string",
      "IsPaperless": true,
      "CategoryId": "00000000-0000-0000-0000-000000000000"
    }
  ]
}
```

### Paperless Options

```
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
```
