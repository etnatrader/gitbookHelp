---
description: Subscribe to orders
---

# Orders

### Subscription Parameters <a id="Quote-Subscribe"></a>

| Parameter | Value |
| :---: | :---: |
| **Cmd** | Subscribe.txt |
| **SessionId** | Session ID from the authentication request |
| **Keys** | The ID of the trading account whose orders you would like to stream |
| **EntityType** | Order |
| **HttpClientType** | WebSocket |

**Example:** {"Cmd":"Subscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"140","EntityType":"Order","HttpClientType":"WebSocket"}

### Unsubscription Parameters <a id="Quote-Unsubscribe"></a>

| Parameter | Value |
| :---: | :---: |
| **Cmd** | Unsubscribe.txt |
| **SessionId** | Session ID from the authentication request |
| **Keys** | The ID of the trading account whose orders you would like to unsubscribe from |
| **EntityType** | Order |
| **HttpClientType** | WebSocket |

**Example:** {"Cmd":"Unsubscribe.txt", "SessionId":"7e83072e-09e7-43ed-91d5-f2b747bf162e", "Keys":"140","EntityType":"Order","HttpClientType":"WebSocket"}

### Response <a id="Orders-Message"></a>

In response to this request, you will receive information for all orders of the target trading account in the JSON format.

**Example:**

**{**

* "EntityType":"Order",
* "Id":"9626",
* "SecurityId":"4",
* "Quantity":"100.00000",
* "Price":"100.00000",
* "ExecutedQuantity":"0.00000",
* "LastPrice":"0.00000",
* "LastQuantity":"0.00000",
* "LeavesQuantity":"100.00000",
* "AveragePrice":"0.00000",
* "Side":"Buy",
* "CreateDate":"1439992835673",
* "Date":"1439992835673",
* "DateOffset":"10800000",
* "DateText":"",
* "TransactionDate":"1439992835798",
* "TransactionDateText":"1439992835798",
* "Status":"New",
* "ExecutionStatus":"New",
* "Type":"Limit",
* "Description":"",
* "Comment":"",
* "TimeInForce":"Day",
* "AccountId":"140",
* "StopPrice":"0.00000",
* "ExecInst":"65536",
* "ExpireDate":"1440006855798",
* "SecurityType":"CommonStock",
* "Symbol":"AAPL",
* "Exchange":"",
* "Currency":"",
* "Name":"AAPL",
* "UnderlyingSymbol":"",
* "UnderlyingId":"-1",
* "UnderlyingStrike":"0",
* "UnderlyingOptionType":"Undefined",
* "UnderlyingExpirationDate":"-62135596800000",
* "UnderlyingExpirationType":"Undefined",
* "TrailingStopAmountType":"Absolute",
* "TrailingStopAmount":"0.00000",
* "TrailingLimitAmountType":"Absolute",
* "TrailingLimitAmount":"0.00000",
* "RejectReason":"",
* "ParentId":"-1",
* "InitialType":"Limit"

**}**

