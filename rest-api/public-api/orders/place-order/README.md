# Place Order

### Overview

This POST endpoint enables you to place a new order in ETNA Trader. The order is sent in the JSON format to our service which turns it into a new outstanding order that should eventually be fulfilled \(or suspended depending on the type of order and the [order review mechanisms](../../../../administrator-guide/administrators-widgets/bo-order-review/) applicable to this user\). 

{% hint style="warning" %}
In order to place a new order, you must use an [authorization token](../../authentication/requesting-tokens/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

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

The body of this request represents the information about the to-be-created order. It must be sent in the JSON format in the following way:

```javascript
{
  "Symbol": "string",
  "ClientId": "string",
  "ExpireDate": "2019-02-12T12:04:52.868Z",
  "Type": "Market",
  "Side": "Buy",
  "ExecInst": "AllOrNone",
  "TimeInforce": "Day",
  "Quantity": 0,
  "Price": 0,
  "StopPrice": 0,
  "Exchange": "string",
  "TrailingStopAmountType": "Absolute",
  "TrailingStopAmount": 0,
  "TrailingLimitAmountType": "Absolute",
  "TrailingLimitAmount": 0,
  "ExtendedHours": "string",
  "Token": "string",
  "ExecutionInstructions": {},
  "ValidationsToBypass": 0,
  "Legs": [
    {}
  ]
}
```

where:

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
      <td style="text-align:left">This is the order ID on the client's side.</td>
    </tr>
    <tr>
      <td style="text-align:left">ExpireDate</td>
      <td style="text-align:left">This is the expiration of the order. If the order isn't executed until
        the specified date, it'll automatically be cancelled.</td>
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
        or not at all. Possible values: <b>'DoNotIncrease'</b>, <b>'DoNotReduce'</b>, <b>'AllOrNone'</b>.</td>
    </tr>
    <tr>
      <td style="text-align:left">TimeInforce</td>
      <td style="text-align:left">
        <p>Indicates the time frame in which the order will be active. Possible Values:</p>
        <ol>
          <li><b>Day</b>. The order automatically expires at the end of the regular
            trading session if it weren't executed.</li>
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
      <td style="text-align:left">Token</td>
      <td style="text-align:left">Optional token (additional identity key)</td>
    </tr>
    <tr>
      <td style="text-align:left">ExecutionInstructions</td>
      <td style="text-align:left">Execution instructions for algorithmic trades</td>
    </tr>
    <tr>
      <td style="text-align:left">ValidationsToBypass</td>
      <td style="text-align:left">Indicates the validation rules that must be skipped</td>
    </tr>
    <tr>
      <td style="text-align:left">Legs</td>
      <td style="text-align:left">These are the legs of a multi-leg order</td>
    </tr>
  </tbody>
</table>### Response

In response to this request, you'll receive a JSON file confirming that the order has been successfully placed:

```javascript

```

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to place a new order. 

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for placing a new order, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

It's critical to understand that when you use the authorization token of a particular user in this request's header, only this user's trading accounts can be used for placing new orders. Placing a new order on a trading account of a different user will lead to the 401 error.

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

In the following article we provide in-depth coverage of the syntax for this API request.

