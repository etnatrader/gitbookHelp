---
description: Subscribe to positions
---

# Positions

### Subscription Parameters <a href="positions-subscribe" id="positions-subscribe"></a>

|      Parameter     |                                   Value                                  |
| :----------------: | :----------------------------------------------------------------------: |
|       **Cmd**      |                               Subscribe.txt                              |
|    **SessionId**   |                Session ID from the authentication request                |
|      **Keys**      | The ID of the trading account whose positions you would like to retrieve |
|   **EntityType**   |                                 Position                                 |
| **HttpClientType** |                                 WebSocket                                |

**Example:** { "Cmd":"Subscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"140","EntityType":"Position","HttpClientType":"WebSocket"}

### Unsubscription Parameters <a href="positions-unsubscribe" id="positions-unsubscribe"></a>

|      Parameter     |                                       Value                                      |
| :----------------: | :------------------------------------------------------------------------------: |
|       **Cmd**      |                                  Unsubscribe.txt                                 |
|    **SessionId**   |                    Session ID from the authentication request                    |
|      **Keys**      | The ID of the trading account whose positions you would like to unsubscribe from |
|   **EntityType**   |                                     Position                                     |
| **HttpClientType** |                                     WebSocket                                    |

**Example: **{ "Cmd":"Unsubscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"140","EntityType":"Position","HttpClientType":"WebSocket"}

### Message <a href="positions-message" id="positions-message"></a>

In response to this request, you will receive all position-related information in the JSON format.

**Example:**

{

* "EntityType":"Position",
* "Id":"2785",
* "AccountId":"140",
* "SecurityId":"738835",
* "CostBasis":"96000.00000",
* "DailyCostBasis":"0.00000",
* "CreateDate":"1432634060645",
* "CreateDateOffset":"-14400000",
* "ModifyDate":"1432634060645",
* "ModifyDateOffset":"-14400000",
* "Quantity":"4.00000",
* "RealizedProfitLoss":"0.00000",
* "AverageOpenPrice":"240.00000",
* "AverageClosePrice":"0.00000",
* "SecurityType":"Option",
* "Symbol":"VMSFT160117P00030000",
* "Exchange":"VIRTEX",
* "Currency":"USD",
* "Name":"VMSFT Jan 2016 30 Put",
* "CompanyName":"",
* "UnderlyingSymbol":"VMSFT",
* "UnderlyingId":"738803",
* "UnderlyingStrike":"30.00000",
* "UnderlyingOptionType":"Put",
* "UnderlyingExpirationDate":"1452988800000",
* "UnderlyingExpirationType":"Regular"

}
