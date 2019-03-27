---
description: Cancel an existing outstanding order
---

# Cancel Order

### Overview

This DELETE endpoint enables you to cancel an outstanding order of the user whose authorization token is provided in the header request. If the user has buy, sell, short-sell, or a buy-to-cover orders pending, you can cancel each one of them by sending this API request.

There are five required parameters that must be provided in the request header:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service.  It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\). 
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../../public-api/authentication/requesting-tokens/).
3. **orderId** \(path\). This is the numeric ID of the order that must be cancelled. 
4. **version** \(path\). Unless necessary, leave it at "1.0"
5. **accountID** \(path\). This is the numeric ID of the trading account on which the order must be canceled.

This API request must be sent to the following URL:

```javascript
apiURL/v1.0/accounts/6303/orders/73552
```

### Response

In response to this API request — if the order was successfully deleted — you'll receive no JSON file. The status code of the request will be 204 \(successful order cancellation\). 

### Common Mistakes

Here are some of the common mistakes that developers make when trying to cancel an outstanding order. 

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Specifying the ID of a Completed Order

Another common mistake when making this request is specifying the order ID of an already filled order. In this case the cancellation will be rejected because only outstanding orders can be cancelled.

In the following article we provide in-depth coverage of the syntax for this API request.

