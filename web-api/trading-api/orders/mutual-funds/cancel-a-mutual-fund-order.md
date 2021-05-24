---
description: Cancel an outstanding unfulfilled order
---

# Cancel a Mutual Fund Order

### Overview

This DELETE endpoint enables you to cancel an existing, outstanding, and unfulfilled mutual fund order.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/). The value of this header must have the following format: `Bearer BQ898r9fefi` \(`Bearer` + 1 space + the token\).
3. **Trading Account ID** \(path\). This is the internal ID of the trading account on whose behalf a new order must be placed. 
4. **API version** \(path\). Unless necessary, leave it at "1.0".
5. **Order ID** \(path\). This is the internal ID of the order that ought to be cancelled.

Here's the final template for this API request:

```text
DELETE apiURL/v1.0/accounts/{Trading Account ID}/orders/mutual-funds/{Order ID}
```

### Response

In response to this API request, if the order was successfully cancelled, you will receive the 200 status code and no response message.

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to cancel a mutual fund order:

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Providing a Non-Existent Order ID

Another common mistake made when sending this API request is providing the ID of a non-existent order. Doing so will result in the 409 status code.

