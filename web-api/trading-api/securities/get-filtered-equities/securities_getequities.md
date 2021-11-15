# Syntax

## Get equities

```
GET /v{version}/equities
```

### Description

This API endpoint enables you to retrieve a collection of equities filtered by a specific query.

### Parameters

| Type       | Name                                                         | Description                                                                                                                              | Schema          | Default |
| ---------- | ------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                     | string          |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                         | string          |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.    | string          | `"1"`   |
| **Query**  | <p><strong>desc</strong>  <br><em>required</em></p>          | This is a boolean field that indicates if the returned equities should be sorted in the descending (true) or ascending (false) order.    | boolean         |         |
| **Query**  | <p><strong>filter</strong>  <br><em>optional</em></p>        | This is a filter query used to retrieve only those equities that satisfy the conditions of the query.                                    | string (String) |         |
| **Query**  | <p><strong>pageNumber</strong>  <br><em>required</em></p>    | This is the page number (all equities are split into pages).                                                                             | integer (int32) |         |
| **Query**  | <p><strong>pageSize</strong>  <br><em>required</em></p>      | This is the number of equities that should be retrieved from the specified page.                                                         | integer (int32) |         |
| **Query**  | <p><strong>sortField</strong>  <br><em>required</em></p>     | This is the field by which all equities should be sorted. For example, if you specify Type, first you'll receive stocks, then ETFs, etc. | string          |         |

### Responses

| HTTP Code | Description                                                                                       | Schema                                                                |
| --------- | ------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| **200**   | Successful request, JSON data containing the collection of filtered equities is returned.         | < [EquityResource](securities\_getequities.md#equityresource) > array |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation. | No Content                                                            |
| **403**   | The provided Et-App-Key is incorrect.                                                             | No Content                                                            |
| **422**   | A validation error occurred while processing the request.                                         | No Content                                                            |
| **500**   | Internal server error                                                                             | No Content                                                            |

### Produces

* `application/json`
* `text/json`
