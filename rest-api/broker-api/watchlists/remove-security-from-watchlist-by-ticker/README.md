---
description: Remove a security from a watchlist by specifying the security's ticker symbol
---

# Remove Security from Watchlist by Ticker

## Overview

This DELETE endpoint enables you to remove a specific security \(by its ticker symbol\) from a specific watchlist of the user whose id is provided in the request's path.

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the ID of the user whose particular watchlist needs to be have one security removed.
5. **watchlistID** \(path\). This is the internal identifier of the watchlist from which a security must be removed. You can retrieve the list of a user's watchlists with [this method](../get-users-watchlist/).
6. **symbolToExchange** \(body\). This is a dictionary that contains the ticker symbol of the security that must be removed from the specified watchlist. 

### Request Body Syntax

To remove a security from a watchlist by its ticker symbol, specify the following parameter in the request body:

```javascript
{
  "Symbol": "SNAP", //the ticker symbol of the security
}
```

Here's the final template for this API request:

```text
DELETE apiURL/v1.0/users/{userID}/watchlists/{watchlistID}/securities/{securityId}
```

## Response

In response to this API request, you'll receive a JSON file with the updated watchlist. In this sample request we removed the Google stock from the watchlist 17973.

```javascript
{
    "Id": 17973,
    "Name": "My Stocks",
    "Type": "UserList",
    "CreateDate": "2019-01-14T12:27:38.52Z",
    "ModifyDate": "2019-01-14T12:27:38.52Z",
    "ReadOnly": false,
    "SecurityList": [
        {
            "Id": 6,
            "Symbol": "MSFT",
            "Description": "Microsoft Corporation",
            "Exchange": "XNAS",
            "Currency": "USD",
            "AddedDate": "2012-11-29T16:05:43.997Z",
            "ModifyDate": "2017-12-14T08:00:13.5446736Z",
            "Type": "CommonStock",
            "Source": 0,
            "ParentId": -1,
            "OptionType": "Undefined",
            "ExpirationType": "Undefined",
            "ExpirationDate": "0001-01-01T00:00:00Z",
            "StrikePrice": 0,
            "SeriesId": -1,
            "ContractSize": 1,
            "Precision": 2,
            "VolumePrecision": 0,
            "TickSize": 0.01,
            "MarginRate": 0
        },
        {
            "Id": 2829,
            "Symbol": "FB",
            "Description": "Facebook, Inc.",
            "Exchange": "XNAS",
            "Currency": "USD",
            "AddedDate": "2012-11-29T16:08:15.947Z",
            "ModifyDate": "2017-12-14T08:00:09.171586Z",
            "Type": "CommonStock",
            "Source": 0,
            "ParentId": -1,
            "OptionType": "Undefined",
            "ExpirationType": "Undefined",
            "ExpirationDate": "0001-01-01T00:00:00Z",
            "StrikePrice": 0,
            "SeriesId": -1,
            "ContractSize": 1,
            "Precision": 2,
            "VolumePrecision": 0,
            "TickSize": 0.01,
            "MarginRate": 0
        },
        {
            "Id": 9041,
            "Symbol": "YHOO",
            "Description": "Yahoo! Inc.",
            "Exchange": "XNAS",
            "Currency": "USD",
            "AddedDate": "2012-11-29T16:08:15.96Z",
            "ModifyDate": "2017-06-20T07:00:14.4306455Z",
            "Type": "CommonStock",
            "Source": 0,
            "ParentId": -1,
            "OptionType": "Undefined",
            "ExpirationType": "Undefined",
            "ExpirationDate": "0001-01-01T00:00:00Z",
            "StrikePrice": 0,
            "SeriesId": -1,
            "ContractSize": 1,
            "Precision": 2,
            "VolumePrecision": 0,
            "TickSize": 0.01,
            "MarginRate": 0
        }]
}
```

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to remove a particular security by its ticker symbol from a specific watchlist.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

### Specifying  the Security's Internal ID Instead of its Ticker Symbol

Another common mistake when making this API request is specifying the internal ID of the added security instead of its ticker symbol — for this purpose, there's a [separate API request](../../../trading-api/watchlists/remove-security-from-watchlist-by-id/). If you specify the security's internal ID in this request, you'll receive the 409 status code.

The following article covers the syntax for this API request in detail.

