---
description: Updated a user's default trading settings
---

# Modify User's Settings

## Overview

This PUT endpoint enables you to request a user's default settings by providing their unique identifier in the header. In response, you'll receive a JSON file with the user's information.

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/requesting-tokens/). The value of this header must have the following format: `Bearer BQ898r9fefi` \(`Bearer` + 1 space + the token\).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the internal ID of the user  whose settings you'd like to retrieve. If you're sending the request on behalf of the user whose authorization token is used to perform the request, set this parameter to `@me`.
5. **tradingSettings** \(body\). This is a JSON object containing the updated trading settings for this user.

### Body Syntax

The body of the request represents a JSON object containing the new trading settings for this user.

```javascript
{
  "Instruments": {
    "Stocks": {
      "OrderType": "Market",
      "Quantity": 100,
      "DurationType": "Day",
      "ExchangeType": "NSDQ",
      "AON": false
    },
    "Options": {
      "OrderType": "Market",
      "Quantity": 50,
      "DurationType": "Day",
      "ExchangeType": "Auto",
      "AON": false,
      "Spreads": 1
    },
    "Forex": {
      "OrderType": "Market",
      "Quantity": 1,
      "DurationType": "Day",
      "ExchangeType": "Auto",
      "AON": false
    }
  },
  "QuantityStepIncrementMultiplier": 1,
  "PriceStepIncrementMultiplier": 1,
  "SkipVerifyOrder": "Show",
  "SkipVerifyCancelOrder": "Show",
  "SkipVerifyClosingPosition": "Show",
  "SkipVerifyOrderReplace": "Show",
  "SkipPlaceOrderStatus": "Show",
  "SkipCancelOrderStatus": "Show",
  "SkipClosingPositionStatus": "Show",
  "SkipOrderReplaceStatus": "Show",
  "MaxStocksQuantity": 10000000,
  "MaxOptionsQuantity": 99
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Instruments | An array of updated settings for each security type. |
| OrderType | The default order type that is set whenever a security of the specified type is traded. |
| Quantity | The default number of securities of an order for the specified security type. |
| DurationType | The default duration of an order for the specified security type. |
| ExchangeType | The default execution venue for the specified security type. |
| AON | Indicates whether orders should be All-Or-None by default. |
| QuantityStepIncrementMultiplier | The step by which the number of securities must be increased when placing an order. Applicable only if the UI features up and down arrows via which the quantity can either be increased or decreased. |
| PriceStepIncrementMultiplier | The step by which the limit or stop price must be increased when placing an order. Applicable only if the UI features up and down arrows via which the price can either be increased or decreased. |
| SkipVerifyOrder | Indicates whether the order verification view should be displayed when placing an order. Possible values: `Show`, `DoNotShow`, `ShowIfAnError`. |
| SkipVerifyCancelOrder | Indicates whether the order verification view should be displayed when cancelling an order. Possible values: `Show`, `DoNotShow`, `ShowIfAnError`. |
| SkipVerifyClosingPosition | Indicates whether the order verification view should be displayed when closing an existing position. Possible values: `Show`, `DoNotShow`, `ShowIfAnError`. |
| SkipVerifyOrderReplace | Indicates whether the order verification view should be displayed when replacing an order. Possible values: `Show`, `DoNotShow`, `ShowIfAnError`. |
| SkipPlaceOrderStatus | Indicates whether the order status view should be displayed after an order has been placed. Possible values: `Show`, `DoNotShow`, `ShowIfAnError`. |
| SkipCancelOrderStatus | Indicates whether the order status view should be displayed after an order has been cancelled. Possible values: `Show`, `DoNotShow`, `ShowIfAnError`. |
| SkipClosingPositionStatus | Indicates whether the order status view should be displayed after a positions has been closed. Possible values: `Show`, `DoNotShow`, `ShowIfAnError`. |
| SkipOrderReplaceStatus | Indicates whether the order status view should be displayed after an order has been replaced. Possible values: `Show`, `DoNotShow`, `ShowIfAnError`. |
| MaxStocksQuantity | The maximum number of securities that can be traded in a single stock order. |
| MaxOptionsQuantity | The maximum number of securities that can be traded in a single option order. |

The following is the final template for this request:

```text
PUT apiURL/v1.0/users/{userID}/settings/trading
```

## Response

In response, you'll receive a JSON file containing the default trading settings of this user:

```javascript
{
  "Instruments": {
    "Stocks": {
      "OrderType": "Market",
      "Quantity": 100,
      "DurationType": "Day",
      "ExchangeType": "NSDQ",
      "AON": false
    },
    "Options": {
      "OrderType": "Market",
      "Quantity": 50,
      "DurationType": "Day",
      "ExchangeType": "Auto",
      "AON": false,
      "Spreads": 1
    },
    "Forex": {
      "OrderType": "Market",
      "Quantity": 1,
      "DurationType": "Day",
      "ExchangeType": "Auto",
      "AON": false
    }
  },
  "QuantityStepIncrementMultiplier": 1,
  "PriceStepIncrementMultiplier": 1,
  "SkipVerifyOrder": "Show",
  "SkipVerifyCancelOrder": "Show",
  "SkipVerifyClosingPosition": "Show",
  "SkipVerifyOrderReplace": "Show",
  "SkipPlaceOrderStatus": "Show",
  "SkipCancelOrderStatus": "Show",
  "SkipClosingPositionStatus": "Show",
  "SkipOrderReplaceStatus": "Show",
  "MaxStocksQuantity": 10000000,
  "MaxOptionsQuantity": 99
}
```

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to update a user's trading settings:

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

