---
description: >-
  Remove a security from a watchlist by providing the security's internal
  identifier
---

# Remove Security from Watchlist by ID

### Overview

This DELETE endpoint enables you to remove a particular security from a particular watchlist by providing the security's ID in the request's path. 

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **watchlistID** \(path\). This is the ID of the watchlist from which a security must be removed.
5. **userID** \(path\). This is the ID of the user whose particular watchlist should have the specified security removed.
6. **securityID** \(path\). This is the ID of the security that must be removed from a particular watchlist. You can fetch the ID of a particular security with [this method](../../securities/get-securitys-info-by-its-ticket-symbol/).

The final template for this request is as follows:

```text
DELETE apiURL/v1.0/users/{userID}/watchlists/{watchlistID}/securities/{securityID}
```

### Response

In response to this API request, you'll receive the updated watchlist with the specified security removed. In this example we've removed the Apple stock from a tech-oriented watchlist.

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
```

#### Watchlist Parameters

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal identifier of the watchlist in ETNA Trader. |
| Name | This is the name of the watchlist in ETNA Trader. |
| Type | This is the type of the watchlist. It could either be a user-created watchlist or a default watchlist provided by the system. |
| CreateDate | This is the date on which the watchlist was created. |
| ModifyDate | This is the date on which the watchlist was last modified. |
| ReadOnly | This field indicates if the watchlist is modifiable. |
| SecurityList | This is a collection of securities in the watchlist. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to remove a particular security from a watchlist.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Specifying  the Security's Ticker Symbol Instead of its Internal ID

Another common mistake when making this API request is specifying the ticker symbol of the to-be-added security instead of its internal ID — for this purpose, there's a [separate API request](../remove-security-from-watchlist-by-ticker/). If you specify the security's ticker symbol in this request, you'll receive the 400 status code and the following error message:

```javascript
{
    "Message": "The request is invalid."
}
```

The following article covers the syntax for this API request in detail.

