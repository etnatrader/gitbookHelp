# Set a New Pin Code

### Introduction

This endpoint enables users to set a new pin code if the company's security policy requires it.

{% swagger method="get" path="/v{apiVersion}/users/pincode/change" baseUrl="baseURL" summary="Sets a user's pin code" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of API. By default, set it to 

`1.0`

.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
This is the authorization token from the very first token request. The value of this header must have the following format: 

`Bearer BQ898r9fefi`

 (

`Bearer`

 \+ 1 space + the token).
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" type="String" required="true" %}
This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the 

**BO Companies**

 widget. When editing the company's settings, navigate to the 

**WebApi**

 tab and look for the required key (it could be a key for the web terminal, the mobile app, or a custom key).
{% endswagger-parameter %}

{% swagger-parameter in="body" required="true" name="Token" type="String" %}
The 

`ConfirmationToken`

 parameter from the 

[authentication endpoint](../../authentication/)

.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="Pin" type="Integer" required="true" %}
The new pin code.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="ImageName" type="String" required="true" %}
The name of the security image from 

[this endpoint](retrieve-security-images.md)

.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="PersonalPhrase" type="String" required="true" %}
Some text that will be displayed to the user when they're entering their pin code.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful request, the pin code was successfully updated." %}
```javascript
{
  "Errors": [
    "string"
  ],
  "ErrorsCode": [
    "string"
  ],
  "StatusCode": "Continue",
  "IsSucceed": true
}
```
{% endswagger-response %}
{% endswagger %}
