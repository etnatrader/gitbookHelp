# Syntax

## Get user watchlist

```
GET /v{version}/users/{userId}/watchlists/{watchlistId}
```

### Description

This API endpoint enables you to retrieve information about a specific watchlist. If parameter includeSecurities is set to true, the watchlist’s securities will also be included in the response.

### Parameters

| Type       | Name                                                             | Description                                                                                                                           | Schema          | Default |
| ---------- | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p>     | This is the authorization token that you retrieved from the first endpoint (/token).                                                  | string          |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>        | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                      | string          |         |
| **Path**   | <p><strong>userId</strong>  <br><em>required</em></p>            | This is the internal identifier of the user whose watchlist’s information needs to be retrieved.                                      | integer (int32) |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>           | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string          | `"1"`   |
| **Path**   | <p><strong>watchlistId</strong>  <br><em>required</em></p>       | This is the internal identifier of the watchlist whose information needs to be retrieved.                                             | integer (int32) |         |
| **Query**  | <p><strong>includeSecurities</strong>  <br><em>required</em></p> | This boolean parameter indicates if the list of securities in the watchlist should be returned in the request response.               | boolean         |         |

### Responses

| HTTP Code | Description                                                                                                                                                                        | Schema                                                       |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| **200**   | Successful request, JSON data containing the information about the new watchlist is returned (along with its securities if the resultIncludeSecurities parameter was set to true). | [WatchlistModel](watchlists\_getwatchlist.md#watchlistmodel) |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation.                                                                                  | No Content                                                   |
| **403**   | The provided Et-App-Key is incorrect.                                                                                                                                              | No Content                                                   |
| **409**   | The watchlist does not exist.                                                                                                                                                      | No Content                                                   |
| **422**   | A validation error occurred while processing the request.                                                                                                                          | No Content                                                   |
| **500**   | Internal server error                                                                                                                                                              | No Content                                                   |

### Produces

* `application/json`
* `text/json`
