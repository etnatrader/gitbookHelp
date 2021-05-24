---
description: Place a buy order for a mutual fund
---

# Buy a Mutual Fund

### Overview

This POST endpoint enables you to place an order to purchase a mutual fund. Unlike a regular order dealing with stocks and bonds, orders involving mutual funds necessitate specification of associated parameters like reinvestment of dividends, reinvestment of long- or short-term gains, etc. And all of these parameters can be passed in the payload of this request to enable traders to properly place mutual fund orders.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/). The value of this header must have the following format: `Bearer BQ898r9fefi` \(`Bearer` + 1 space + the token\).
3. **Trading Account ID** \(path\). This is the internal ID of the trading account on whose behalf a new order must be placed. 
4. **API version** \(path\). Unless necessary, leave it at "1.0".
5. **body** \(body of the request\). This is a JSON file that contains the order's characteristics. 

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
    <tr>
      <td style="text-align:left">ReinvestDividends</td>
      <td style="text-align:left">Indicates if the mutual fund&apos;s managers should reinvest dividends
        received from its holdings.</td>
    </tr>
    <tr>
      <td style="text-align:left">ReinvestShortTermGains</td>
      <td style="text-align:left">Indicates if the mutual fund&apos;s managers should reinvest the realized
        short-term capital gains.</td>
    </tr>
    <tr>
      <td style="text-align:left">ReinvestLongTermGains</td>
      <td style="text-align:left">Indicates if the mutual fund&apos;s managers should reinvest the realized
        short-term capital gains.</td>
    </tr>
  </tbody>
</table>

The following is a sample JSON that can be used to place a buy order for a mutual fund:

```javascript
{
  "Symbol":"PHDAX",
  "Quantity":700,
  "QuantityQualifier":"EvenDollar",
  "ReinvestDividends":true,
  "ReinvestShortTermGains":true,
  "ReinvestLongTermGains":true
}
```

Here's the final template for this API request:

```text
POST apiURL/v1.0/accounts/{Trading Account ID}/orders/mutual-funds/buy
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

Here are some of the common mistakes that developers make when attempting to place an order to buy a mutual fund.

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

