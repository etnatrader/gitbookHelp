# Syntax

## Get price alerts

```
GET /v{version}/users/{userId}/pricealerts
```

### Description

This API endpoint enables you to retrieve all price alerts of a specific user.

### Parameters

| Type       | Name                                                         | Description                                                                                                                            | Schema          | Default |
| ---------- | ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                   | string          |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                       | string          |         |
| **Path**   | <p><strong>userId</strong>  <br><em>required</em></p>        | This is the internal identifier of the user whose price alerts must be retrieved.                                                      | integer (int32) |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.  | string          | `"1"`   |
| **Query**  | <p><strong>isDesc</strong>  <br><em>required</em></p>        | This is a boolean field that indicates if the returned price alerts should be sorted in  descending (true) or ascending (false) order. | boolean         |         |
| **Query**  | <p><strong>pageNumber</strong>  <br><em>required</em></p>    | This is the page number (all price alerts are split into pages).                                                                       | integer (int32) |         |
| **Query**  | <p><strong>pageSize</strong>  <br><em>required</em></p>      | This is the number of price alerts that should be retrieved from the specified page.                                                   | integer (int32) |         |
| **Query**  | <p><strong>sortBy</strong>  <br><em>required</em></p>        | Sorting field                                                                                                                          | string          |         |

### Responses

| HTTP Code | Description                                                                                       | Schema                                                                                                 |
| --------- | ------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| **200**   | Successful request, JSON data containing the user’s price alerts is returned.                     | [PagingResult\[PriceAlertInfoModel\]](pricealerts\_getpricealerts.md#pagingresult-pricealertinfomodel) |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation. | No Content                                                                                             |
| **403**   | The provided Et-App-Key is incorrect.                                                             | No Content                                                                                             |
| **422**   | A validation error occurred while processing the request.                                         | No Content                                                                                             |
| **500**   | Internal server error                                                                             | No Content                                                                                             |

### Produces

* `application/json`
* `text/json`
