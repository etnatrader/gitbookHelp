# Validate Order Replacement

### Overview

This PUT endpoint enables you to validate an order replacement before using it to replace an existing order in ETNA Trader. This might be useful for ensuring that the user has properly constructed an order and prevent any issues related with defective orders.

{% hint style="warning" %}
In order to validate an order replacement, you must use an [authorization token](../authentication/requesting-tokens/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **Trading Account ID** \(path\). This is the numeric ID of the trading account on which an existing order replacement must be validated.
5. **orderId** \(path\). This is the id of the order which parameter replacement must be validated. You can retrieve IDs of orders of a particular trading account using this [API request](get-filtered-orders/).
6. **modifyParams** \(body\). This is a JSON file that contains the parameters that need to be modified in an existing order. 

Here's the final template for this API request:

```text
PUT apiURL/v1.0/accounts/{accountID}/preview/orders/{existingOrderID}
```

### Request Body

The body of this request represents the information that must validated before being replaced in an existing order. It must be sent in the JSON format with mandatory parameters about the order.

The first five parameters — **ID**, **Quantity**, **Price**, **ExecutionInstructions**, and **Legs** — are mandatory, while the remaining parameters should only be provided if necessary.

#### Order Modification Validation Sample

```javascript
{
  "Id": 76320,
  "Quantity": 100,
  "Price": 169,
  "ExecutionInstructions": {}
}
```

### Response

In response to this request, you'll receive a JSON file confirming \(or rejecting\) that the order replacement has been properly constructed.

```javascript
{
  "IsSuccessful": true,
  "Commission": 3.75,
  "Commissions": {
    "Per Trade Commission": 3.75
  },
  "Cost": 169000,
  "NetCost": 168996.25,
  "Quotes": [
    {
      "Ask": 184,
      "Bid": 175.76,
      "Last": 175.875,
      "Volume": 1,
      "OpenInterest": 0
    }
  ],
  "MarginChange": 16900
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
| Quotes | This is the last batch of quotes for this security. |
| MarginChange | This is the amount by which the trading account margin requirements will be affected once this order is filled. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to validate an order replacement.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for validating order replacements, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

#### Providing an Incorrect Set of Parameters 

Another common mistake made when sending this API request is failing to provide all mandatory parameters. Doing so will result in the 500 status code and the following error message:

```javascript
{
  "message": "An error occurred while processing your request",
  "error": "Unexpected server error"
}
```

### 

