# Buy a Mutual Fund

### Overview

This POST endpoint enables you to place an order to purchase a mutual fund. Unlike a regular order dealing with stocks and bonds, orders involving mutual funds necessitate specification of associated parameters like reinvestment of dividends, reinvestment of long- or short-term gains, etc. And all of these parameters can be passed in the payload of this request to enable traders to properly place mutual fund orders.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **Trading Account ID** \(path\). This is the internal ID of the trading account on whose behalf a new order must be placed. 
4. **API version** \(path\). Unless necessary, leave it at "1.0".
5. **body** \(body of the request\). This is a JSON file that contains the order's characteristics. 

#### Body Syntax

The body of this request represents the information about the to-be-created order. It must be sent in the JSON format with the parameters described in the following table:

| Parameter | Description |
| :--- | :--- |
| Action | The side of the order. Since you're trying to purchase a mutual funds, set it to **Buy**. |
| Symbol | The ticker symbol of the target mutual fund. |

Here's the final template for this API request:

```text
POST apiURL/v1.0/accounts/{Trading Account ID}/orders/mutual-funds/buy
```



```javascript
{
  "Action":"Buy",
  "Symbol":"PHDAX",
  "Quantity":700,
  "QuantityQualifier":"EvenDollar",
  "ReinvestDividends":true,
  "ReinvestShortTermGains":true,
  "ReinvestLongTermGains":true
}
```

