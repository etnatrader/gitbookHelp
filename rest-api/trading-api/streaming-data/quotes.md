---
description: Subscribe to quotes
---

# Quotes

### Subscription Parameters <a id="Quote-Subscribe"></a>

| Parameter | Value |
| :---: | :---: |
| [**Cmd**](https://wiki.etnasoft.com/display/ET/Enumerations) | Subscribe.txt |
| **SessionId** | Session ID from the authentication request |
| **Keys** | Security ID whose quote you would like to receive |
| [**EntityType**](https://wiki.etnasoft.com/display/ET/Enumerations) | Quote |
| [**HttpClientType**](https://wiki.etnasoft.com/display/DOCS/Enumerations) | WebSocket |

**Example:** {"Cmd":"Subscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"5","EntityType":"Quote","HttpClientType":"WebSocket"}

### Unsubscription Parameters <a id="Quote-Unsubscribe"></a>

| Parameter | Value |
| :---: | :---: |
| [**Cmd**](https://wiki.etnasoft.com/display/ET/Enumerations) | Unsubscribe.txt |
| **SessionId** | Session ID from the authentication request |
| **Keys** | Security ID whose quote you would like to unsubscribe from |
| [**EntityType**](https://wiki.etnasoft.com/display/ET/Enumerations) | Quote |
| [**HttpClientType**](https://wiki.etnasoft.com/display/DOCS/Enumerations) | WebSocket |

**Example:** {"Cmd":"Unsubscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"5","EntityType":"Quote","HttpClientType":"WebSocket"}

### Response <a id="Quote-Message"></a>

In response to this request, you will receive various quote-related parameters for the target security in the JSON format.

**Example:**

**{**

* "EntityType":"Quote",
* "QuoteTypes":"0",
* "Ask":"76",
* "AskMarket":"",
* "AskTime":"08/20/2015 20:00:00",
* "AskUpdate":"False",
* "Bid":"72.9",
* "BidMarket":"",
* "BidTime":"01/01/1970 00:00:00",
* "BidUpdate":"False",
* "Last":"69",
* "Price":"69",
* "LastMarket":"",
* "Key":"738939",
* "Date":"08/11/2015 13:51:18",
* "High":"69",
* "Low":"69",
* "Open":"69",
* "Close":"69",
* "Volume":"2",
* "Change":"0",
* "ChangePc":"0",
* "Week52Low":"67.8",
* "Week52High":"125.9",
* "Dividend":"0",
* "DividendShare":"0",
* "DividendYield":"0",
* "MarketCap":"0",
* "Eps":"0",
* "DayHigh":"0",
* "DayLow":"0",
* "PeRatio":"0",
* "OpenInterest":"4",
* "TotalDailyVolume":"0",
* "AskSize":"36",
* "BidSize":"23",
* "TradeCondition":"18",
* "Beta":"0",
* "Sector":"",
* "AverageVolume3Month":"0",
* "PreviousClose":"0",
* "DontAffectCandle":"False"

**}**

