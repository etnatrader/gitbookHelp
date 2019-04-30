---
description: Place a new order
---

# Place Order

### Overview

This POST endpoint enables you to place a new order in ETNA Trader. The order is sent in the JSON format to our service which turns it into a new outstanding order that should eventually be fulfilled \(or suspended depending on the type of order and the [order review mechanisms](../../../../administrator-guide/administrators-widgets/bo-order-review/) applicable to this user\). 

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **Trading Account ID** \(path\). This is the numeric ID of the trading account on which a new order must be placed. 
4. **API version** \(path\). Unless necessary, leave it at "1.0".
5. **body** \(body of the request\). This is a JSON file that contains the order's characteristics. 

Here's the final template for this API request:

```text
POST apiURL/v1.0/accounts/{accountID}/orders
```

### Request Body

The body of this request represents the information about the to-be-created order. It must be sent in the JSON format with the parameters described in the following table:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Parameter</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Symbol</td>
      <td style="text-align:left">This is the ticker symbol of the underlying security in the new order.</td>
    </tr>
    <tr>
      <td style="text-align:left">ClientId</td>
      <td style="text-align:left">This is the order ID on the client&apos;s side.</td>
    </tr>
    <tr>
      <td style="text-align:left">ExpireDate</td>
      <td style="text-align:left">This is the expiration of the order. If the order isn&apos;t executed
        until the specified date, it&apos;ll automatically be cancelled.</td>
    </tr>
    <tr>
      <td style="text-align:left">Type</td>
      <td style="text-align:left">This is the type of the order. The range of possible values includes: <b>Market</b>, <b>Limit</b>, <b>Stop</b>, <b>Stop Limit</b>.</td>
    </tr>
    <tr>
      <td style="text-align:left">Side</td>
      <td style="text-align:left">This is the side of the trade. The range of possible values includes: <b>Buy</b>, <b>Sell</b>, <b>Sell</b>  <b>Short</b>, <b>Buy to Cover</b>.</td>
    </tr>
    <tr>
      <td style="text-align:left">ExecInst</td>
      <td style="text-align:left">Indicates if the order should be filled either entirely in one transaction
        or not at all. Possible values: <b>&apos;DoNotIncrease&apos;</b>, <b>&apos;DoNotReduce&apos;</b>, <b>&apos;AllOrNone&apos;</b>.</td>
    </tr>
    <tr>
      <td style="text-align:left">TimeInforce</td>
      <td style="text-align:left">
        <p>Indicates the time frame in which the order will be active. Possible Values:</p>
        <ol>
          <li><b>Day</b>. The order automatically expires at the end of the regular
            trading session if it weren&apos;t executed.</li>
          <li><b>GTC </b>(Good-till-Canceled). The order persists indefinitely until
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
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Quantity</td>
      <td style="text-align:left">The number of shares in the order.</td>
    </tr>
    <tr>
      <td style="text-align:left">Price</td>
      <td style="text-align:left">The price at which the shares must be purchased.</td>
    </tr>
    <tr>
      <td style="text-align:left">StopPrice</td>
      <td style="text-align:left">When this price is reached, the order will automatically be converted
        into a market order.</td>
    </tr>
    <tr>
      <td style="text-align:left">Exchange</td>
      <td style="text-align:left">This is the exchange on which the order should be executed.</td>
    </tr>
    <tr>
      <td style="text-align:left">TrailingStopAmountType</td>
      <td style="text-align:left">This is the type of the trailing stop (<b>Absolute</b> or <b>Persentage</b>).</td>
    </tr>
    <tr>
      <td style="text-align:left">TrailingStopAmount</td>
      <td style="text-align:left">This is the trailing amount of the trailing stop (in percentage terms
        or in the currency units).</td>
    </tr>
    <tr>
      <td style="text-align:left">TrailingLimitAmountType</td>
      <td style="text-align:left">This is the type of the trailing limit (<b>Absolute</b> or <b>Persentage</b>).</td>
    </tr>
    <tr>
      <td style="text-align:left">TrailingLimitAmount</td>
      <td style="text-align:left">This is the trailing amount (in percentage terms or in the currency units).</td>
    </tr>
    <tr>
      <td style="text-align:left">ExtendedHours</td>
      <td style="text-align:left">Indicates if the order should be placed during the extended hours (pre-market
        session, post-market session).</td>
    </tr>
    <tr>
      <td style="text-align:left">ExecutionInstructions</td>
      <td style="text-align:left">Execution instructions for algorithmic trades.</td>
    </tr>
    <tr>
      <td style="text-align:left">Legs</td>
      <td style="text-align:left">These are the legs of a multi-leg order.</td>
    </tr>
  </tbody>
