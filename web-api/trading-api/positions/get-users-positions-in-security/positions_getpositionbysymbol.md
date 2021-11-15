# Syntax

## Get positions by symbol

```
GET /v{version}/accounts/{accountId}/positions/{symbol}
```

### Description

This API endpoint enables you to retrieve a trading account’s outstanding positions in a specific security.

### Parameters

| Type       | Name                                                         | Description                                                                                                                                                                | Schema          | Default |
| ---------- | ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                                                       | string          |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                                                           | string          |         |
| **Path**   | <p><strong>accountId</strong>  <br><em>required</em></p>     | This is the unique identifier of the trading account whose outstanding positions in a security need to be retrieved.                                                       | integer (int32) |         |
| **Path**   | <p><strong>symbol</strong>  <br><em>required</em></p>        | This is the ticker symbol of the underlying security under which it is listed on the exchange.                                                                             | string          |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.                                      | string          | `"1"`   |
| **Query**  | <p><strong>currency</strong>  <br><em>optional</em></p>      | This is the currency in which the underlying security is denominated (use it if you have two securities with the same ticker but denominated in two different currencies). | string          |         |
| **Query**  | <p><strong>exchange</strong>  <br><em>optional</em></p>      | This is the exchange on which the underlying security is listed (use it if you have two securities with the same ticker but listed on two different exchanges).            | string          |         |

### Responses

| HTTP Code | Description                                                                                           | Schema                                                                           |
| --------- | ----------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| **200**   | Successful request, JSON data containing outstanding positions in the specified security is returned. | < [PositionResource](positions\_getpositionbysymbol.md#positionresource) > array |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation.     | No Content                                                                       |
| **403**   | The provided Et-App-Key is incorrect.                                                                 | No Content                                                                       |
| **422**   | A validation error occurred while processing the request.                                             | No Content                                                                       |
| **500**   | Internal server error                                                                                 | No Content                                                                       |

### Produces

* `application/json`
* `text/json`
