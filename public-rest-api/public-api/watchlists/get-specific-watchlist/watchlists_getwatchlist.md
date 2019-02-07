# Syntax

## Get user watchlist

```text
GET /v{version}/users/{userId}/watchlists/{watchlistId}
```

### Description

Retrieves specified watchlist. If parameter includeSecurities set to true watchlist all securities will be included.

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **userId**   _required_ | User identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1"` |
| **Path** | **watchlistId**   _required_ | Watchlist identifier | integer \(int32\) |  |
| **Query** | **includeSecurities**   _required_ | Include list of wathlist securities in result model | boolean |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Wathlist | [WatchlistModel](watchlists_getwatchlist.md#watchlistmodel) |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **409** | Watchlist does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

