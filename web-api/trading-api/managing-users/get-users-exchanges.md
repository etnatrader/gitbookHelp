---
description: Retrieve the list of exchanges available to a specific user
---

# Get User's Exchanges

## Overview

This GET endpoint enables you to fetch the list of exchanges available to a specific user.

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/requesting-tokens/). The value of this header must have the following format: `Bearer BQ898r9fefi` \(`Bearer` + 1 space + the token\).
3. **userID** \(path\). This is the internal ID of the user  whose exchanges you'd like to list. If you're sending the request on behalf of the user whose authorization token is used to perform the request, set this parameter to `@me`.
4. **API version** \(path\). Unless necessary, leave it at "1.0".

The user information request must be sent to the following URL:

```text
GET apiURL/v1.0/users/{userID}/exchanges
```

### Response

In response, you'll receive a JSON file containing the list of exchanges available to that user:

```javascript
[
  "NYSE",
  "KNIGHT",
  "NSDQ",
  "Auto",
  "VIRTEX",
  "FXCM",
  "ARCA",
  "BATS",
  "MNGD",
  "EDGX"
]
```

{% hint style="info" %}
If a trader selects **`Auto`** when placing an order, this order will be routed to the most appropriate exchange.
{% endhint %}

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve the list of exchanges available to a specific user. 

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

