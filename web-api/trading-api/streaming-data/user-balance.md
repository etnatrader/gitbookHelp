---
description: Subscribe to the balance summary across all accounts of a user.
---

# User Balance

### Subscription Parameters <a href="#positions-subscribe" id="positions-subscribe"></a>

|      Parameter     |                              Value                             |
| :----------------: | :------------------------------------------------------------: |
|       **Cmd**      |                          Subscribe.txt                         |
|    **SessionId**   |           Session ID from the authentication request.          |
|      **Keys**      | The ID of the user account whose balance you want to retrieve. |
|   **EntityType**   |                           UserBalance                          |
| **HttpClientType** |                            WebSocket                           |

**Example:** `{"Cmd":"Subscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"140","EntityType":"UserBalance","HttpClientType":"WebSocket"}`

### Unsubscription Parameters <a href="#positions-unsubscribe" id="positions-unsubscribe"></a>

|      Parameter     |                          Value                         |
| :----------------: | :----------------------------------------------------: |
|       **Cmd**      |                     Unsubscribe.txt                    |
|    **SessionId**   |       Session ID from the authentication request.      |
|      **Keys**      | The ID of the user you would like to unsubscribe from. |
|   **EntityType**   |                       UserBalance                      |
| **HttpClientType** |                        WebSocket                       |

**Example:** { "Cmd":"Unsubscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"140","EntityType":"UserBalance","HttpClientType":"WebSocket"}

### Message <a href="#positions-message" id="positions-message"></a>

In response to this request, you will receive all account-related information in the JSON format.

**Example:**

```javascript
{
    "EntityType": "UserBalance",
    "AccountId": "140",
    "CashBalance": "0",
    "PendingCash": "0",
    "PendingOrdersCount": "0",
    "Items": "[{\"Name\":\"cash\",\"Value\":1084543.57000000},{\"Name\":\"netCash\",\"Value\":1084543.57000000},{\"Name\":\"excess\",\"Value\":1084543.57000000},{\"Name\":\"changeAbsolute\",\"Value\":-1214.31400000000000000000},{\"Name\":\"changePercent\",\"Value\":-0.1031318408562315568923557400},{\"Name\":\"equityTotal\",\"Value\":1176224.18600000000000000000},{\"Name\":\"pendingOrdersCount\",\"Value\":0},{\"Name\":\"netLiquidity\",\"Value\":91680.61600000000000000000},{\"Name\":\"stockLongMarketValue\",\"Value\":135293.16600000000000000000},{\"Name\":\"stockShortMarketValue\",\"Value\":-43612.550000000000000000},{\"Name\":\"optionLongMarketValue\",\"Value\":0},{\"Name\":\"optionShortMarketValue\",\"Value\":0},{\"Name\":\"forexLongMarketValue\",\"Value\":0},{\"Name\":\"forexShortMarketValue\",\"Value\":0},{\"Name\":\"dayTrades\",\"Value\":0},{\"Name\":\"stockBuyingPower\",\"Value\":1084543.57},{\"Name\":\"optionBuyingPower\",\"Value\":1084543.57000000},{\"Name\":\"forexBuyingPower\",\"Value\":1084543.57},{\"Name\":\"dayTradingBuyingPower\",\"Value\":4338174.28000000},{\"Name\":\"pendingCash\",\"Value\":0},{\"Name\":\"maintenanceMargin\",\"Value\":0},{\"Name\":\"optionMaintenanceMargin\",\"Value\":0},{\"Name\":\"openPL\",\"Value\":40344.455996740000000000000000},{\"Name\":\"openPLDay\",\"Value\":-1214.31400000000000000000},{\"Name\":\"openPLPercent\",\"Value\":78.588768607114373461918599730},{\"Name\":\"closePL\",\"Value\":0.00000000},{\"Name\":\"marketValue\",\"Value\":91680.61600000000000000000},{\"Name\":\"totalPL\",\"Value\":40344.455996740000000000000000}]"
}
```
