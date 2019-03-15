# Syntax

## Get chart historical data

```text
PUT /v{version}/history/symbols
```

### Description

Get candles and indicators data for charting

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Body** | **body**   _required_ |  | [ChartHistoryRequestModel](historicaltradedata_getchartbasicdata.md#charthistoryrequestmodel) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Requested candle and indicators data | [ChartHistoryModel](historicaltradedata_getchartbasicdata.md#charthistorymodel) |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **409** | Requested data could not be provided | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`

