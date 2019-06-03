---
description: Unbind an existing trading account from an existing user
---

# Remove a Trading Account from a User

## Overview

This DELETE endpoint enables you to unbind a particular trading account from an existing user. Once the account is unbound from an existing user, you can verify that this user no longer has access to this account by leveraging [this API endpoint](../../user-accounts/list-users-accounts/).

{% hint style="warning" %}
In order to unbind a trading account from a user, you must use an [authorization token]() of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request]().
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountID** \(path\). This is the internal identifier of the trading account which is to be unbound from an existing user.
5. **userID** \(query\). This is the internal identifier of the user from whom an existing trading account must be unbound.

Here's the final template for this API request:

```text
DELETE apiURL/v1.0/accounts/{accountID}/users/{userID}
```

## Response

In response to this API request, you'll receive a JSON file with an array of users who have access to this trading account \(after it was unbound from the user specified in the **userID** parameter\). The user specified in the userID parameter must not be in the array, as they have just been removed.

```javascript
[
  {
    "UserModel": {
      "UserId": 7472,
      "FirstName": "Jim",
      "MiddleName": "",
      "LastName": "James",
      "Login": "robert.zakievdev",
      "Email": "robert.zakiev@etnatrader.com",
      "AddedDate": "2019-02-12T16:51:00.1335811Z",
      "Salutation": "NoSalutation",
      "Suffix": "NoSuffix"
    },
    "AccountAccessType": "Full"
  },
  {
    "UserModel": {
      "UserId": 7473,
      "FirstName": "string",
      "MiddleName": "s",
      "LastName": "string",
      "Login": "string",
      "Email": "new@email.com",
      "AddedDate": "2019-03-06T15:12:43.2333427Z",
      "Salutation": "NoSalutation",
      "Suffix": "NoSuffix"
    },
    "AccountAccessType": "Full"
  }
]
```

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to unbind existing trading accounts from existing users.

### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for unbinding trading accounts from existing users, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

So be sure to use the authorization token generated with an administrator's credentials.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

In the following article we provide in-depth coverage of the syntax for this API request.

