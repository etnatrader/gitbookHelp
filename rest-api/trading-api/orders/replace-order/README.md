---
description: Modify an existing order (cancel and replace)
---

# Replace Order

### Overview

This PUT endpoint enables you to replace an existing order in ETNA Trader. The order is sent in the JSON format to our service which in turn replaced the fields in the existing order.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **Trading Account ID** \(path\). This is the numeric ID of the trading account on which an existing order must be modified.
4. **API version** \(path\). Unless necessary, leave it at "1.0".
5. **body** \(body of the request\). This is a JSON file that contains the parameters that must be modified in an existing order. 

Here's the final template for this API request:

```text
PUT apiURL/v1.0/accounts/{accountID}/orders/{existingOrderID}
```

### Request Body

The body of this request represents the information that must be replaced in an existing order. It must be sent in the JSON format with mandatory parameters about the order and also those parameters that need to be modified.

The first four parameters — **ID**, **Quantity**, **Price**, **ExecutionInstructions**, **Legs** — are mandatory, while the remaining parameters should only be provided in case they need to be modified. Apart from these four parameters, the rest of the JSON should be constructed identically to the [order placement JSON](../place-order/).

#### Order Modification Sample

```javascript
{
  "Id": 178941,
  "Quantity": 5,
  "Price": 49,
  "ExecutionInstructions" : {"Commission": "0.5"}
}
```

### Response

In response to this request, you'll receive a JSON file with the updated information about the modified order:

```javascript
{
  "Id": 0,
  "SecurityId": 0,
  "Quantity": 0,
  "Price": 0,
  "StopPrice": 0,
  "ClientId": "string",
  "ParentClientId": "string",
  "OrigClientId": "string",
  "ExecutedQuantity": 0,
  "LastPrice": 0,
  "LastQuantity": 0,
  "LeavesQuantity": 0,
  "AveragePrice": 0,
  "Side": "Buy",
  "Date": "2019-02-25T09:59:39.231Z",
  "TransactionDate": "2019-02-25T09:59:39.231Z",
  "SettDate": "2019-02-25T09:59:39.231Z",
  "Status": "New",
  "ExecutionStatus": "New",
  "Type": "Market",
  "RequestStatus": "RequireValidation",
  "Target": "Ignore",
  "Description": "string",
  "Comment": "string",
  "TimeInForce": "Day",
  "ExecInst": "DoNotIncrease",
  "ExpireDate": "2019-02-25T09:59:39.231Z",
  "CounterPartyOrderId": "string",
  "AccountId": 0,
  "UserId": 0,
  "RequestId": 0,
  "StateId": 0,
  "ParentId": 0,
  "Legs": [
    {}
  ],
  "Exchange": "string",
  "ExecutionVenue": "string",
  "TrailingStopAmountType": "Absolute",
  "TrailingStopAmount": 0,
  "TrailingLimitAmountType": "Absolute",
  "TrailingLimitAmount": 0,
  "CreateDate": "2019-02-25T09:59:39.231Z",
  "InitialType": "Market",
  "ExtendedHours": "string",
  "IsExternal": true,
  "ExecBrocker": "string",
  "ExecutionInstructions": {},
  "TransType": "New",
  "ExecId": "string",
  "Token": "string",
  "ValidationsToBypass": 0,
  "ParentRequestId": 0,
  "SettlementDate": "2019-02-25T09:59:39.231Z",
  "LastMarket": "string"
}
```

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to modify an existing order. 

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Specifying the User ID Instead of the Trading Account ID

Another common mistake when making this request is specifying the user ID instead of the user's trading account ID. Doing so will result in the 500 status code and the following error message:

```javascript
{
    "message": "An error occurred while processing your request",
    "error": "Unexpected server error"
}
```

#### Specifying a Trading Account of a Different User

It's critical to understand that when you use the authorization token of a particular user in this request's header, only this user's trading accounts can be used for modifying existing orders. Modifying an existing order on a trading account of a different user will lead to the 401 error.

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

The following article covers the syntax for this API request in detail.

