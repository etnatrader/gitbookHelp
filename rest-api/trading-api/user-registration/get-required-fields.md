---
description: Get a set of parameters that must be specified when creating users
---

# Get Required Fields

### Introduction

This GET endpoint enables you to retrieve the list of required fields for registration of users. This might be useful for determining the required text fields and drop-down menus when designing a custom UI for user registration.

There are three required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. You can retrieve this key in the **BO Companies** widget on the WebApi tab of the company modification window.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "v1.0".

The request ought to be sent to the following URL:

```text
GET apiURL/v1.0/registration/schema
```

### Response

In response to this API request, you will receive a collection of required parameters split into different categories. Each parameter will have a corresponding `Required` parameter, indicating if it must be provided during registration. 

```javascript
[
  {
    "UnitName": "Credentials",
    "Fields": [
      {
        "FieldName": "Login",
        "Required": true
      },
      {
        "FieldName": "Email",
        "Required": true
      },
      {
        "FieldName": "Password",
        "Required": true
      }
    ]
  },
  {
    "UnitName": "Name",
    "Fields": [
      {
        "FieldName": "FirstName",
        "Required": true
      },
      {
        "FieldName": "LastName",
        "Required": true
      },
      {
        "FieldName": "MiddleName",
        "Required": false
      },
      {
        "FieldName": "Suffix",
        "Required": false,
        "Options": [
          "NoSuffix",
          "Jr",
          "Sr",
          "Second",
          "Third",
          "Fourth"
        ]
      }
    ]
  }
]
```

### Common Mistakes

Here are some of the common mistakes that developers make when requesting required registration parameters.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

