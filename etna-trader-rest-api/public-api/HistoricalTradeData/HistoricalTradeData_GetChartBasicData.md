
<a name="historicaltradedata_getchartbasicdata"></a>
#### Get chart historical data
```
PUT /v{version}/history/symbols
```


##### Description
Get candles and indicators data for charting


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1.0"`|
|**Body**|**body**  <br>*required*||[ChartHistoryRequestModel](#charthistoryrequestmodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Requested candle and indicators data|[ChartHistoryModel](#charthistorymodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|Requested data could not be provided|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



