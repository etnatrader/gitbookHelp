# Syntax

## Create watchlist

```text
POST /v{version}/users/{userId}/watchlists
```

### Description

Creates new watchlist for specified user. If parameter includeSecurities set to true watchlists all securities will be included.

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **userId**   _required_ | User identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1"` |
| **Query** | **resultIncludeSecurities**   _required_ | Include list of wathlist securities in result model | boolean |  |
| **Body** | **body**   _required_ | Watchlist identifier | [CreateWatchlistModel](watchlists_createwatchlist.md#createwatchlistmodel) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Created watchlist | [WatchlistModel](watchlists_createwatchlist.md#watchlistmodel) |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **409** | Watchlist with same name already exists or specified securities can not be added | [WatchlistModel](watchlists_createwatchlist.md#watchlistmodel) |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`

