# Add New Position

### Overview

This POST endpoint enables you to create positions in securities, bypassing the regular oder creation mechanism. Every once in a while some breakdown takes place on the exchange or in ETNA Trader, forcing you to use our Back Office to manually add the required position to the user's trading account. This procedure must be carried out with caution so as to prevent any conflicts.

{% hint style="warning" %}
In order to add a new position, you must use an [authorization token](../authentication/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **recalculate** \(query\). This is a boolean field that indicates if the account's cash should be recalculated after adding the new position.
5. **position** \(body\). This is a JSON file that contains information about the new position. 

#### New Position Syntax

Following is a sample of a new position that can be added to a user's trading account. The first three parameters — **AccountId**, **SecurityId**, and **Quantity** — are mandatory while the rest can be configured depending on the circumstances. If you intend to increase the number of securities in an existing position, you must also provide the **Id** parameter.

```javascript
{
  "AccountId": 6688, //required
  "SecurityId": 4 ,  //required
  "Quantity": 107, //required
  "CostBasis": 0,
  "Id" : 701, //should only be indicated if the position already exists 
  "DailyCostBasis": 0,
  "CreateDate": "2019-02-27T10:24:18.492Z",
  "ModifyDate": "2019-02-27T10:24:18.492Z",
  "RealizedProfitLoss": 0,
  "AverageOpenPrice": 0,
  "AverageClosePrice": 0,
  "StopLossPrice": 0,
  "TakeProfitPrice": 0,
  "DailyCloseProfitLoss": 0,
  "ExcessChanges": 0,
  "DayQuantity": 0,
  "OpenQuantity": 0,
  "LastLot": 0,
  "Unsettled": 0,
  "UnsettledDate": "2019-02-27T10:24:18.492Z",
  "MarginType": "Empty",
  "Locked": true,
  "SpreadQuantity": 0 
}
```

where:

| Parameter | Description |
| :--- | :--- |
| AccountId | This is the internal identifier of the trading account. |
| SecurityId | This is the internal identifier of the underlying security in ETNA Trader. You can get this ID using [this API method](../securities/get-securitys-info-by-its-ticket-symbol.md). |
| Quantity | This is the number of securities in the new position. |
| CostBasis | This is the weighted average execution price of the order. |
| Id | This is the internal identifier of an existing position to which you intend to add securities. |
| DailyCostBasis | The gross cost of all positions during the day. After the trading session this variable resets to the PrevCloseMarketValue variable. |
| CreatedDate | This is the date on which the position was created. |
| ModifyDate | This is the date on which the position was modified. |
| RealizedProfitLoss | Realized profit or loss. |
| AverageOpenPrice | The average opening price of the position. |
| AverageClosePrice | The average closing price of the position.  |
| StopLossPrice | This is the price at which the position should be terminated if the market value reaches the price. |
| TakeProfitPrice | This is the price at which the profit of the position should be realized if the market value reaches the price. |
| DailyCloseProfitLoss |  |

