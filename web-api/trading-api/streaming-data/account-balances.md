---
description: Subscribe to changes in traders' account balances
---

# Account Balances

### Subscription Parameters <a id="Positions-Subscribe"></a>

| Parameter | Value |
| :---: | :---: |
| **Cmd** | Subscribe.txt |
| **SessionId** | Session ID from the authentication request |
| **Keys** | The ID of the trading account whose account balances you would like to retrieve |
| **EntityType** | AccountBalance |
| **HttpClientType** | WebSocket |

**Example:** `{"Cmd":"Subscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"140","EntityType":"AccountBalance","HttpClientType":"WebSocket"}`

### Unsubscription Parameters <a id="Positions-Unsubscribe"></a>

| Parameter | Value |
| :---: | :---: |
| **Cmd** | Unsubscribe.txt |
| **SessionId** | Session ID from the authentication request |
| **Keys** | The ID of the trading account whose account balances you would like to unsubscribe from |
| **EntityType** | AccountBalance |
| **HttpClientType** | WebSocket |

**Example:** { "Cmd":"Unsubscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"140","EntityType":"Position","HttpClientType":"WebSocket"}

### Message <a id="Positions-Message"></a>

In response to this request, you will receive all account-related information in the JSON format.

**Example:**

{

* "EntityType":"AccountBalance",
* "AccountId":"140",
* "CashBalance":"0",
* "PendingCash":"0",
* "PendingOrdersCount":"0",
* "Items":"\[{\"Name\":\"dayTrades\",\"Value\":0},{\"Name\":\"pendingCash\",\"Value\":0},{\"Name\":\"equityTotal\",\"Value\":1195352.7446300000},{\"Name\":\"stockLongMarketValue\",\"Value\":21501.0000000},{\"Name\":\"stockShortMarketValue\",\"Value\":69404.0000000},{\"Name\":\"optionLongMarketValue\",\"Value\":167420.000000},{\"Name\":\"optionShortMarketValue\",\"Value\":213550.0000000},{\"Name\":\"maintenanceMargin\",\"Value\":313439.900000000000},{\"Name\":\"optionMaintenanceMargin\",\"Value\":267647.50000000},{\"Name\":\"excess\",\"Value\":928042.844630000000},{\"Name\":\"stockBuyingPower\",\"Value\":928042.844630000000},{\"Name\":\"optionBuyingPower\",\"Value\":928042.844630000000},{\"Name\":\"openPL\",\"Value\":3519.0000000000},{\"Name\":\"closePL\",\"Value\":0},{\"Name\":\"netLiquidity\",\"Value\":-94033.0000000},{\"Name\":\"availableCash\",\"Value\":1262425.744630000000000},{\"Name\":\"pendingOrdersCount\",\"Value\":0}\]"

}

