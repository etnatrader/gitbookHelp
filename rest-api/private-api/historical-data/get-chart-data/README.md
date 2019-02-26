---
description: Retrieve chart data for a particular security
---

# Get Chart Data

### Overview

This PUT endpoint enables you to retrieve and compare historical trading data for a set of securities. This data includes price ranges, candles, and various other non-market data. 

{% hint style="warning" %}
In order to retrieve historical trading data for a set of securities, you must use an [authorization token](../../authentication/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **model** \(body\). This is a JSON dictionary that contains information about the enquired securities.

#### Enquired Securities Syntax

Here's an example of the request body with the information about the enquired securities.

```javascript
{"Securities":
	[{"Symbol":"MSFT","Exchange":"XNAS","Currency":"USD","Id":6},
	{"Symbol":"AAPL","Exchange":"XNAS","Currency":"USD","Id":4}],
	
	"SecuritiesHistorySettings":
	{
		"StartDate":1548046800,
		"EndDate":1550755974,
		"CandlesCount":10,
		"Period":"1h",
		"Interval":1,
		"IncludeNonMarketData":false
	}
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Securities | This is an array with the enquired securities. |
| Symbol | This is the ticker symbol of the security under which it is listed on the exchange. |
| Exchange | This is the exchange on which the enquired security is listed. |
| Currency | This is the currency in which the enquired security is denominated. |
| StartDate | This is the beginning of the period for which the data will be retrieved. |
| EndDate | This is the end of the period for which the data will be retrieved. |
| CandlesCount | This is the number of candles that will be retrieved for the specified time period. |
| Interval | This is the trading data interval for the specified time period.  |

{% hint style="warning" %}
All parameters must be provided in the body JSON; otherwise the chart data will not be retrieved.
{% endhint %}

Here's the final template for this API request:

```text
PUT apiURL/v1.0/history/compare
```

### Response

In response to this API request, you'll receive the chart data for the list of specified securities. Notice that trading data for Microsoft comes first, and after it comes the second array with the trading data for the Apple stock.

```javascript
[
    [ //Microsoft data starts
        {
            "IsMarket": false,
            "Volume": 1370999,
            "OpenInterest": 0,
            "Time": 1550599200,
            "DateTime": "2019-02-19T18:00:00Z",
            "Open": 108.3,
            "High": 108.3,
            "Low": 108.3,
            "Close": 0
        },
        {
            "IsMarket": false,
            "Volume": 1976587,
            "OpenInterest": 0,
            "Time": 1550602800,
            "DateTime": "2019-02-19T19:00:00Z",
            "Open": 108.4941,
            "High": 108.4941,
            "Low": 108.4941,
            "Close": 0.17922
        },
        {
            "IsMarket": false,
            "Volume": 3517858,
            "OpenInterest": 0,
            "Time": 1550606400,
            "DateTime": "2019-02-19T20:00:00Z",
            "Open": 108.24,
            "High": 108.24,
            "Low": 108.24,
            "Close": -0.0554
        },
        {
            "IsMarket": false,
            "Volume": 2044715,
            "OpenInterest": 0,
            "Time": 1550671200,
            "DateTime": "2019-02-20T14:00:00Z",
            "Open": 107.69,
            "High": 107.69,
            "Low": 107.69,
            "Close": -0.56325
        },
        {
            "IsMarket": false,
            "Volume": 2644735,
            "OpenInterest": 0,
            "Time": 1550674800,
            "DateTime": "2019-02-20T15:00:00Z",
            "Open": 107.47,
            "High": 107.47,
            "Low": 107.47,
            "Close": -0.76639
        },
        {
            "IsMarket": false,
            "Volume": 2153441,
            "OpenInterest": 0,
            "Time": 1550678400,
            "DateTime": "2019-02-20T16:00:00Z",
            "Open": 107.325,
            "High": 107.325,
            "Low": 107.325,
            "Close": -0.90028
        },
        {
            "IsMarket": false,
            "Volume": 2918433,
            "OpenInterest": 0,
            "Time": 1550682000,
            "DateTime": "2019-02-20T17:00:00Z",
            "Open": 106.56,
            "High": 106.56,
            "Low": 106.56,
            "Close": -1.60665
        },
        {
            "IsMarket": false,
            "Volume": 1588487,
            "OpenInterest": 0,
            "Time": 1550685600,
            "DateTime": "2019-02-20T18:00:00Z",
            "Open": 106.985,
            "High": 106.985,
            "Low": 106.985,
            "Close": -1.21422
        },
        {
            "IsMarket": false,
            "Volume": 2680613,
            "OpenInterest": 0,
            "Time": 1550689200,
            "DateTime": "2019-02-20T19:00:00Z",
            "Open": 107.03,
            "High": 107.03,
            "Low": 107.03,
            "Close": -1.17267
        },
        {
            "IsMarket": false,
            "Volume": 3354880,
            "OpenInterest": 0,
            "Time": 1550692800,
            "DateTime": "2019-02-20T20:00:00Z",
            "Open": 107.2,
            "High": 107.2,
            "Low": 107.2,
            "Close": -1.0157
        }
    ], //Microsoft data ends
    [ //Apple data starts
        {
            "IsMarket": false,
            "Volume": 1123672,
            "OpenInterest": 0,
            "Time": 1550599200,
            "DateTime": "2019-02-19T18:00:00Z",
            "Open": 170.62,
            "High": 170.62,
            "Low": 170.62,
            "Close": 0
        },
        {
            "IsMarket": false,
            "Volume": 1864475,
            "OpenInterest": 0,
            "Time": 1550602800,
            "DateTime": "2019-02-19T19:00:00Z",
            "Open": 171.4085,
            "High": 171.4085,
            "Low": 171.4085,
            "Close": 0.46214
        },
        {
            "IsMarket": false,
            "Volume": 2758510,
            "OpenInterest": 0,
            "Time": 1550606400,
            "DateTime": "2019-02-19T20:00:00Z",
            "Open": 170.94,
            "High": 170.94,
            "Low": 170.94,
            "Close": 0.18755
        },
        {
            "IsMarket": false,
            "Volume": 3445526,
            "OpenInterest": 0,
            "Time": 1550671200,
            "DateTime": "2019-02-20T14:00:00Z",
            "Open": 172.08,
            "High": 172.08,
            "Low": 172.08,
            "Close": 0.8557
        },
        {
            "IsMarket": false,
            "Volume": 6690456,
            "OpenInterest": 0,
            "Time": 1550674800,
            "DateTime": "2019-02-20T15:00:00Z",
            "Open": 172.72,
            "High": 172.72,
            "Low": 172.72,
            "Close": 1.23081
        },
        {
            "IsMarket": false,
            "Volume": 2261422,
            "OpenInterest": 0,
            "Time": 1550678400,
            "DateTime": "2019-02-20T16:00:00Z",
            "Open": 172.64,
            "High": 172.64,
            "Low": 172.64,
            "Close": 1.18392
        },
        {
            "IsMarket": false,
            "Volume": 2291704,
            "OpenInterest": 0,
            "Time": 1550682000,
            "DateTime": "2019-02-20T17:00:00Z",
            "Open": 171.91,
            "High": 171.91,
            "Low": 171.91,
            "Close": 0.75607
        },
        {
            "IsMarket": false,
            "Volume": 1516213,
            "OpenInterest": 0,
            "Time": 1550685600,
            "DateTime": "2019-02-20T18:00:00Z",
            "Open": 172.39,
            "High": 172.39,
            "Low": 172.39,
            "Close": 1.03739
        },
        {
            "IsMarket": false,
            "Volume": 3536329,
            "OpenInterest": 0,
            "Time": 1550689200,
            "DateTime": "2019-02-20T19:00:00Z",
            "Open": 172.25,
            "High": 172.25,
            "Low": 172.25,
            "Close": 0.95534
        },
        {
            "IsMarket": false,
            "Volume": 2975844,
            "OpenInterest": 0,
            "Time": 1550692800,
            "DateTime": "2019-02-20T20:00:00Z",
            "Open": 172.09,
            "High": 172.09,
            "Low": 172.09,
            "Close": 0.86156
        }
    ] //Apple data ends
]
```

where:

| Parameter | Description |
| :--- | :--- |
| IsMarket | This field indicates if the candle is positioned during the regular trading hours. If so, the value will be set to true; if not, the value will be set to false. |
| Volume | This is the trading volume for the specified period. |
| OpenInterest | This is the total number of outstanding derivative contracts that have not been settled yet \(only applicable for derivatives\). |
| Time | This is the date and time \(in ticks\) at which this particular candle was registered. |
| DateTime | This is the date and time \(in UTC time\) at which this particular candle was registered. |
| Open | This is the opening price of the security. |
| Close | This is the closing price of the security. |
| High | This is the highest price point for the security during the specified time period. |
| Low | This is the lowest price point for the security during the specified time period. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve trading data for a set of securities.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for retrieving trade data for a set of securities, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

#### Incorrectly Specifying the Request Body 

Another common mistake when attempting to retrieve the chart data for a set of securities is incorrectly structuring the request body. It's critical that you follow the template provided above and specify all of the required parameters. Otherwise you'll receive the 500 status code and the following error message: 

```javascript
{
    "message": "An error occurred while processing your request",
    "error": "Unexpected server error"
}
```

The following article covers the syntax for this API request in detail.

