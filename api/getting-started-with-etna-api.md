---
description: API Description sample
---

# Getting Started With ETNA API

### Creating a New User

To create a new user for the ETNA Trader API, use the following method:

{% api-method method="post" host="https://api.etnatrader.com/v0/{route}/" path="registration" %}
{% api-method-summary %}
Create a New User
{% endapi-method-summary %}

{% api-method-description %}
This API method creates a new user within your company.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
application/json
{% endapi-method-parameter %}

{% api-method-parameter name="x-api-routing" type="string" required=true %}
Your environment route. Example: demo
{% endapi-method-parameter %}

{% api-method-parameter name="x-api-key" type="string" required=true %}
Your API key. Example: yiBCDJFVpimYYtmI0dYp9uUsc9YWeYc233VW9v2j
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="New user\'s info" type="object" required=true %}
This is the information of the new user in the JSON format. The example is provided in the table below.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
"ResponseCode": 0, //response code (Could be 0,1,2,4,7)
"Result": {
    "ErrorAttributes": null, //indicates that there are no errors
    "ErrorKey": null, //indicates that there are no errors
    "Login": "your_login", //the login of the newly created user
    "Password": "your_password", //the password of the newly created user
    "UserId": your_userID //the ID of the newly created user
    },
"Ticket": ""
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Request Body

The body of the request must be provided in the JSON format. Example:

{% code-tabs %}
{% code-tabs-item title="Request body JSON sample" %}
```javascript
{
"version":"3.00",
"device":"iOS",
"registrationRequest":
        {
        "AnswerSecretQuestion":"your_answer",
        "Login":"your_login",
        "SecretQuestion":2, //look at the table below for more information
        "FirstName":"your_FirstName",
        "LastName":"your_LastName",
        "Password":"your_password",
        "Email":"Your email",
        
        "PrimaryPhoneCountry":"Primary_phone_country_code",
        "PrimaryPhoneCode":"Primary_phone_country_region_code",
        "PrimaryPhone":"Primary_phone",
        
        "StreetAddress1":"Main_street_address",
        "StreetAddress2":"Secondary_street_address",
        "City":"City",
        "State":"state_id_when_country_is_US",
        
        "PostalCode":"Postal_or_zip_code.",
        "CountryId":"Country_ID",
        
        "SendInvitationEmail":true/false
 }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### Secret Question Types

The secret question is used for password reset. When a user forgets their password, they may answer this question to successfully reset their password. There are 7 different secret questions a user can choose and also the **Unknown** option that allows you to skip this step.

| ID | Name | Description |
| :--- | :--- | :--- |
| -1 | Unknown | No question. |
| 2 | MotherNameQuestion | The user's mother's name. |
| 3 | ChildhoodNicknameQuestion | The user's childhood nickname. |
| 4 | SpouseMeetingCityQuestion | The city where the user met their spouse. |
| 5 | ChildhoodFriendNameQuestion | The user's childhood friend's name. |
| 6 | HomeStreetThirdGradeQuestion | The street on which the user lived in the third grade. |
| 7 | EldestSiblingBirthdayQuestion | The date of the user's eldest sibling birthday. |

