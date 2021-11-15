# Syntax

## Rename watchlist.

```
PUT /v{version}/users/{userId}/watchlists/{watchlistId}/name
```

### Description

This API endpoint enables you to rename an existing watchlist

### Parameters

| Type       | Name                                                         | Description                                                                                                                           | Schema          | Default |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                  | string          |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                      | string          |         |
| **Path**   | <p><strong>userId</strong>  <br><em>required</em></p>        | This is the internal identifier of the user whose watchlist needs to be renamed.                                                      | integer (int32) |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string          | `"1"`   |
| **Path**   | <p><strong>watchlistId</strong>  <br><em>required</em></p>   | This is the internal identifier of the watchlist that must be renamed.                                                                | integer (int32) |         |
| **Query**  | <p><strong>name</strong>  <br><em>required</em></p>          | This is the new name of the modified watchlist.                                                                                       | string          |         |

### Responses

| HTTP Code | Description                                                                                       | Schema                                                                       |
| --------- | ------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| **200**   | Successful request, in response you’ll receive the renamed watchlist’s ID and its new name.       | [Tuple\[Int32,String\]](watchlists\_editwatchlistname.md#tuple-int32-string) |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation. | No Content                                                                   |
| **403**   | The provided Et-App-Key is incorrect.                                                             | No Content                                                                   |
| **409**   | The watchlist couldn’t be renamed due to some conflict.                                           | No Content                                                                   |
| **422**   | A validation error occurred while processing the request.                                         | No Content                                                                   |
| **500**   | Internal server error                                                                             | No Content                                                                   |

### Produces

* `application/json`
* `text/json`
