# Syntax

## Get chart historical data

```
PUT /v{version}/history/symbols
```

### Description

This API endpoint enables you to retrieve chart data for a particular security in the Microsoft Excel (.xlsx) format.

### Parameters

| Type       | Name                                                         | Description                                                                                                                           | Schema                                                                                         | Default |
| ---------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ------- |
| **Header** | <p><strong>Authorization</strong>  <br><em>required</em></p> | This is the authorization token that you retrieved from the first endpoint (/token).                                                  | string                                                                                         |         |
| **Header** | <p><strong>Et-App-Key</strong>  <br><em>required</em></p>    | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.                                      | string                                                                                         |         |
| **Path**   | <p><strong>version</strong>  <br><em>required</em></p>       | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string                                                                                         | `"1"`   |
| **Body**   | <p><strong>body</strong>  <br><em>required</em></p>          | This is a JSON dictionary that contains information about the enquired security.                                                      | [ChartHistoryRequestModel](historicaltradedata\_getchartbasicdata.md#charthistoryrequestmodel) |         |

### Responses

| HTTP Code | Description                                                                                         | Schema                                                                           |
| --------- | --------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| **200**   | Successful request, an XLSX file is returned, containing the chart data for the specified security. | [ChartHistoryModel](historicaltradedata\_getchartbasicdata.md#charthistorymodel) |
| **401**   | The access level of the provided authorization token is not sufficient to perform this operation.   | No Content                                                                       |
| **403**   | The provided Et-App-Key is incorrect.                                                               | No Content                                                                       |
| **409**   | Requested data could not be provided                                                                | No Content                                                                       |
| **422**   | A validation error occurred while processing the request.                                           | No Content                                                                       |
| **500**   | Internal server error                                                                               | No Content                                                                       |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`