</table>#### Smallest Market Order Sample

```javascript
{
  "Symbol": "AAPL", //Buying 100 shares of the Apple stock
  "Type": "Market",
  "Side": "Buy",
  "Quantity": 100
}
```

#### Smallest Limit Order Sample

```javascript
{
  "Symbol": "AAPL", //Buying 100 shares of the Apple stock
  "Type": "Limit",
  "Side": "Buy",
  "Quantity": 100,
  "Price" : 170 //The limit price of the order
}
```

#### Smallest Stop Order Sample

```javascript
{
  "Symbol": "AAPL", //Buying 100 shares of the Apple stock
  "Type": "Stop",
  "Side": "Buy",
  "Quantity": 100,
  "StopPrice" : 150 //The stop price of the order
}
```

#### Smallest Stop-Limit Order Sample

```javascript
{
  "Symbol": "AAPL", //Buying 100 shares of the Apple stock
  "Type": "StopLimit",
  "Side": "Buy",
  "Quantity": 100,
  "StopPrice" : 149, //The stop price of the order
  "Price": 150 //The limit price of the order
}
```

#### Smallest Limit Order Sample \(Options\)

```javascript
{
  "Symbol": "STNE  190517P00055000", //the option's OSI Symbol
  "ExpireDate": "2019-03-24T17:32:28.824Z",
  "Type": "Limit",
  "Side": "Buy",
  "Price":170,
  "ExecInst": "DoNotIncrease",
  "TimeInforce": "Day",
  "Quantity": 1,
}
```

#### Complex Order Sample \(Options\)

```javascript
{
  "Symbol": "AAPL  190503C00165000", //the option's OSI Symbol
  "ExpireDate": "2019-03-30T17:00:00.824Z",  
  "Type": "Limit",
  "Side": "Buy",
  "Price":170,
  "ExecInst": "DoNotIncrease",
  "TimeInforce": "Day",
  "Quantity": 1,
  "Legs": [{ //simultaneously buying the Apple stock
			"Symbol": "AAPL", 
			"Type": "Market",
			"Side": "Buy",
			"Quantity": 100
		}
	]
}
```

#### Multi-Leg Order Sample \(Option + Option\)

```javascript
{
	"Symbol": "",
	"Legs": [{
			"Symbol": "AAPL  190503C00165000",
			"ExpireDate": "2019-03-30T17:00:00.824Z",
			"Type": "Market",
			"Side": "Buy",
			"ExecInst": "DoNotIncrease",
			"TimeInforce": "Day",
			"Quantity": 1
		},
		{
			"Symbol": "AAPL  190503C00165000",
			"ExpireDate": "2019-03-24T17:32:28.824Z",
			"Type": "Limit",
			"Side": "Buy",
			"Price": 200,
			"ExecInst": "DoNotIncrease",
			"TimeInforce": "Day",
			"Quantity": 1
		}
	]
}
```

#### Comprehensive Limit Order Sample

```javascript
{
  "Symbol": "AAPL",
  "ExpireDate": "2019-03-24T10:07:59.181Z",
  "Type": "Limit",
  "Side": "Buy",
  "ExecInst": "AllOrNone",
  "TimeInforce": "GTC",
  "Quantity": 100,
  "Price": 190,
  "Exchange": "XNAS",
  "ExtendedHours": "REGPOST",
  "ExecutionInstructions" : {"Commission": "0.5"}
}
```

#### Comprehensive Market Order Sample

```javascript
{
  "Symbol": "AAPL",
  "ExpireDate": "2019-03-24T10:07:59.181Z",
  "Type": "Market",
  "Side": "Buy",
  "ExecInst": "AllOrNone",
  "TimeInforce": "GTC",
  "Quantity": 445,
  "Exchange": "XNAS",
  "ExtendedHours": "PRE",
  "ExecutionInstructions" : {"Commission": "0.5"}
}
```

#### Comprehensive Stop Order Sample

