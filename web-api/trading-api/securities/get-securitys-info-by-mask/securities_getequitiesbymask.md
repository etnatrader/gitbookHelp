# Syntax

## Get equity by mask

```
GET /v{version}/equities/lookup
```

### Description

This API endpoint enables you to retrieve a list of securities with a certain pattern by specifying a keyword that will be queried in all equities' symbol, exchange, and description fields.

### Parameters

| Type       | Name                                                         | Description                                                                                                                           | Schema          | Default |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                  | string          |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                      | string          |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string          | `"1"`   |
| **Query**  | <p><strong>count</strong>  <br><em>required</em></p>         | This is the maximum number of equities that should be retrieved.                                                                      | integer (int32) |         |
| **Query**  | <p><strong>mask</strong>  <br><em>required</em></p>          | This is the target keyword that will be searched for in all equities' symbol, exchange, and description fields.                       | string          |         |

### Responses

| HTTP Code | Description                                                                                               | Schema                                                                      |
| --------- | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| **200**   | Successful request. JSON data is returned, containing an array of securities that satisfy the given mask. | < [EquityResource](securities\_getequitiesbymask.md#equityresource) > array |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation.         | No Content                                                                  |
| **403**   | The provided Et-App-Key is incorrect.                                                                     | No Content                                                                  |
| **422**   | A validation error occurred while processing the request.                                                 | No Content                                                                  |
| **500**   | Internal server error                                                                                     | No Content                                                                  |

### Produces

* `application/json`
* `text/json`
