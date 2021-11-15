# Syntax

## Get equity by symbol

```
GET /v{version}/equities/{symbol}
```

### Description

This API endpoint enables you to retrieve detailed information about a particular equity by providing its ticker symbol under which it’s listed on the exchange.

### Parameters

| Type       | Name                                                         | Description                                                                                                                                                 | Schema | Default |
| ---------- | ------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ------ | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                                        | string |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                                            | string |         |
| **Path**   | <p><strong>symbol</strong>  <br><em>required</em></p>        | This is the ticker symbol of the equity under which it’s listed on the exchange.                                                                            | string |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.                       | string | `"1"`   |
| **Query**  | <p><strong>currency</strong>  <br><em>optional</em></p>      | This is the currency in which the equity is denominated (use it if you have two equities with the same ticker but denominated in two different currencies). | string |         |
| **Query**  | <p><strong>exchange</strong>  <br><em>optional</em></p>      | This is the exchange on which the equity is listed (use it if you have two equities with the same ticker but listed on two different exchanges).            | string |         |

### Responses

| HTTP Code | Description                                                                                            | Schema                                                            |
| --------- | ------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------- |
| **200**   | Successful request, JSON data containing detailed information about the enquired security is returned. | [EquityResource](securities\_getequitybysymbol.md#equityresource) |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation.      | No Content                                                        |
| **403**   | The provided Et-App-Key is incorrect.                                                                  | No Content                                                        |
| **404**   | Resource was not found                                                                                 | No Content                                                        |
| **422**   | A validation error occurred while processing the request.                                              | No Content                                                        |
| **500**   | Internal server error                                                                                  | No Content                                                        |

### Produces

* `application/json`
* `text/json`
