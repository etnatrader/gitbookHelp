---
description: >-
  Add a security to an existing watchlist by providing the security's internal
  identifier
---

# Add Security to Watchlist by ID

## Overview

This PUT endpoint enables you to add a specific security to a specific watchlist of the user whose id is provided in the request's path.

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the ID of the user whose particular watchlist needs to be appended by a new security.
5. **watchlistID** \(path\). This is the internal identifier of the watchlist that needs to be appended by a new security. You can retrieve the list of a user's watchlists with [this method](../get-users-watchlist/).
6. **securityID** \(path\). This is the internal identifier if the security that needs to be added to the watchlist. You can find the ID of a particular security with [this method](https://github.com/etnatrader/gitbookHelp/tree/6c42ded62b3c38323fe9c79d5284ef0387d6f690/rest-api/broker-api/securities/get-securitys-info-by-its-ticket-symbol/README.md).

Here's the final template for this API request:

```text
PUT apiURL/v1.0/users/{userID}/watchlists/{watchlistID}/securities/{securityId}
```

## Response

In response to this API request, you'll receive a JSON file with the updated watchlist. In this sample request we added the Ford stock to the watchlist:

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
            "Id": 4,
            "Symbol": "AAPL",
            "Description": "Apple Inc.",
            "Exchange": "XNAS",
            "Currency": "USD",
            "AddedDate": "2012-11-29T16:05:43.993Z",
            "ModifyDate": "2018-12-10T08:00:22.2867686Z",
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
            "Id": 5,
            "Symbol": "GOOG",
            "Description": "Alphabet Inc.",
            "Exchange": "XNAS",
            "Currency": "USD",
            "AddedDate": "2012-11-29T16:05:43.993Z",
            "ModifyDate": "2017-12-14T08:00:10.1826129Z",
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
            "Id": 680410,
            "Symbol": "F",
            "Description": "Ford Motor Company Common Stock",
            "Exchange": "XNYS",
            "Currency": "USD",
            "AddedDate": "2012-11-30T07:22:20.667Z",
            "ModifyDate": "2017-12-14T08:00:29.2429719Z",
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

    ]
}
```

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to add a particular security to a specific watchlist.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

### Specifying  the Security's Ticker Symbol Instead of its Internal ID

Another common mistake when making this API request is specifying the ticker symbol of the added security instead of its internal ID — for this purpose, there's a [separate API request](../add-security-to-watchlist-by-ticker/). If you specify the security's ticker symbol in this request, you'll receive the 400 status code and the following error message:

```javascript
{
    "Message": "The request is invalid."
}
```

The following article covers the syntax for this API request in detail.

