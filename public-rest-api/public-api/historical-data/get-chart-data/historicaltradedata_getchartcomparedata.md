# Syntax

## Get chart compare data

```text
PUT /v{version}/history/compare
```

### Description

Get compared securities data for charting

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1"` |
| **Body** | **body**   _required_ |  | [ChartCompareRequestModel](historicaltradedata_getchartcomparedata.md#chartcomparerequestmodel) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Requested compared securities data | &lt; &lt; [TimeSeriesValueCandleMapModel](historicaltradedata_getchartcomparedata.md#timeseriesvaluecandlemapmodel) &gt; array &gt; array |
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

