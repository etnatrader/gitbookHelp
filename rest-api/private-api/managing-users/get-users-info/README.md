---
description: Get a user's information by their ETNA Trader identifier
---

# Get User's Info

### Overview

This endpoint enables you to request a user's information by supplying their unique ETNA Trader identifier in the header. In response, you'll receive a JSON file with the user's information.

{% hint style="warning" %}
In order to request information about a particular user, you must use an [authorization token](../../../public-api/authentication/requesting-tokens/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are three required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../../public-api/authentication/requesting-tokens/).
3. **Internal user ID** \(path\). This is the numeric ID of the user  whose information you'd like to receive. 
4. **API version** \(path\). Unless necessary, leave it at "1.0"

The user information request must be sent to the following URL:

```text
apiURL/v1.0/users/644(userID)/info
```

### Response

As a response, you'll receive a JSON file with the information about this user:

```javascript
{
    "UserId": 644, //this is the ID from the path
    "FirstName": "Robert",
    "MiddleName": "",
    "LastName": "Zakiev",
    "Login": "robert.zak",
    "Email": "someEmail@etnatrader.com",
    "AddedDate": "2019-01-14T12:27:37.6205663Z",
    "Salutation": "NoSalutation",
    "Suffix": "NoSuffix"
}
```

### Common Mistakes

Here are some of the common mistakes that developers make when requesting a token:

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for receiving information about a particular user, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

So be sure to use the authorization token generated with an administrator's credentials.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Specifying the Regular User ID Instead of the Internal One

Another common mistake when making this request is specifying the regular user ID instead of the internal ETNA Trader ID. Doing so will result in the 400 status code and the following error message:

```javascript
{
    "Message": "The request is invalid."
}
```

