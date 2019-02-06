
<a name="pricealerts_modifypricealerttrigger"></a>
#### Modify price alert
```
PUT /v{version}/users/{userId}/pricealerts/{alertId}
```


##### Description
Modify price alert. Model properties "State",


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**alertId**  <br>*required*|Alert identifier|integer (int32)||
|**Path**|**userId**  <br>*required*|User identifier|integer (int32)||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Body**|**body**  <br>*required*|Price alert model|[PriceAlertEditableModel](#pricealerteditablemodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Updated price alert|[PriceAlertInfoModel](#pricealertinfomodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|Conflict|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



