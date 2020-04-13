---
description: Retrieve a trading account's collective market value of all security types
---

# Get Market Value of all Security Types

### Introduction‌ <a id="introduction"></a>

This GET endpoint enables you to retrieve the collective market value of different security types in a specific trading account.‌

There are five required parameters that must be provided in the request:‌

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to retrieve this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountID** \(path\). This is the internal ID of the trading account whose market value of different security types must be listed.‌

Here's the final template for this API request:

```text
GET apiURL/v1.0/accounts/{accountID}/positions/groups
```

## Response <a id="response"></a>

In response to this API request, you'll receive a JSON file with the collective market value of different security types in the specified trading account.

```javascript
[
  {
    "Name": "Options",
    "MarketValue": -996.5
  },
  {
    "Name": "Equity",
    "MarketValue": 129835.86
  },
  {
    "Name": "Cash",
    "MarketValue": 342377.84999484
  }
]
```

where:

| Parameter | Description |
| :--- | :--- |
| Name | The type of security. |
| MarketValue | The collective market value of all securities of this type in this trading account. |

## Common Mistakes <a id="common-mistakes"></a>

Here are some of the common mistakes that developers make when attempting to fetch the collective market value of different security types in a specific trading account.‌

### Failing to Specify the Et-App-Key Parameter <a id="failing-to-specify-the-et-app-key-parameter"></a>

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```text
{    "error": "Application key is not defined or does not exist"}
```

### Specifying the User ID Instead of the Trading Account ID <a id="specifying-the-user-id-instead-of-the-trading-account-id"></a>

Another common mistake when making this request is specifying the user ID instead of the user's trading account ID. Doing so will result in the 500 status code and the following error message:

```text
{    "message": "An error occurred while processing your request",    "error": "Unexpected server error"}
```

