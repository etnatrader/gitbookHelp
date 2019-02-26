---
description: Fetch information about a specific watchlist
---

# Get Specific Watchlist

### Overview

This GET endpoint enables you to retrieve information about a specific watchlist of a user whose internal ID is provided in the request's path. The watchlist can be retrieved either with only information about the watchlists or including the list of securities in every watchlist. 

{% hint style="warning" %}
In order to retrieve information about a particular watchlist, you must use an [authorization token](../../authentication/requesting-tokens/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the ID of the user whose particular watchlist need to be retrieved.
5. **watchlistID** \(path\). This is the internal identifier of the watchlist whose information must be retrieved.
6. **includeSecurities** \(query\). This field indicates if the retrieved watchlist should include its corresponding stocks.

Here's the final template for this API request:

```text
apiURL/v1.0/users/{userID}/watchlists/{watchlistID}?includeSecurities=true
```

### Response

In response to this API request, you'll receive a JSON file that contains information about the enquired watchlist.

```javascript
{
  "Id": 17973,
  "Name": "My Stocks",
  "Type": "UserList",
  "CreateDate": "2019-01-14T12:27:38.52Z",
  "ModifyDate": "2019-01-14T12:27:38.52Z",
  "ReadOnly": false
}
```

If the _**includeSecurities**_ query parameter is set to true, the retrieved watchlist will include its corresponding securities:

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
    },
    {
      "Id": 678823,
      "Symbol": "C",
      "Description": "Citigroup, Inc. Common Stock",
      "Exchange": "XNYS",
      "Currency": "USD",
      "AddedDate": "2012-11-30T07:22:20.663Z",
      "ModifyDate": "2017-12-14T08:00:24.0768768Z",
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
      "Id": 684344,
      "Symbol": "QQQ",
      "Description": "Invesco QQQ Trust, Series 1",
      "Exchange": "XNAS",
      "Currency": "USD",
      "AddedDate": "2012-11-30T07:22:20.67Z",
      "ModifyDate": "2018-05-29T07:00:05.8792207Z",
      "Type": "ETF",
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
      "Id": 685714,
      "Symbol": "TSLA",
      "Description": "Tesla, Inc. ",
      "Exchange": "XNAS",
      "Currency": "USD",
      "AddedDate": "2012-11-30T07:22:20.67Z",
      "ModifyDate": "2017-12-14T08:00:18.6797687Z",
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
      "Id": 693649,
      "Symbol": "DIA",
      "Description": "SPDR Dow Jones Industrial Average ETF",
      "Exchange": "ARCX",
      "Currency": "USD",
      "AddedDate": "2013-02-05T14:49:51.137Z",
      "ModifyDate": "2017-12-14T08:00:26.7449241Z",
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
      "Id": 694510,
      "Symbol": "SPY",
      "Description": "SPDR S&P 500",
      "Exchange": "ARCX",
      "Currency": "USD",
      "AddedDate": "2013-02-05T14:49:51.137Z",
      "ModifyDate": "2017-12-14T08:00:45.8162954Z",
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
    }
  ]
}
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

Here are some of the common mistakes that developers make when attempting to retrieve a specific watchlist. 

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for retrieving a specific watchlist, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

#### Failing to Specify the Query Parameter

It's crucial to understand that the _**includeSecurities**_ parameter must be indicated in the request; otherwise you'll receive the 404 status code and the following message:

```javascript
{
    "Message": "No HTTP resource was found that matches the request URI 'https://pub-api-et-demo-prod.etnasoft.us/api/v1.0/users/@me/watchlists'."
}
```

The following article covers the syntax for this API request in detail.

