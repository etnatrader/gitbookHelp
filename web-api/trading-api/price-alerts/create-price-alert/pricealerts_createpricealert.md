# Syntax

## Create price alert

```
POST /v{version}/users/{userId}/pricealerts
```

### Description

This API endpoint enables you to create a new price alert.

### Parameters

| Type       | Name                                                         | Description                                                                                                                           | Schema                                                                              | Default |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                  | string                                                                              |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                      | string                                                                              |         |
| **Path**   | <p><strong>userId</strong>  <br><em>required</em></p>        | This is the internal identifier of the user on whose behalf a new price alert will be created.                                        | integer (int32)                                                                     |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string                                                                              | `"1"`   |
| **Body**   | <p><strong>body</strong>  <br><em>required</em></p>          | This is JSON data that contains information about the new price alert.                                                                | [PriceAlertEditableModel](pricealerts\_createpricealert.md#pricealerteditablemodel) |         |

### Responses

| HTTP Code | Description                                                                                       | Schema                                                                      |
| --------- | ------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| **200**   | Successful request, the price alert has been successfully created.                                | [PriceAlertInfoModel](pricealerts\_createpricealert.md#pricealertinfomodel) |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation. | No Content                                                                  |
| **403**   | The provided Et-App-Key is incorrect.                                                             | No Content                                                                  |
| **409**   | The body of the request is lacking one of the required parameters                                 | No Content                                                                  |
| **422**   | A validation error occurred while processing the request.                                         | No Content                                                                  |
| **500**   | Internal server error                                                                             | No Content                                                                  |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`
