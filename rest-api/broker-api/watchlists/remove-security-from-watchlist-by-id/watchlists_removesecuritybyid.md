# Syntax

## Remove security by Id.

```text
DELETE /v{version}/users/{userId}/watchlists/{watchlistId}/securities/{securityId}
```

### Description

Removes security to watchlist by security Id.

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **securityId**   _required_ | Security identifier | integer \(int32\) |  |
| **Path** | **userId**   _required_ | User identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Path** | **watchlistId**   _required_ | Watchlist identifier | integer \(int32\) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Changed watchlist with securities | [WatchlistModel]() |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **409** | Conflict | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

