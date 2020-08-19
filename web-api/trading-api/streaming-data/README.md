---
description: Subscribe to quote streamers
---

# Streaming Data

### Introduction

The Streaming APIs give developers low-latency access to streams of data. A proper implementation of a streaming client will include pushed messages indicating quotes, order, positions and other events have occurred, without any of the overhead associated with polling a REST endpoint.

### Connecting

To create a new connection to the streamer following conditions must be satisfied:

* User should be authorized in the system.
* Session ID should be valid.
* User ID should be valid.

### Request <a id="WebSocketsAPI-Request"></a>

#### Option 1: Via Login and Password

**GET** &lt;**URL&gt;СreateSession.txt**?User=**&lt;UserLogin&gt;**&Password=**&lt;UserPassword&gt;**&HttpClientType=**WebSocket**

Example: [**ws://etnatrader.etnasoft.us:9999**](ws://etnatrader.etnasoft.us:9999/CreateSession.txt?User=)\*\*\*\*[**/CreateSession.txt?User=trader&Password=trader&HttpClientType=WebSocket**](wss://etnatrader-dev.etnasoft.us:9999/CreateSession.txt?User=trader&Password=trader&HttpClientType=WebSocket)\*\*\*\*

| Param | Description |
| :--- | :--- |
| **UserLogin** | The is the user's login. |
| **UserPassword** | This is the user's password.  |

#### Option 2: Via Streamer Session ID

**GET** &lt;**URL&gt;**?User=**&lt;UserID&gt;**:**&lt;SessionID&gt;**&Password=**&lt;StreamerSessionID&gt;**&HttpClientType=**WebSocket**

**Example:** [ws://etnatrader.etnasoft.us:9999/CreateSession.txt?User=](ws://etnatrader.etnasoft.us:9999/CreateSession.txt?User=)**someUser:sessionID**&Password=**StreamerSessionID**&HttpClientType=**WebSocket**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Param</th>
      <th style="text-align:left">JSON Key</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>UserID</b>
      </td>
      <td style="text-align:left">Result.UserId</td>
      <td style="text-align:left">User&apos;s identifier</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>SessionID</b>
      </td>
      <td style="text-align:left">Result.SessionID</td>
      <td style="text-align:left">User&apos;s session identifier.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>StreamerSessionID</b>
      </td>
      <td style="text-align:left">
        <p>For trade data streamer: Result.DataAddresses.SessionID</p>
        <p>For quote data streamer: Result.QuoteAddresses.SessionID</p>
      </td>
      <td style="text-align:left">Session identifier for the target streamer.</td>
    </tr>
  </tbody>
</table>

### Response <a id="WebSocketsAPI-Response"></a>

| Param | Value | Description |
| :--- | :--- | :--- |
| **Cmd** | CreateSession.txt | Create a new connection |
| **StatusCode** | Connection Status | — |
| **SessionID** | User's session identifier | — |

**Example:** {"Cmd":"CreateSession.txt", "StatusCode":"Ok", "SessionId":"6210cb85-c6bb-44f1-a53b-0e43669bd6f4" }

**Example 2:** {"Cmd":"CreateSession.txt", "StatusCode":"Error"}

## Subscribe/Unsubscribe <a id="WebSocketsAPI-Subscribe/Unsubscribe"></a>

Used for start/stop receiving data changes. Once applications subscribe to a streaming endpoint, they are delivered a feed of data, without needing to worry about polling or REST API rate limits.

| Param | Type | Description |
| :--- | :--- | :--- |
| **Cmd** | String | Command |
| **SessionId** | String | User's session identifier from the authentication response. |
| **Keys** | String | One or several subscription keys, each separated by “;” |
| **EntityType** | String | Entity type identifier. It's equal to the key property from entity definition section on the streamer's side. |
| **HttpClientType** | String | Client type. |

### Streamer Types

ETNA Trader provides two types of streamers: 

1. Quote data streamer 
2. Trade data streamer.

Each streamer is accessible through its own separate port in your environment. Quote data streamer is responsible for streaming quotes, trades, and market depth. Trade data streamer, on the other hand, is responsible for streaming other data like watchlists, positions, orders, account balances, price alerts, etc.

### Streamer Configuration

While the current implementation of data streaming includes only several data types that can be retrieved in real-time, ETNA Trader also provides custom configurations of streamers that build on top of the existing functionality. For example, if you would like to stream positions across several trading accounts or account information across the whole environment, you will need a separate configuration of the streamer. To learn more about the degree to which the default functionality can be extended, contact our [support team](mailto:support@etnatrader.com).

### Streamer Performance

ETNA Trader's streaming API is built to sustain a high load of user subscriptions. Data throughput will vary depending on the type of data to which the user subscribes \(quote streaming being the most resource intensive\). Traders may have large watchlists with dozens of different securities and each security must be displayed along with a real-time quote for the best user experience. That raises the question of how many simultaneous quotes the streamer can process. Most of the time the streamer can meet the requirements of the heftiest watchlists; however, our internal tests have indicated that the performance of a streamer may somewhat deteriorate after subscribing to more than 100 quotes.