```javascript
{
  "Symbol": "AAPL",
  "ExpireDate": "2019-07-30T10:07:59.181Z",
  "Type": "Stop",
  "Side": "Buy",
  "ExecInst": "AllOrNone",
  "TimeInforce": "GTC",
  "Quantity": 100,
  "StopPrice" : 200,
  "Exchange": "XNAS",
  "ExtendedHours": "REG",
  "ExecutionInstructions" : {"Commission": "0.5"}
}
```

#### Comprehensive Stop Limit Order Sample

```javascript
{
  "Symbol": "AAPL",
  "ExpireDate": "2019-12-20T10:07:59.181Z",
  "Type": "StopLimit",
  "Side": "Buy",
  "ExecInst": "AllOrNone",
  "TimeInforce": "GTC",
  "Quantity": 105,
  "Exchange": "XNAS",
  "ExtendedHours": "REGPOST",
   "Price" : 201,
   "StopPrice" : 200,
   "ExecutionInstructions" : {"Commission": "0.5"}
}
```

#### Comprehensive Trailing Stop Order Type

```javascript
{
  "Symbol": "AAPL",
  "ExpireDate": "2019-12-20T10:07:59.181Z",
  "Type": "TrailingStop",
  "Side": "Buy",
  "ExecInst": "AllOrNone",
  "TimeInforce": "GTC",
  "Quantity": 105,
  "Exchange": "XNAS",
  "ExtendedHours": "REGPOST",
  "TrailingStopAmountType" : "Persentage",
  "TrailingStopAmount" : 2
}
```

#### Comprehensive Trailing Stop Limit Order Type

```javascript
{
  "Symbol": "AAPL",
  "ExpireDate": "2019-12-20T10:07:59.181Z",
  "Type": "TrailingStopLimit",
  "Side": "Buy",
  "ExecInst": "AllOrNone",
  "TimeInforce": "GTC",
  "Quantity": 1,
  "Exchange": "XNAS",
  "TrailingLimitAmountType" : "Absolute", //Limit offset
  "TrailingLimitAmount" : 4,
  "ExtendedHours": "REGPOST",
  "TrailingStopAmountType" : "Absolute", //Trailing Stop
  "TrailingStopAmount" : 10,
}
```

#### One-Triggers-the-Other Order Type

One-Triggers-the-Other is a type of conditional order in which execution of one order automatically triggers the other one. Each of the two orders has to be provided as a separate leg:

```javascript
{
	"Type": "OneTriggerOther", //the type of the order
        "Symbol": "", //this parameter must be empty
		"Legs": [{ //the array of two legs
			"Symbol": "AAPL", //the first leg
			"Type": "Limit",
			"Price": 150,
			"Side": "Buy",
			"Quantity": 100
		},
		{
			"Symbol": "TSLA", //the second leg
			"Type": "Limit",
			"Price": 100,
			"Side": "Buy",
			"Quantity": 100
		}
	]
}
```

In this case, if the limit order to purchase the Apple stock gets executed, the second limit order to purchase the Tesla stock will automatically be triggered.

{% hint style="warning" %}
In One-Triggers-the-Other orders, the first leg cannot be a market order.
{% endhint %}

#### One-Cancels-the-Other Order Type

One-Cancels-the-Other is a type of conditional order in which execution of one order automatically cancels the other one. Each of the two orders has to be provided as a separate leg:

```javascript
{
	"Type": "OneCancelOther", //the type of the order
        "Symbol": "", //this parameter must be empty
		"Legs": [{ //the array of two legs
			"Symbol": "AAPL", //the first leg
			"Type": "Limit",
			"Price": 150,
			"Side": "Buy",
			"Quantity": 100
		},
		{
			"Symbol": "TSLA", //the second leg
			"Type": "Limit",
			"Price": 100,
			"Side": "Buy",
			"Quantity": 100
		}
	]
}
```

In this case, if the limit order to purchase the Apple stock gets executed, the second limit order to purchase the Tesla stock will automatically be cancelled.

{% hint style="warning" %}
In One-Cancels-the-Other orders, both legs cannot be market orders.
{% endhint %}

### Response

In response to this request, you'll receive a JSON file with comprehensive information about the newly created order:

