# Syntax

## Place order

```
POST /v{version}/accounts/{accountId}/orders
```

### Description

This API endpoint enables you to place a new order in ETNA Trader.

### Parameters

| Type       | Name                                                         | Description                                                                                                                           | Schema                                                           | Default |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                  | string                                                           |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                      | string                                                           |         |
| **Path**   | <p><strong>accountId</strong>  <br><em>required</em></p>     | This is the unique identifier of the trading account on which a new order is to be verified.                                          | integer (int32)                                                  |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string                                                           | `"1"`   |
| **Query**  | <p><strong>currency</strong>  <br><em>optional</em></p>      | This is the currency in which the underlying security of the order is denominated.                                                    | string                                                           |         |
| **Query**  | <p><strong>exchange</strong>  <br><em>optional</em></p>      | This is the exchange on which the order should preferably be placed.                                                                  | string                                                           |         |
| **Query**  | <p><strong>userId</strong>  <br><em>optional</em></p>        | Post on behalf of another user, optional admin feature                                                                                | integer (int32)                                                  | `0`     |
| **Body**   | <p><strong>body</strong>  <br><em>required</em></p>          | This is JSON data that contains information about the new order.                                                                      | [CreateOrderResource](orders\_placeorder.md#createorderresource) |         |

### Responses

| HTTP Code | Description                                                                                                               | Schema                                               |
| --------- | ------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **200**   | JSON data with the order information is returned, indicating that the order has been successfully placed on the platform. | [OrderResource](orders\_placeorder.md#orderresource) |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation.                         | No Content                                           |
| **403**   | The provided Et-App-Key is incorrect.                                                                                     | No Content                                           |
| **422**   | A validation error occurred while processing the request.                                                                 | No Content                                           |
| **500**   | Internal server error                                                                                                     | No Content                                           |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`
