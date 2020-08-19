---
description: Verify an order modification before committing changes
---

# Verify Order Replacement

## Overview

This PUT endpoint enables you to verify an order replacement before using it to replace an existing order in ETNA Trader. This might be useful for ensuring that the user has properly constructed an order and prevent any issues related with defective orders.

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **Trading Account ID** \(path\). This is the numeric ID of the trading account on which an existing order replacement must be verified.
5. **orderId** \(path\). This is the id of the order which parameter replacement must be verified. You can retrieve IDs of orders of a particular trading account using this [API request](../get-filtered-orders/).
6. **modifyParams** \(body\). This is a JSON file that contains the parameters that need to be modified in an existing order. 

Here's the final template for this API request:

* For orders that will only be verified by the API but not the execution venue \(quick\):

```text
PUT apiURL/v1.0/accounts/{accountID}/preview/orders/{existingOrderID}
```

* For orders that will be verified by the API and the execution venue too \(slow\):

```text
PUT apiURL/v1.0/accounts/{accountID}/preview/syncorders/{existingOrderID}
```

## Request Body

The body of this request represents the information that must verified before being replaced in an existing order. It must be sent in the JSON format with mandatory parameters about the order.

The first four parameters — **ID**, **Quantity**, **Price**, **ExecutionInstructions**, and **Execution Instructions** — are mandatory, while the remaining parameters should only be provided if necessary. Apart from these four parameters, the rest of the JSON should be constructed identically to the [order placement JSON](../place-order/).

### Order Modification Verification Sample

```javascript
{
  "Id": 76320,
  "Quantity": 100,
  "Price": 240,
  "Comment": "Updating the limit price and target trading session",
  "TimeInforce": "GoodTillCancel",
  "ExtendedHours": "PREREG",
  "ExecutionInstructions" : {"Commission": "0.5"}
}
```

## Response

In response to this request, you'll receive a JSON file confirming \(or rejecting\) that the order replacement has been properly constructed.

```javascript
{
  "IsSuccessful": true,
  "Commission": 1.00000002,
  "Commissions": {
    "Per Trade Commission": 1,
    "Per Contract Commission": 2e-8
  },
  "Cost": 482,
  "NetCost": 483.00000002,
  "TotalCost": 1.00000002,
  "Quotes": [
    {
      "Ask": 266.7,
      "Bid": 266.61,
      "Last": 266.5,
      "Volume": 50,
      "OpenInterest": 0,
      "Symbol": "AAPL",
      "SecurityId": 4,
      "Timestamp": "2019-11-28T01:00:00Z"
    }
  ],
  "MarginChange": 0
}
```

where:

| Parameter | Description |
| :--- | :--- |
| IsSuccessful | This field indicates if the order replacement has been successfully executed. |
| Commission | This is the total commission applicable to the order. |
| Commissions | This is an array that breaks down the applicable commissions. |
| Cost | This is the total cost of the order \(including commission\). |
| NetCost | This is the cost of the order less commission. |
| TotalCost | This is the gross commission applied to the order \(including all other commissions\). |
| Quotes | This is the last batch of quotes for this security \(includes the security's ticker symbol, its internal identifier in ETNA Trader, and the quote's timestamp\). |
| MarginChange | This is the amount by which the trading account margin requirements will be affected once this order is filled. |

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to verify an order replacement.

### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for verifying order replacements, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

### Providing an Incorrect Set of Parameters

Another common mistake made when sending this API request is failing to provide all mandatory parameters. Doing so will result in the 500 status code and the following error message:

```javascript
{
  "message": "An error occurred while processing your request",
  "error": "Unexpected server error"
}
```

The following article covers the syntax for this API request in detail.

