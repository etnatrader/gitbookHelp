# Get Users' Info

### Overview

This GET endpoint enables you to retrieve information about a particular user by providing their internal identifier in ETNA Trader in the request header.

{% hint style="warning" %}
In order to retrieve information about a particular user, you must use an [authorization token](../authentication/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the internal identifier of the user whose information needs to be retrieved.

### Response

```javascript
{
  "Id": 7472,
  "FirstName": "Jim",
  "Middle": "",
  "LastName": "James",
  "EmailAddress": "robert.zakiev@etnatrader.com",
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

