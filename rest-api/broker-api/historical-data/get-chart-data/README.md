---
description: Retrieve chart data for a particular security
---

# Get Comparative Chart Data

### Overview

This PUT endpoint enables you to retrieve and compare historical trading data for a set of securities. The data includes price ranges, candles, and various other non-market data. It can be used to draw comparative trading charts as demonstrated by the following screenshot:

![](../../../../.gitbook/assets/screenshot-2019-05-20-at-14.39.46.png)

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **model** \(body\). This is a JSON dictionary that contains information about the enquired securities.

#### Enquired Securities Syntax

Here's an example of the request body with the information about the enquired securities.

* Specific period:

```javascript
{"Securities":
    [{"Symbol":"MSFT","Exchange":"XNAS","Currency":"USD","Id":6},
    {"Symbol":"AAPL","Exchange":"XNAS","Currency":"USD","Id":4}],
    "SecuritiesHistorySettings":
    {
        "StartDate":1548046800,
        "EndDate":1550755974,
        "Period":"1h",
    }
}
```

* The last n data points:

```javascript
{"Securities":
    [{"Symbol":"MSFT","Exchange":"XNAS","Currency":"USD","Id":6},
    {"Symbol":"AAPL","Exchange":"XNAS","Currency":"USD","Id":4}],
    "SecuritiesHistorySettings":
    {
        "CandlesCount":10,
        "Period":"1h",
    }
}
```

* The last n data points within a specific time period:

```javascript
{"Securities":
    [{"Symbol":"MSFT","Exchange":"XNAS","Currency":"USD","Id":6},
    {"Symbol":"AAPL","Exchange":"XNAS","Currency":"USD","Id":4}],
    "SecuritiesHistorySettings":
    {
        "CandlesCount":10,
        "Period":"1h",
        "Interval":1,
    }
}
```

where:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Parameter</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Securities</td>
      <td style="text-align:left">This is an array with the enquired securities.</td>
    </tr>
    <tr>
      <td style="text-align:left">Symbol</td>
      <td style="text-align:left">This is the ticker symbol of the security under which it is listed on
        the exchange.</td>
    </tr>
    <tr>
      <td style="text-align:left">Exchange (optional)</td>
      <td style="text-align:left">This is the exchange on which the enquired security is listed.</td>
    </tr>
    <tr>
      <td style="text-align:left">Currency (optional)</td>
      <td style="text-align:left">This is the currency in which the enquired security is denominated. Possible
        values: &quot;USD&quot;.</td>
    </tr>
    <tr>
      <td style="text-align:left">Id</td>
      <td style="text-align:left">This is the internal ID of the security in ETNA Trader. You can retrieve
        this ID with <a href="../../internal-securities/get-security-info-by-ticker/">this API endpoint</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left">StartDate</td>
      <td style="text-align:left">This is the beginning of the period for which the data will be retrieved.
        The value must be provided in <a href="https://www.unixtimestamp.com/">UNIX Time Stamps</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left">EndDate</td>
      <td style="text-align:left">This is the end of the period for which the data will be retrieved. The
        value must be provided in <a href="https://www.unixtimestamp.com/">UNIX Time Stamps</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left">CandlesCount</td>
      <td style="text-align:left">This is the number of reference points for the chart. For example, if
        this parameter is set to 5, that chart will be drawn using five values.</td>
    </tr>
    <tr>
      <td style="text-align:left">Period</td>
      <td style="text-align:left">
        <p>This is the preferred time frame for the chart. Possible values:</p>
        <ul>
          <li>&quot;1m&quot;;</li>
          <li>&quot;2m&quot;;</li>
          <li>&quot;3m&quot;;</li>
          <li>&quot;5m&quot;;</li>
          <li>&quot;10m&quot;;</li>
          <li>&quot;15m&quot;;</li>
          <li>&quot;30m&quot;;</li>
          <li>&quot;1h&quot;;</li>
          <li>&quot;2h&quot;;</li>
          <li>&quot;4h&quot;;</li>
          <li>&quot;1D&quot;;</li>
          <li>&quot;1W&quot;;</li>
          <li>&quot;1M&quot;;</li>
          <li>&quot;3M&quot;;</li>
          <li>&quot;6M&quot;;</li>
          <li>&quot;1Y&quot;.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Interval</td>
      <td style="text-align:left">
        <p>This is the required time period for the specified time period. Possible
          values:</p>
        <ol>
          <li>&quot;TDY&quot;;</li>
          <li>&quot;1D&quot;;</li>
          <li>&quot;1W&quot;;</li>
          <li>&quot;1M&quot;;</li>
          <li>&quot;3M&quot;;</li>
          <li>&quot;6M&quot;;</li>
          <li>&quot;YTD&quot;;</li>
          <li>&quot;1Y&quot;;</li>
          <li>&quot;3Y&quot;;</li>
          <li>&quot;ALL&quot;.</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>{% hint style="warning" %}
All parameters must be provided in the body JSON; otherwise the chart data will not be retrieved.
{% endhint %}

Here's the final template for this API request:

```text
PUT apiURL/v1.0/history/compare
```

### Sample CURL

```text
curl -X PUT --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer token' --header 'Et-App-Key: yourEttAppKey' -d '{"Securities": [{"Symbol":"MSFT","Exchange":"XNAS","Currency":"USD","Id":6},
 {"Symbol":"AAPL","Exchange":"XNAS","Currency":"USD","Id":4}],
 "SecuritiesHistorySettings":
 { "CandlesCount":14,
 "Period":"4h"
 } }' 'https://priv-api-et-demo-prod.etnasoft.us/api/v1.0/history/compare'
```

### Response

In response to this API request, you'll receive the chart data for the list of specified securities. Notice that trading data for the Microsoft stock comes first, and after it comes the second array with the trading data for the Apple stock.

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

