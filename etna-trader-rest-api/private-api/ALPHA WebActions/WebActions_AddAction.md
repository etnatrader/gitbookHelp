
<a name="webactions_addaction"></a>
#### Create new web action
```
POST /v{version}/webactions
```


##### Description
Creates new Action


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Body**|**body**  <br>*required*|Action model|[WebActionMapModel](#webactionmapmodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Action was successfully created|[WebActionMapModel](#webactionmapmodel)|
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