```javascript
{
    "Id": 80328,
    "SecurityId": 4,
    "Quantity": 100,
    "Price": 0,
    "StopPrice": 0,
    "ClientId": "2029837977",
    "ExecutedQuantity": 0,
    "LastPrice": 0,
    "LastQuantity": 0,
    "LeavesQuantity": 0,
    "AveragePrice": 0,
    "Side": "Buy",
    "Date": "2019-02-25T13:33:40.9022856Z",
    "TransactionDate": "2019-02-25T13:33:40.9022856Z",
    "SettDate": "0001-01-01T00:00:00Z",
    "Status": "PendingNew",
    "ExecutionStatus": "PendingNew",
    "Type": "Market",
    "RequestStatus": "RequireValidation",
    "Target": "New",
    "TimeInForce": "Day",
    "ExecInst": 0,
    "ExpireDate": "2019-02-25T21:00:00Z",
    "AccountId": 6303,
    "UserId": 7125,
    "RequestId": 105467,
    "StateId": 0,
    "ParentId": -1,
    "Legs": [],
    "TrailingStopAmountType": "Absolute",
    "TrailingStopAmount": 0,
    "TrailingLimitAmountType": "Absolute",
    "TrailingLimitAmount": 0,
    "CreateDate": "2019-02-25T13:33:40.9022856Z",
    "InitialType": "Market",
    "IsExternal": false,
    "ExecutionInstructions": {
        "CorrelationId": "ade9537995f84dcc840eabc724107487",
        "CreateOrderRequestTimeUnix": "636866984209012879"
    },
    "TransType": "New",
    "ValidationsToBypass": 0,
    "ParentRequestId": 0,
    "SettlementDate": "0001-01-01T00:00:00Z"
}
```

{% hint style="warning" %}
Please note that you may receive the 200 status code even if the order was improperly configured. For example, if you attempt to create a limit order and specify the stop price instead of the limit price, the order will be registered in the system but will eventually be rejected. Please monitor the order's status \(it's _PendingNew_ by default\) to determine if the order has been rejected or placed.
{% endhint %}

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to place a new order. 

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

It's critical to understand that when you use the authorization token of a particular user in this request's header, only this user's trading accounts can be used for placing new orders. Placing a new order on a trading account of a different user will lead to the 401 error.

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

In the following article we provide in-depth coverage of the syntax for this API request.

#### Placing Orders Whose Value Exceeds the Account's Buying Power

When attempting to place an order whose value exceeds the trading account's buying power, you'll receive a JSON file with the `ErrorDescription` parameter equaling `DayTradingBuyingPowerExceeded`.

```javascript
{
  "IsSuccessful": false,
  "ErrorDescription": "DayTradingBuyingPowerExceeded",
  "ErrorDescriptionArgs": [],
  "Commission": 3.75,
  "Commissions": {
    "Per Trade Commission": 3.75
  },
  "Cost": 1766790,
  "NetCost": 1766786.25,
  "Quotes": [
    {
      "Ask": 196.31,
      "Bid": 196.28,
      "Last": 196.29,
      "Volume": 200,
      "OpenInterest": 0
    }
  ],
  "MarginChange": 0
}
```

#### Failing to Specify the Limit Price for Limit Orders

An attempt to place a limit order without specifying its price will result in an error; in response you'll receive a JSON file with the `ErrorDescription` parameter equaling `QuotePriceIsInvalid`.

```javascript
{
  "IsSuccessful": false,
  "ErrorDescription": "QuotePriceIsInvalid",
  "Commission": 0,
  "Commissions": {},
  "Cost": 0,
  "NetCost": 0,
  "MarginChange": 0
}
```

#### Failing to Specify the Stop Price for Stop-Loss Orders

An attempt to place a stop-loss order without specifying its price will result in an error; in response you'll receive a JSON file with the `ErrorDescription` parameter equaling `QuotePriceIsInvalid`.

```javascript
{
  "IsSuccessful": false,
  "ErrorDescription": "QuotePriceIsInvalid",
  "Commission": 0,
  "Commissions": {},
  "Cost": 0,
  "NetCost": 0,
  "MarginChange": 0
}
```

### Sample Code

Feel free to examine our [Code Samples](../../code-samples/placing-new-orders.md#placing-new-orders-and-checking-their-status) article that demonstrates how to place a new order with the help of a Python script.

The following article covers the syntax for this API request in detail.

The following article covers the syntax for this API request in detail.

