# Get Filtered Orders

### Overview

This GET endpoint enables to you list all outstanding and executed orders of the user whose authorization token was used in the request header. Optionally, you can filter the list by a set of criteria provided in the request's body.

{% hint style="warning" %}
In order to list orders of a particular user, you must use an [authorization token](../../authentication/requesting-tokens/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **Trading Account ID** \(path\). This is the numeric ID of the trading account whose orders must be retrieved. 
4. **API version** \(path\). Unless necessary, leave it at "1.0".
5. **pageNumber** \(query\). Because there can be dozens of outstanding orders, we split them into pages which you can individually retrieve by specifying this parameter.
6. **pageSize** \(query\). This parameter indicates the number of orders from a particular page that must be returned in the response.

Here's the final template for this API request:

```text
apiURL/v1.0/accounts/{accountNumber}/orders?pageNumber=0&pageSize=2
```

### Response

In response to this API request, you'll receive the following JSON file that lists the specified number of orders 

```javascript
{
    "Result": [
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
        },
        {
            "Id": 75225,
            "SecurityId": 2829,
            "Quantity": 100,
            "Price": 0,
            "StopPrice": 0,
            "ClientId": "931672854",
            "ExecutedQuantity": 0,
            "LastPrice": 0,
            "LastQuantity": 0,
            "LeavesQuantity": 0,
            "AveragePrice": 0,
            "Side": "Buy",
            "Date": "2019-01-30T15:09:23.7597893Z",
            "TransactionDate": "2019-01-30T21:01:00.0397665Z",
            "SettDate": "0001-01-01T00:00:00Z",
            "Status": "DoneForDay",
            "ExecutionStatus": "DoneForDay",
            "Type": "Market",
            "RequestStatus": "Complete",
            "Target": "New",
            "Description": "Expired by OMS",
            "Comment": "",
            "TimeInForce": "Day",
            "ExecInst": 0,
            "ExpireDate": "2019-01-30T21:00:00Z",
            "AccountId": 6303,
            "UserId": 7125,
            "RequestId": 98413,
            "StateId": 173093,
            "ParentId": -1,
            "Legs": [],
            "ExecutionVenue": "Etna Emulator",
            "TrailingStopAmountType": "Absolute",
            "TrailingStopAmount": 0,
            "TrailingLimitAmountType": "Absolute",
            "TrailingLimitAmount": 0,
            "CreateDate": "2019-01-30T15:09:23.7597893Z",
            "InitialType": "Market",
            "IsExternal": false,
            "ExecBrocker": "NSDQ",
            "ExecutionInstructions": {},
            "TransType": "New",
            "ValidationsToBypass": 0,
            "ParentRequestId": 0,
            "SettlementDate": "0001-01-01T00:00:00Z"
        }
    ],
    "NextPageLink": "https://pub-api-et-demo-prod.etnasoft.us/api/v1.0/accounts/6303/orders?pageNumber=1&pageSize=2",
    "PreviousPageLink": "",
    "TotalCount": 5
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal ID of the order |
| SecurityId | This is the internal ID of the underlying security of the order |
| Quantity | This is the number of shares in the order |
| StopPrice | This is the stop price of the order \(if there's no stop price — the value of this parameter will be 0\) |
| ClientId??? | This is the  |
| ExecutedQuantity | This is the number of shares that have been purchased or sold  |
| LastPrice | This is the price of the last executed order for the underlying security |
| LastQuantity |  |
| LeavesQuantity |  |
| AveragePrice | This is the average price at which the order was executed |
| Side | This is the type of order \(could be "Buy", "Sell", "SellShort", or "BuyToCover"\) |
| Date | This is the date on which the order was placed by the user |
| TransactionDate | This is the date on which  |
| SettDate |  |
| Status |  |
| ExecutionStatus | This is the execution status of the order.  |
| Type |  |
| RequestStatus |  |
| Target |  |
| TimeInForce |  |
| ExecInst |  |
| ExpireDate |  |
| CounterPartyOrderId |  |
| AccountId |  |
| UserId |  |
| RequestId |  |
| StateId |  |
| ParentId |  |
| Legs |  |
| Exchange |  |
| ExecutionVenue |  |
| TrailingStopAmountType |  |
| TrailingStopAmount |  |
| TrailingLimitAmountType |  |
| TrailingLimitAmount |  |
| CreateDate |  |
| InitialType |  |
| IsExternal |  |
| ExecBrocker |  |
| ExecutionInstructions |  |
| TransType |  |
| ExecId |  |
| ValidationsToBypass |  |
| ParentRequestId |  |
| SettlementDate |  |

### Common Mistakes

Here are some of the common mistakes that developers make when requesting the list of all outstanding and executed orders. 

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for listing all orders of a particular user, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

#### Specifying the User ID Instead of the Trading Account ID

Another common mistake when making this request is specifying the user ID instead of the user's trading account ID. Doing so will result in the 500 status code and the following error message:

```javascript
{
    "message": "An error occurred while processing your request",
    "error": "Unexpected server error"
}
```

#### Specifying a Trading Account of a Different User

It's critical to understand that when you use the authorization token of a particular user in this request's header, only this user's orders can be listed. Listing orders of a different user will lead to the 401 error.

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

In the following article we provide in-depth coverage of the syntax for this API request.

