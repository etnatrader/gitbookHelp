
<a name="pricealerts_modifypricealerttrigger"></a>
#### Modify price alert
```
PUT /v{version}/users/{userId}/pricealerts/{alertId}
```


##### Description
This API endpoint enables you to modify an existing price alert.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**alertId**  <br>*required*|This is the internal identifier of the price alert that needs to be modified|integer (int32)||
|**Path**|**userId**  <br>*required*|This is the internal identifier of the user whose price alert will be modified.|integer (int32)||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Body**|**body**  <br>*required*|This is JSON data that contains updated information about the price alert.|[PriceAlertEditableModel](#pricealerteditablemodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data containing the updated price alert is returned.|[PriceAlertInfoModel](#pricealertinfomodel)|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**409**|Conflict|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



