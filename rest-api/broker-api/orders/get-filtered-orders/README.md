---
description: List a user's outstanding and executed orders
---

# Get Filtered Orders

## Overview

This GET endpoint enables to you list all outstanding and executed orders of the user whose authorization token was used in the request header. Optionally, you can filter the list by a set of criteria provided in the request's body.

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\). 
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **Trading Account ID** \(path\). This is the numeric ID of the trading account whose orders must be retrieved. 
4. **API version** \(path\). Unless necessary, leave it at "1.0".
5. **pageNumber** \(query\). Because there can be dozens of outstanding orders, we split them into pages which you can individually retrieve by specifying this parameter.
6. **pageSize** \(query\). This parameter indicates the number of orders from a particular page that must be returned in the response.

There's also one optional parameter worth examining:

* filter \(query\). This is an SQL query used to retrieve only those orders that satisfy the conditions of the query. The following table outlines the parameter's syntax.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Syntax</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>CreateDate (&gt;, &gt;=, &lt;, &lt;=) Date</li>
          <li>CreateDate between Range</li>
        </ul>
      </td>
      <td style="text-align:left">This query enables you to retrieve orders that were created in the time
        period specified in the Range parameter or exactly at the time specified
        in the Date parameter.</td>
      <td style="text-align:left">
        <ul>
          <li>CreateDate between #2019-03-13T18:31:42# and #2019-03-17T18:31:42#</li>
          <li>CreateDate &gt;= #2019-03-13T18:31:42#</li>
          <li>CreateDate &lt; #2019-03-12T19:31:42#</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">SecurityId = Number</td>
      <td style="text-align:left">This query enables you to retrieve orders whose securityId parameter is
        equal to the Id provided in the query.</td>
      <td style="text-align:left">
        <ul>
          <li>SecurityId = 4</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Status in (value1, value2, etc.)</td>
      <td style="text-align:left">This query enables you to retrieve orders whose Status parameter is contained
        in the query set.</td>
      <td style="text-align:left">
        <ul>
          <li>Status in (0,1,4,5,7)</li>
          <li>Status in (0)</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>{% hint style="info" %}
Note that you can combine different queries to create more complex requests:

* SecurityId = 4 and Status in \(0,1,2,3,4,5,6,7,8,9,20\)
{% endhint %}

Here's the final template for this API request:

```text
apiURL/v1.0/accounts/{accountNumber}/orders?pageNumber=0&pageSize=2
```

## Response

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


| Id | This is the internal ID of the order. |
| :--- | :--- |


| SecurityId | This is the internal ID of the underlying security of the order. |
| :--- | :--- |


| Quantity | This is the number of shares in the order. |
| :--- | :--- |


