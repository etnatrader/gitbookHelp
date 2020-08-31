# Sell a Mutual Fund

### Overview

This POST endpoint enables you to place an order to sell a mutual fund.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **Trading Account ID** \(path\). This is the internal ID of the trading account on whose behalf a new order must be placed. 
4. **API version** \(path\). Unless necessary, leave it at "1.0".
5. **body** \(body of the request\). This is a JSON object that contains the order's parameter. 

#### Body Syntax

The body of this request represents the information about the to-be-placed order. It must be sent in the JSON format with the parameters described in the following table:

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
      <td style="text-align:left">The ticker symbol of the target mutual fund.</td>
    </tr>
    <tr>
      <td style="text-align:left">Quantity</td>
      <td style="text-align:left">The number of mutual fund shares to be purchased.</td>
    </tr>
    <tr>
      <td style="text-align:left">QuantityQualifier</td>
      <td style="text-align:left">
        <p>The quantity qualifier.
          <br />Possible values (depends on the configuration of the environment):</p>
        <ul>
          <li>EvenDollar</li>
          <li>Shares</li>
          <li>GrossDollar</li>
          <li>MinusRounding</li>
          <li>PlusRounding</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

The following is a sample JSON that can be used to place a sell order for a mutual fund:

```javascript
{
  "Symbol":"PHDAX",
  "Quantity":700,
  "QuantityQualifier":"EvenDollar",
}
```

Here's the final template for this API request:

```text
POST apiURL/v1.0/accounts/{Trading Account ID}/orders/mutual-funds/sell
```

### Response

In response to this API request, you will receive a JSON object containing the current information about the order:

```javascript
{
  "Id": 336989,
  "Status": "PendingNew",
  "ExecutionStatus": "PendingNew",
  "ExecutedQuantity": 0,
  "Quantity": 700
}
```

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to place an order to sell a mutual fund.

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
  "Message": "Validation error occured while processing entity",
  "ModelState": {
    "resource.Symbol": [
      "Symbol is required"
    ]
  }
}
```

