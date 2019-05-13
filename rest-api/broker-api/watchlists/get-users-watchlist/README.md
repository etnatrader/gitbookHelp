---
description: List a user's watchlists
---

# Get User's Watchlists

## Overview

This GET endpoint enables you to retrieve the list of watchlists of a user whose ID is provided in the request's path. The watchlists can be retrieved either with only information about the watchlists or including the list of securities in every watchlist.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the ID of the user whose watchlists need to be retrieved.
5. **includeSecurities** \(query\). This field indicates if the retrieved watchlists should include their corresponding stocks.

Here's the final template for this API request:

```text
apiURL/v1.0/users/{userID}/watchlists?includeSecurities=true
```

## Response

In response to this API request, you'll receive a JSON file that lists the user's watchlists:

```javascript
[
    {
        "Id": 17973,
        "Name": "My Stocks",
        "Type": "UserList",
        "CreateDate": "2019-01-14T12:27:38.52Z",
        "ModifyDate": "2019-01-14T12:27:38.52Z",
        "ReadOnly": false
    },
    {
        "Id": 2766,
        "Name": "* Top 10 Loss NYSE",
        "Type": "SystemList",
        "CreateDate": "2015-09-14T13:15:11.2979309Z",
        "ModifyDate": "2015-09-14T13:15:11.2979309Z",
        "Source": "GainLossBuilderTop10NYSELoss",
        "ReadOnly": false
    },
    {
        "Id": 2767,
        "Name": "* Top 10 Loss NASDAQ",
        "Type": "SystemList",
        "CreateDate": "2015-09-14T13:15:11.2979309Z",
        "ModifyDate": "2015-09-14T13:15:11.2979309Z",
        "Source": "GainLossBuilderTop10NSDQLoss",
        "ReadOnly": false
    },
]
```

If the _**includeSecurities**_ query parameter is set to true, the retrieved watchlists will include their corresponding securities:

```javascript
[
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
            }       
    }
]
```

### Watchlist Parameters

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal identifier of the watchlist in ETNA Trader. |
| Name | This is the name of the watchlist in ETNA Trader. |
| Type | This is the type of the watchlist. It could either be a user-created watchlist or a default watchlist provided by the system. |
| CreateDate | This is the date on which the watchlist was created. |
| ModifyDate | This is the date on which the watchlist was last modified. |
| ReadOnly | This field indicates if the watchlist is modifiable. |
| SecurityList | This is a collection of securities in the watchlist. |

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve a user's watchlists.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

### Failing to Specify the Query Parameter

It's crucial to understand that the _**includeSecurities**_ parameter must be indicated in the request; otherwise you'll receive the 404 status code and the following message:

```javascript
{
    "Message": "No HTTP resource was found that matches the request URI 'https://pub-api-et-demo-prod.etnasoft.us/api/v1.0/users/@me/watchlists'."
}
```

The following article covers the syntax for this API request in detail.

