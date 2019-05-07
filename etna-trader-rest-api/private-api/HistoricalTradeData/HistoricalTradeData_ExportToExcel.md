
<a name="historicaltradedata_exporttoexcel"></a>
#### Get excel file with chart data
```
POST /v{version}/history/export
```


##### Description
Get excel file with chart data


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Body**|**body**  <br>*required*||[HistoricalTradeDataExportDataModel](#historicaltradedataexportdatamodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Requested excel file with chart data|object|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



