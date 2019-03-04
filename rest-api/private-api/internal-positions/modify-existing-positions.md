---
description: Updated an existing position
---

# Modify Existing Positions

### Overview

This PUT endpoint enables you to modify an existing position on a user's trading account, bypassing the regular order modification mechanism.  Every once in a while some breakdown takes place on the exchange or in ETNA Trader, forcing you to use our Back Office to manually modify an existing position on the user's trading account. This procedure must be carried out with caution so as to prevent any conflicts.

{% hint style="warning" %}
In order to modify an existing position, you must use an [authorization token](../authentication/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **recalculate** \(query\). This is a boolean field that indicates if the account's cash should be recalculated after modifying the position.
5. **position** \(body\). This is a JSON file that contains information about the modified position. 

#### New Position Syntax

Following is a sample of the request body that must be sent in order to modify an existing position . The first four parameters — **AccountId**, **SecurityId**, **Id**, and **Quantity** — are mandatory while the rest can be configured depending on the circumstances. Because you intend to modify an existing position, you must  provide the **Id** parameter which represents the identifier of the modified position.

```javascript
{
  "AccountId": 6688, //required
  "SecurityId": 4 ,  //required
  "Quantity": 107, //required
  "Id" : 701, //required
  "CostBasis": 0,
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
| DailyCloseProfitLoss | This is the unrealized profit or loss of the position measured against the last closing price. |
| ExcessChanges | This is an internal field in ETNA Trader and it shouldn't be used by third parties. |
| DayQuantity | This is an internal field in ETNA Trader and it shouldn't be used by third parties. |
| OpenQuantity | This is an internal field in ETNA Trader and it shouldn't be used by third parties. |
| LastLot | This is an internal field in ETNA Trader and it shouldn't be used by third parties. |
| Unsettled | This is an internal field in ETNA Trader and it shouldn't be used by third parties. |
| UnsettledDate | This is an internal field in ETNA Trader and it shouldn't be used by third parties. |
| MarginType | This is the trading account type. Possible values: **Cash**, **Margin**, **DayTrader**. |
| Locked | This is an internal field in ETNA Trader and it shouldn't be used by third parties. |
| SpreadQuantity | This is an internal field in ETNA Trader and it shouldn't be used by third parties. |

Here's the final template for this API request:

```text
PUT apiURL/v1.0/positions  
```

### Response

In response to this API request, you'll receive a JSON file with the information about the updated position.

```javascript
{
  "Id": 22730,
  "AccountId": 6688,
  "SecurityId": 4,
  "CostBasis": 0,
  "DailyCostBasis": 0,
  "CreateDate": "0001-01-01T00:00:00Z",
  "ModifyDate": "0001-01-01T00:00:00Z",
  "Quantity": 107,
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
  "UnsettledDate": "0001-01-01T00:00:00Z",
  "MarginType": "Empty",
  "Locked": false,
  "SpreadQuantity": 0
}
```

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to modify an existing position, bypassing the regular order replacement mechanism.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for modifying existing positions, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

#### Failing to Specify the Query Parameters

It's crucial to understand that the _**pageSize, pageNumber, isDesc, and sortBy**_ parameters must be provided in the request; otherwise you'll receive the 404 status code and the following message:

```javascript
{
    "Error": {
        "Code": "UnsupportedApiVersion",
        "Message": "The requested resource with API version '1.0' does not support HTTP method 'GET'."
    }
}
```

The following article covers the syntax for this API request in detail.

