---
description: Fetch information about a particular equity by providing its internal ID
---

# Get Equity Info by Internal ID

## Overview

This GET endpoint enables you to retrieve information about a particular security by specifying its internal ID in the request's path. This information is not retrieved directly from the exchange; rather, it's the information about the security that is specific to ETNA Trader.

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **ID** \(path\). This is the internal ID of the security whose information you'd like to retrieve. 

Here's the final template for this API request:

```text
GET apiURL/v1.0/equities/4 //Apple Inc.
```

## Response

In response to this API request, you'll receive a JSON file with all the information about the enquired security:

```javascript
{
    "Id": 4,
    "Symbol": "AAPL",
    "Description": "Apple Inc.",
    "Exchange": "XNAS",
    "Currency": "USD",
    "AddedDate": "2012-11-29T16:05:43.993Z",
    "ModifyDate": "2018-12-10T08:00:22.2867686Z",
    "Type": "CommonStock",
    "Precision": 2,
    "VolumePrecision": 0,
    "TickSize": 0.01,
    "Enabled": true,
    "AllowTrade": true,
    "AllowMargin": true,
    "AllowShort": true
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal ID of the security in ETNA Trader. |
| Symbol | This is the ticker symbol under which the security is listed on the exchange. |
| Description | Usually this is the full name of the underlying company. |
| Exchange | This is the exchange on which the security is listed. |
| Currency | This is the currency in which the security is denominated. |
| AddedDate | This is the date on which the security was added to the database. |
| ModifyDate | This is the date in which the security's information was last modified. |
| Type | This is the type of the security. |
| Precision | This is the number of decimal places in the security's price. |
| VolumePrecision | This is the number of decimal places in the security's trading volume \(might be useful for cryptocurrencies\). |
| TickSize | This is the minimum price change of the security. For example, if this property equals 0.01 for AAPL, the minimum price change for AAPL is 0.01 \(150.67 —&gt; 150.68, but not 150.675\). For securities with the market price of less than $1, the TickSize is equal to 0.0001. |
| Enabled | This field indicated if the security is enabled and can be traded by users. |
| AllowTrade | This field indicates is the security if permitted for trading. |
| AllowMargin | This field indicates if the security is allowed to be traded on margin. |
| AllowShort | This field indicates if the security can be sold short. |

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve information about a particular security by its ticker.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

The following article covers the syntax for this API request in detail.