| StopPrice | This is the stop price of the order \(if there's no stop price — the value of this parameter will be 0\). |
| :--- | :--- |


| ClientId | This is the order ID on the client's side. |
| :--- | :--- |


| ExecutedQuantity | This is the number of shares that have been purchased or sold. |
| :--- | :--- |


| LastPrice | This is the price of the last executed order for the underlying security. |
| :--- | :--- |


| LastQuantity | This is the number of shares that were traded in the last transaction. |
| :--- | :--- |


| LeavesQuantity | This is the number of shares in the order that are yet to be purchased. |
| :--- | :--- |


| AveragePrice | This is the average price at which the order was executed. |
| :--- | :--- |


| Side | This is the type of order \(could be "Buy", "Sell", "SellShort", or "BuyToCover"\). |
| :--- | :--- |


| Date | This is the date on which the order was placed by the user. |
| :--- | :--- |


| TransactionDate | This is the date on which the transaction took place. |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">Status</th>
      <th style="text-align:left">
        <p>This is the current status of the order. Possible values:</p>
        <p>0 - New</p>
        <p>1 - Partially Filled</p>
        <p>2 - Filled</p>
        <p>3 - Done For Day</p>
        <p>4 - Canceled</p>
        <p>5 - Replaced</p>
        <p>6 - Pending Cancel</p>
        <p>7 - Stopped</p>
        <p>8 - Rejected</p>
        <p>9 - Suspended</p>
        <p>10 - Pending New</p>
        <p>11 - Calculated</p>
        <p>12 - Expired</p>
        <p>13 - Accepted For Bidding</p>
        <p>14 - Pending Replace</p>
        <p>15 - Error</p>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| ExecutionStatus | This is the execution status of the order. It's usually identical to Status with the exception of emergency situations. For example, if an order modification request was rejected by the exchange because the order has already been filled, the status will be **Filled** and the execution status will be **Rejected**. |
| :--- | :--- |


| Type | This is the type of the order. The range of possible values includes: **Market**, **Limit**, **Stop**, **Stop Limit**. |
| :--- | :--- |


| RequestStatus | This is the status of the order modification request. |
| :--- | :--- |


| Target | This is the target operation of the order. Possible values: **new**, **cancel**, **modify**. |
| :--- | :--- |


<table>
  <thead>
    <tr>
      <th style="text-align:left">TimeInForce</th>
      <th style="text-align:left">
        <p>Indicates the time frame in which the order will be active. Possible Values:</p>
        <ol>
          <li><b>Day</b>. The order automatically expires at the end of the regular
            trading session if it weren&apos;t executed.</li>
          <li><b>GTC</b> (Good-till-Canceled). The order persists indefinitely until
            it is executed or manually cancelled.</li>
          <li><b>AtTheOpening</b>. The order should be filled at the opening of the
            marketplace or cancelled.</li>
          <li><b>ImmediateOrCancel</b>. The order should be completely or partially
            filled immediately. If partially filled, the remaining part of the order
            should be cancelled.</li>
          <li><b>FillOrKill</b>. The order should be filled immediately and entirely
            or cancelled right away.</li>
          <li><b>GoodTillCrossing</b>. The order will be active until the market enters
            the auction phase.</li>
          <li><b>GoodTillDate</b>. The order will be active until the date specified
            in the ExpireDate attribute (unless it is executed or cancelled).</li>
          <li><b>GoodTillTime</b>. The order will be active until a certain time point.</li>
        </ol>
      </th>
    </tr>
  </thead>
  <tbody></tbody>
</table>| ExecInst | Indicates if the order should be filled either entirely in one transaction or not at all. Possible values: **'DoNotIncrease'**, **'DoNotReduce'**, **'AllOrNone'**. |
| :--- | :--- |


| ExpireDate | This is the expiration of the order. If the order isn't executed until the specified date, it'll automatically be cancelled. |
| :--- | :--- |


| CounterPartyOrderId | This is the order of the order counterparty on the execution venue \(set by the executor\). |
| :--- | :--- |


| AccountId | This is the identifier of the trading account. |
| :--- | :--- |


| UserId | This is the ID of the user on whose trading account the order was executed. |
| :--- | :--- |


| RequestId | This is the identifier of the request modification. |
| :--- | :--- |


| StateId | The is the identifier of the order's state in ETNA Trader. |
| :--- | :--- |


| ParentId | This is the ID of the parent security in a multi-leg order. |
| :--- | :--- |


| Legs | These are the legs of a multi-leg order. |
| :--- | :--- |


| Exchange | This is the exchange on which the order should be executed. |
| :--- | :--- |


| ExecutionVenue | This is the execution venue of the order \(the list of options may vary depending on which exchanges are available to your company\). |
| :--- | :--- |


| TrailingStopAmountType | This is the type of the trailing stop \(**Absolute** or **Persentage**\). |
| :--- | :--- |


| TrailingStopAmount | This is the trailing amount of the trailing stop \(in percentage terms or in the currency units\). |
| :--- | :--- |


| TrailingLimitAmountType | This is the type of the trailing limit \(**Absolute** or **Persentage**\). |
| :--- | :--- |


| TrailingLimitAmount | This is the trailing amount \(in percentage terms or in the currency units\). |
| :--- | :--- |


| CreateDate | This is the date on which the order was created. |
| :--- | :--- |


| InitialType | This is the initial type of the order. |
| :--- | :--- |


| IsExternal | This field indicates if the order was placed externally. For example, a user can place an order manually by calling their broker without using ETNA Trader. |
| :--- | :--- |


| ExecBrocker | This is the final executor of the order. |
| :--- | :--- |


| ExecutionInstructions | These are instructions specified as part of the order. |
| :--- | :--- |


| TransType | This is the type of the execution transaction. Possible values: **New**, **Correct**, **Cancel**, **Status**. |
| :--- | :--- |


| ExecId | This is the identifier of the execution on the execution venue. |
| :--- | :--- |


| ValidationsToBypass | Indicates the validation rules that must be skipped. |
| :--- | :--- |


| ParentRequestId | This is an internal ETNA Trader field that should not be used. |
| :--- | :--- |


| SettlementDate | This is the date on which the order was settled. |
| :--- | :--- |


Here are some of the common mistakes that developers make when requesting the list of all outstanding and executed orders.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

### Specifying the User ID Instead of the Trading Account ID

Another common mistake when making this request is specifying the user ID instead of the user's trading account ID. Doing so will result in the 500 status code and the following error message:

```javascript
{
    "message": "An error occurred while processing your request",
    "error": "Unexpected server error"
}
```

### Specifying a Trading Account of a Different User

It's critical to understand that when you use the authorization token of a particular user in this request's header, only this user's orders can be listed. Listing orders of a different user will lead to the 401 error.

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

In the following article we provide in-depth coverage of the syntax for this API request.

