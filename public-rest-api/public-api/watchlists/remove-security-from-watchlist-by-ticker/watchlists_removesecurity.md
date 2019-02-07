# Syntax

## Removes security.

```text
DELETE /v{version}/users/{userId}/watchlists/{watchlistId}/securities
```

### Description

Removes security from watchlist by security symbol and exchange.

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **userId**   _required_ | User identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1"` |
| **Path** | **watchlistId**   _required_ | Watchlist identifier | integer \(int32\) |  |
| **Body** | **body**   _required_ | Security symbol and exchange | [SecuritySignature](watchlists_removesecurity.md#securitysignature) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Changed watchlist with securities | [WatchlistModel](watchlists_removesecurity.md#watchlistmodel) |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **409** | Security was not found | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`

