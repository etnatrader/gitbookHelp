---
description: Cancel an existing outstanding order
---

# Cancel an Order

## Overview

This DELETE endpoint enables you to cancel an outstanding order of the user whose authorization token is provided in the header request. If the user has pending buy, sell, short-sell, or buy-to-cover orders, you can cancel each one of them by sending this API request.

There are five required parameters that must be provided in the request header:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/). The value of this header must have the following format: `Bearer BQ898r9fefi` \(`Bearer` + 1 space + the token\).
3. **orderId** \(path\). This is the numeric ID of the order that must be cancelled. 
4. **version** \(path\). Unless necessary, leave it at "1.0"
5. **accountID** \(path\). This is the numeric ID of the trading account on which the order must be canceled.

This API request must be sent to the following URL:

* For orders that will only be verified by the API but not the execution venue \(quick\):

```text
DELETE apiURL/v1.0/accounts/6303/orders/73552
```

* For orders that will be verified by the API and the execution venue too \(slow\):

```text
DELETE apiURL/v1.0/accounts/6303/syncorders/73552
```

## Response

In response to this API request — if the order was successfully deleted — you'll receive no JSON file. The status code of the request will be 204 \(successful order cancellation\).

## Common Mistakes

Here are some of the common mistakes that developers make when trying to cancel an outstanding order.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

### Specifying the ID of a Completed Order

Another common mistake when making this request is specifying the order ID of an already filled order. In this case the cancellation will be rejected because only outstanding orders can be cancelled.

In the following article we provide in-depth coverage of the syntax for this API request.

