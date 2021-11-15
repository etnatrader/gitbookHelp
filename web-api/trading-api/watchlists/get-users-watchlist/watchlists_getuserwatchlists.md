# Syntax

## Get user watchlists

```
GET /v{version}/users/{userId}/watchlists
```

### Description

This API endpoint enables you to retrieve all watchlists of a particular user. If parameter includeSecurities is set to true, the watchlists’ securities will also be included in the response.

### Parameters

| Type       | Name                                                             | Description                                                                                                                           | Schema          | Default |
| ---------- | ---------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p>     | This is the authorization token that you retrieved from the first endpoint (/token).                                                  | string          |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>        | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                      | string          |         |
| **Path**   | <p><strong>userId</strong>  <br><em>required</em></p>            | This is the internal identifier of the user whose watchlists need to be retrieved.                                                    | integer (int32) |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>           | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string          | `"1"`   |
| **Query**  | <p><strong>includeSecurities</strong>  <br><em>required</em></p> | This boolean parameter indicates if the list of securities in the watchlists should be returned in the request response.              | boolean         |         |

### Responses

| HTTP Code | Description                                                                                                                                                                                            | Schema                                                                      |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------- |
| **200**   | Successful request, JSON data containing the information about the user’s watchlists is returned (along with their corresponding securities if the resultIncludeSecurities parameter was set to true). | < [WatchlistModel](watchlists\_getuserwatchlists.md#watchlistmodel) > array |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation.                                                                                                      | No Content                                                                  |
| **403**   | The provided Et-App-Key is incorrect.                                                                                                                                                                  | No Content                                                                  |
| **422**   | A validation error occurred while processing the request.                                                                                                                                              | No Content                                                                  |
| **500**   | Internal server error                                                                                                                                                                                  | No Content                                                                  |

### Produces

* `application/json`
* `text/json`
