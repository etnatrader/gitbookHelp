# Syntax

## Rename watchlist.

```text
PUT /v{version}/users/{userId}/watchlists/{watchlistId}/name
```

### Description

Renames user watchlist.

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **userId**   _required_ | User identifie | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1"` |
| **Path** | **watchlistId**   _required_ | Watchlist identifier | integer \(int32\) |  |
| **Query** | **name**   _required_ | New name | string |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Watchlist id and changed name tuple | [Tuple\[Int32,String\]](../../definitions/#tuple-int-32-string) |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **409** | Conflict | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

