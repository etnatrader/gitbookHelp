
<a name="systemactions_resendorderreport"></a>
#### Resend order execution repost
```
PUT /v{version}/systemactions/orders/resendorderreports
```


##### Description
Resend order execution reports to Oms


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Body**|**body**  <br>*required*|Order report request parameters|[ResendOrderReportRequest](#resendorderreportrequest)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Action were successfully executed|[ResendOrderReportRequest](#resendorderreportrequest)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|An error occurred while executing the action|No Content|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



