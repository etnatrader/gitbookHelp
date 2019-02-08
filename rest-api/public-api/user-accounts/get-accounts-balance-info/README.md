---
description: Get balance information of a particular trading account
---

# Get Account's Balance Info

### Overview

This endpoint enables you to retrieve balance information of a particular trading account.

{% hint style="warning" %}
In order to request balance information of a particular trading account, you must use an [authorization token](../../authentication/requesting-tokens/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **Trading Account Number** \(path\). This is the numeric ID of the user  whose trading accounts you'd like to list. You can get the list of a user's trading accounts with [this API call](../list-users-accounts/).
4. **API version** \(path\). Unless necessary, leave it at "1.0"

### Response

In response to this request, you'll receive a JSON file with all of the pertinent information about the trading account:

```javascript
{
    "cash": 976510.75,
    "netCash": 976510.75,
    "excess": 994654.45,
    "changeAbsolute": -571.5,
    "changePercent": -0.05700775140829844330933239,
    "equityTotal": 1001923.75,
    "pendingOrdersCount": 0,
    "netLiquidity": 25413,
    "stockLongMarketValue": 25413,
    "stockShortMarketValue": 0,
    "optionLongMarketValue": 0,
    "optionShortMarketValue": 0,
    "forexLongMarketValue": 0,
    "forexShortMarketValue": 0,
    "dayTrades": 0,
    "stockBuyingPower": 1989308.9,
    "optionBuyingPower": 994654.45,
    "forexBuyingPower": 1989308.9,
    "dayTradingBuyingPower": 3978617.8,
    "pendingCash": 0,
    "maintenanceMargin": 7692.3,
    "optionMaintenanceMargin": 0,
    "openPL": 1927.5,
    "closePL": 0,
    "marketValue": 25413
}
```

where:

| Parameter | Description |
| :--- | :--- |
| cash | This is the amount of funds available on the trading account.  |
| netCash | This the amount of funds available on the account minus all liabilities \(short positions, etc.\). |
| excess | This is the amount of funds that can either be withdrawn or used to open new positions. |
| changeAbsolute | This is the average difference between the opening and the closing price.   |
| changePercent | ? |
| equityTotal | This is the gross valuation of all equity on the trading account. |
| pendingOrdersCount | This is the number of pending orders on the account. |
| netLiquidity | This is the amount of funds that will be available to the user after all active positions are terminated. |
| stockLongMarketValue | This is the gross market value of all long stock positions on the trading account. |
| stockShortMarketValue | This is the gross market value of all short stock positions on the trading account. |
| optionLongMarketValue | This is the gross market value of all long option positions on the trading account. |
| optionShortMarketValue | This is the gross market value of all short option positions on the trading account. |
| forexLongMarketValue | This is the gross market value of all long forex positions on the trading account. |
| forexShortMarketValue | This is the gross market value of all short forex positions on the trading account.  |
| dayTrades | This is the number of day trades that have been executed during the last five trading sessions \(including the current one\). |
| stockBuyingPower | This is the gross amount of stocks that can be purchased on this trading account,  adjusted for the available margin debt.  |
| optionBuyingPower | This is the gross amount of options that can be purchased on this trading account, adjusted for the available margin debt.  |
| forexBuyingPower | This is the gross amount of forex positions that can be opened on this trading account,  adjusted for the available margin debt.  |
| pendingCash | This is the amount of funds reserved to complete pending transactions.  |
| maintenanceMargin | This is the minimum amount of equity that must be maintained in a margin account.  |
| optionMaintenanceMargin | This is the minimum amount of equity that must be maintained for option securities. |
| openPL | This is the amount of unrealized profit or loss at the opening of the current trading session. |
| closePL | This is the amount of unrealized profit or loss at the closing of the current trading session. |
| marketValue | This is the market value of all open long and short positions. |



