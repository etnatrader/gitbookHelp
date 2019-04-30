---
description: Retrieve information about a particular user
---

# Get Users' Info

### Overview

This GET endpoint enables you to retrieve information about a particular user by providing their internal identifier in ETNA Trader in the request path.

{% hint style="warning" %}
In order to retrieve information about a particular user, you must use an [authorization token](../../authentication/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the internal identifier of the user whose information needs to be retrieved. You can retrieve IDs of all users with this [API request](../list-all-users/). 

Here's the final template for this API request:

```text
GET apiURL/v1.0/users/{userID}
```

### Response

In response to this API request, you'll receive a JSON file with detailed information about the user.

```javascript
{
  "Id": 7472,
  "FirstName": "Jim",
  "Middle": "",
  "LastName": "James",
  "EmailAddress": "jim.james@etnatrader.com",
  "Login": "robert.zakievdev",
  "Salutation": "NoSalutation",
  "Suffix": "NoSuffix",
  "AddedDate": "2019-02-12T16:51:00.1335811Z",
  "Enabled": true,
  "Deleted": false,
  "TimeZoneInfoId": "Eastern Standard Time",
  "EntitlementsPhoneNumber": ""
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal identifier of the user in ETNA Trader. |
| FirstName | This is the first name of the user in ETNA Trader. |
| Middle | This is the middle name of the user in ETNA Trader. |
| LastName | This is the last name of the user in ETNA Trader. |
| EmailAddress | This is the email address of the user. |
| Login | This is the user's login. |
| Salutation | This is a special salutation used to address this user in emails. |
| Suffix | This is the suffix used when addressing the user \(Jr, Sr, I, II, III, etc.\). |
| AddedDate | This is the date on which this user account was added to ETNA Trader. |
| Enabled | This field indicates if the user is active and can make trades in ETNA Trader. |
| Deleted | This field indicates if the user has been deleted. |
| TimeZoneInfoId | This field indicates the time zone in which the user lives. |
| EntitlementsPhoneNumber | This the user's phone number. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve information about a particular user.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for retrieving users' information, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

#### Specifying the User's Login Instead of the Internal ID

Another common mistake developers make when making this API request is specifying the login of the user instead of their internal ID. Doing so will lead to the 400 status code, and you will receive the following error message:

```javascript
{
  "Message": "The request is invalid."
}
```

In the following article we provide in-depth coverage of the syntax for this API request.

