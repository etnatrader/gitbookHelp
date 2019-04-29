# Syntax

## Get positions by symbol

```text
GET /v{version}/accounts/{accountId}/positions/{symbol}
```

### Description

Retrieve all positions by specified symbol

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **accountId**   _required_ | Account identifier | integer \(int32\) |  |
| **Path** | **symbol**   _required_ | Security symbol | string |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Query** | **currency**   _optional_ | Target currency, optional | string |  |
| **Query** | **exchange**   _optional_ | Target exchange, optional | string |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Target symbol positions | &lt; [PositionResource](../../definitions/#positionresource) &gt; array |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

