---
description: List all users who use a particular trading account.
---

# List Account Users

### Overview

This GET endpoint enables you to retrieve information about all users who user a particular trading account. This account's ID is provided in the request's path and, in response, ETNA Trader will return an array of users who use this trading account.

{% hint style="warning" %}
In order to list users who user a particular trading account, you must use an [authorization token]() of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request]().
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountID** \(path\). This is the internal identifier of the trading account whose users need to be retrieved.

Here's the final template for this API request:

```text
GET apiURL/v1.0/accounts/{accountID}/users
```

### Response

In response to this API request, you'll receive a JSON file that contains the list of users who use the trading account specified in the request's path:

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
  }
]
```

where:

| Parameter | Description |
| :--- | :--- |
| UserId | This is the internal identifier of the user who uses this trading account. |
| FirstName | This is the first name of the user in ETNA Trader. |
| MiddleName | This is the first name of the user in ETNA Trader. |
| LastName | This is the last name of the user in ETNA Trader. |
| Login | This is the user's login in ETNA Trader. |
| Email | This is the user's email address. |
| AddedDate | This is the date on which the user was added to ETNA Trader. |
| Salutation | This is a special salutation used to address this user in emails. |
| Suffix | This is the suffix used when addressing the user \(Jr, Sr, I, II, III, etc.\). |
| AccountAccessType | This is the account access type which indicates the user's access level to this trading account. Possible values: Full, ReadOnly, ClosePositionsOnly. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve the list of users who use a particular trading account.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for a trading account's users, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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



