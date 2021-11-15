# Syntax

## Get positions collection

```
GET /v{version}/accounts/{accountId}/positions
```

### Description

This API endpoint enables you to retrieve all outstanding positions of a particular trading account.

### Parameters

| Type       | Name                                                         | Description                                                                                                                           | Schema          | Default |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                  | string          |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                      | string          |         |
| **Path**   | <p><strong>accountId</strong>  <br><em>required</em></p>     | This is the unique identifier of the trading account whose outstanding positions need to be retrieved.                                | integer (int32) |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string          | `"1"`   |
| **Query**  | <p><strong>desc</strong>  <br><em>required</em></p>          | Is descendant                                                                                                                         | boolean         |         |
| **Query**  | <p><strong>filter</strong>  <br><em>optional</em></p>        | Positions filter query                                                                                                                | string (String) |         |
| **Query**  | <p><strong>pageNumber</strong>  <br><em>required</em></p>    | Page number                                                                                                                           | integer (int32) |         |
| **Query**  | <p><strong>pageSize</strong>  <br><em>required</em></p>      | Page size                                                                                                                             | integer (int32) |         |
| **Query**  | <p><strong>sortField</strong>  <br><em>required</em></p>     | Sort collection by field                                                                                                              | string          |         |

### Responses

| HTTP Code | Description                                                                                          | Schema                                                                                       |
| --------- | ---------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| **200**   | Successful request, JSON data containing outstanding positions of the specified account is returned. | [PagingResult\[PositionResource\]](positions\_getpositions.md#pagingresult-positionresource) |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation.    | No Content                                                                                   |
| **403**   | The provided Et-App-Key is incorrect.                                                                | No Content                                                                                   |
| **422**   | A validation error occurred while processing the request.                                            | No Content                                                                                   |
| **500**   | Internal server error                                                                                | No Content                                                                                   |

### Produces

* `application/json`
* `text/json`
