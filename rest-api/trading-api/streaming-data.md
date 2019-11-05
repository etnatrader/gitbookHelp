---
description: Subscribe to quote streamers
---

# Streaming Data

### Introduction

The Streaming APIs give developers low latency access to stream of data. A proper implementation of a streaming client will be pushed messages indicating quotes, order, positions and other events have occurred, without any of the overhead associated with polling a REST endpoint.

### Connecting

To create a new connection to the streamer following conditions must be satisfied:

* User should be authorized in the system.
* Session ID should be valid.
* User ID should be valid.

### Request <a id="WebSocketsAPI-Request"></a>

**GET** &lt;**URL&gt;**?User=**&lt;UserID&gt;**:**&lt;SessionID&gt;**&Password=**&lt;StreamerSessionID&gt;**&HttpClientType=**WebSocket**

**Example:** [ws://etnatrader.etnasoft.us:9999/CreateSession.txt?User=](ws://etnatrader.etnasoft.us:9999/CreateSession.txt?User=)**someUser**&Password=**somePassword**&HttpClientType=**WebSocket**

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
      <td style="text-align:left"><b>SessionID (optional)</b>
      </td>
      <td style="text-align:left">Result.SessionID</td>
      <td style="text-align:left">User&apos;s session identifier. You can skip this parameter and provide
        only <b>UserID</b> if you don&apos;t have an active session.</td>
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
</table>### Response <a id="WebSocketsAPI-Response"></a>

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
| **SessionId** | String | User's session identifier |
| **Keys** | String | one or few subscription keys, in a case of multiple keys they should be separated by “;” |
| **EntityType** | String | entity type identificator, equals to key property from entity definition section on streamer side. |
| **HttpClientType** | String | type of client. |

