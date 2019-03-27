---
description: Retrieve information about a particular order
---

# Get Order's Info

## Get Order's Info

#### Overview

This GET endpoint enables you to retrieve information about an outstanding order of the user whose authorization token is provided in the header request. If the user has buy, sell, short-sell, or buy-to-cover orders pending, you can request information on one of those orders by sending this API request.

There are five required parameters that must be provided in the request header:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service.  It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\). 
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../../public-api/authentication/requesting-tokens/).
3. **orderId** \(path\). This is the numeric ID of the order whose information you need to retrieve. 
4. **version** \(path\). Unless necessary, leave it at "1.0"
5. **accountID** \(path\). This is the numeric ID of the trading account on which the order is registered.

This API request must be sent to the following URL:

```javascript
apiURL/v1.0/accounts/6303/orders/73552
```

#### Response

In response to this API request, you'll receive a JSON file with comprehensive information about the order:

```javascript
{
    "Id": 73552,
    "SecurityId": 4,
    "Quantity": 150,
    "Price": 0,
    "StopPrice": 0,
    "ClientId": "1045239786",
    "ExecutedQuantity": 150,
    "LastPrice": 156.57,
    "LastQuantity": 150,
    "LeavesQuantity": 0,
    "AveragePrice": 156.57,
    "Side": "Buy",
    "Date": "2019-01-22T13:00:26.575811Z",
    "TransactionDate": "2019-01-22T14:30:03.7168916Z",
    "SettDate": "0001-01-01T00:00:00Z",
    "Status": "Filled",
    "ExecutionStatus": "Filled",
    "Type": "Market",
    "RequestStatus": "Complete",
    "Target": "Modify",
    "TimeInForce": "Day",
    "ExecInst": "AllOrNone",
    "ExpireDate": "2019-01-22T21:00:00Z",
    "CounterPartyOrderId": "1045239786",
    "AccountId": 6303,
    "UserId": 7125,
    "RequestId": 96193,
    "StateId": 168831,
    "ParentId": -1,
    "Legs": [],
    "Exchange": "Auto",
    "ExecutionVenue": "Etna Emulator",
    "TrailingStopAmountType": "Absolute",
    "TrailingStopAmount": 0,
    "TrailingLimitAmountType": "Absolute",
    "TrailingLimitAmount": 0,
    "CreateDate": "2019-01-21T15:07:45.8158882Z",
    "InitialType": "Market",
    "IsExternal": false,
    "ExecBrocker": "Auto",
    "ExecutionInstructions": {},
    "TransType": "New",
    "ExecId": "173657808",
    "ValidationsToBypass": 0,
    "ParentRequestId": 0,
    "SettlementDate": "0001-01-01T00:00:00Z"
}
```

#### Common Mistakes

Here are some of the common mistakes that developers make when trying to retrieve information about an outstanding order.

**Failing to Specify the Et-App-Key Parameter**

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

**Specifying a Trading Account of a Different User**

It's critical to understand that when you use the authorization token of a particular user in this request's header, only this user's orders can be examined. Retrieving information about orders of a different user will lead to the 401 error.

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

In the following article we provide in-depth coverage of the syntax for this API request.

