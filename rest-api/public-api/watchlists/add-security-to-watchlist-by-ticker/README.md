---
description: >-
  Add a security to an existing watchlist by providing the security's ticker
  symbol
---

# Add Security to Watchlist by Ticker

### Overview

This PUT endpoint enables you to add a specific security \(by its ticker symbol\) to a specific watchlist of the user whose id is provided in the request's path. 

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the ID of the user whose particular watchlist needs to be appended by a new security.
5. **watchlistID** \(path\). This is the internal identifier of the watchlist that needs to be appended by a new security. You can retrieve the list of a user's watchlists with [this method](../get-users-watchlist/).
6. **symbolToExchange** \(body\). This is a dictionary that contains the ticker symbol of the security. 

#### Request Body Syntax

To add a new security by its ticker symbol, specify the following parameter in the request body:

```javascript
{
  "Symbol": "SNAP", //the ticker symbol of the security
}
```

Here's the final template for this API request:

```text
PUT apiURL/v1.0/users/{userID}/watchlists/{watchlistID}/securities/{securityId}
```

### Response

In response to this API request, you'll receive a JSON file with the updated watchlist. In this sample request we added the Red Hat stock to the watchlist:

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
            "Id": 738622,
            "Symbol": "DDD",
            "Description": "3D Systems Corporation Common Stock",
            "Exchange": "XNYS",
            "Currency": "USD",
            "AddedDate": "2014-01-31T15:47:57.05Z",
            "ModifyDate": "2017-12-14T08:00:26.2259193Z",
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
            "Id": 745778,
            "Symbol": "RHT",
            "Description": "Red Hat, Inc. Common Stock",
            "Exchange": "XNYS",
            "Currency": "USD",
            "AddedDate": "2016-05-04T13:32:42.4521164Z",
            "ModifyDate": "2017-12-14T08:00:43.5402374Z",
            "Type": "CommonStock",
            "Source": 0,
            "ParentId": -1,
            "OptionType": "Call",
            "ExpirationType": "Regular",
            "ExpirationDate": "0001-01-01T00:00:00Z",
            "StrikePrice": 0,
            "SeriesId": -1,
            "ContractSize": 1,
            "Precision": 2,
            "VolumePrecision": 0,
            "TickSize": 0.01,
            "MarginRate": 0
        }
    ]
}
```

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to add a particular security by its ticker symbol to a specific watchlist.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Specifying  the Security's Internal ID Instead of its Ticker Symbol

Another common mistake when making this API request is specifying the internal ID of the added security instead of its ticker symbol — for this purpose, there's a [separate API request](../../../private-api/watchlists/add-security-to-watchlist-by-id/). If you specify the security's internal ID in this request, you'll receive the 409 status code.

The following article covers the syntax for this API request in detail.

