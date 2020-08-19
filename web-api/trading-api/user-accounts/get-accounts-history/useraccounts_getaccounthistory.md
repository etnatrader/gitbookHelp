# Syntax

## Get account history

```text
GET /v{version}/accounts/{accountId}/history
```

### Description

This API endpoint returns the historical value of a particular trading account throughout the specified period.

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | This is the authorization token that you retrieved from the first endpoint \(/token\). | string |  |
| **Header** | **Et-App-Key**   _required_ | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader. | string |  |
| **Path** | **accountId**   _required_ | This is the unique identifier of the trading account in ETNA Trader.This is the unique identifier of the trading account in ETNA Trader. | integer \(int32\) |  |
| **Path** | **version**   _required_ | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string | `"1"` |
| **Query** | **endDate**   _required_ | The end of the target period \(in UTC ticks\). | string \(date-time\) |  |
| **Query** | **startDate**   _required_ | The start of the target period \(in UTC ticks\). | string \(date-time\) |  |
| **Query** | **step**   _required_ | Obsolete. | integer \(int32\) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Returns a dictionary with historical values of the trading account | &lt; [AccountValueItem](useraccounts_getaccounthistory.md#accountvalueitem) &gt; array |
| **401** | The access level of the provided authorization token is not sufficient to perform this operation. | No Content |
| **403** | The provided Et-App-Key is incorrect. | No Content |
| **422** | A validation error occurred while processing the request. | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

