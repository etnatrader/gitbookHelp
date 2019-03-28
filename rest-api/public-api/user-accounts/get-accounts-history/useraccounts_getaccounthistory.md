# Syntax

## Get account history

```text
GET /v{version}/accounts/{accountId}/history
```

### Description

Provides account history items specified by query string

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **accountId**   _required_ | Account identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Query** | **endDate**   _required_ | End date in utc ticks | string \(date-time\) |  |
| **Query** | **startDate**   _required_ | Start date in utc ticks | string \(date-time\) |  |
| **Query** | **step**   _required_ | Account value items count per request | integer \(int32\) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Array of account history items | &lt; [AccountValueItem](../../definitions.md#accountvalueitem) &gt; array |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

