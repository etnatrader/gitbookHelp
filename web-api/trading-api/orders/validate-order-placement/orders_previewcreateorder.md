# Syntax

## Verify placing order

```
POST /v{version}/accounts/{accountId}/preview/orders
```

### Description

This API endpoint enables you to validate the parameters of a new order before placing it on the platform.

### Parameters

| Type       | Name                                                         | Description                                                                                                                           | Schema                                                                   | Default |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                  | string                                                                   |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                      | string                                                                   |         |
| **Path**   | <p><strong>accountId</strong>  <br><em>required</em></p>     | This is the unique identifier of the trading account on which a new order is to be verified.                                          | integer (int32)                                                          |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string                                                                   | `"1"`   |
| **Query**  | <p><strong>currency</strong>  <br><em>optional</em></p>      | This is the currency in which the underlying security of the order is denominated.                                                    | string                                                                   |         |
| **Query**  | <p><strong>exchange</strong>  <br><em>optional</em></p>      | This is the exchange on which the verified order should preferably be placed.                                                         | string                                                                   |         |
| **Body**   | <p><strong>body</strong>  <br><em>required</em></p>          | Place order parameters                                                                                                                | [CreateOrderResource](orders\_previewcreateorder.md#createorderresource) |         |

### Responses

| HTTP Code | Description                                                                                                                                              | Schema                                                             |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| **200**   | JSON data with the order information is returned, indicating if the order is properly constructed (examine the isSuccessful parameter in the JSON file). | [VerifyOrderModel](orders\_previewcreateorder.md#verifyordermodel) |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation.                                                        | No Content                                                         |
| **403**   | The provided Et-App-Key is incorrect.                                                                                                                    | No Content                                                         |
| **422**   | A validation error occurred while processing the request.                                                                                                | No Content                                                         |
| **500**   | Internal server error                                                                                                                                    | No Content                                                         |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`
