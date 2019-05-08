
<a name="internalusers_modifyuser"></a>
#### Update user
```
PUT /v{version}/users/{userId}
```


##### Description
This API endpoint enables you to modify an existing user in ETNA Trader.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**userId**  <br>*required*|This is the internal identifier of the user whose information needs to be modified.|integer (int32)||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Query**|**sendInvitationEmail**  <br>*required*|This is a boolean parameter that indicates if an invitation email should be sent to the user after their information is modified.|boolean||
|**Body**|**body**  <br>*required*|This is JSON data that contains detailed information about the modified user.|[ModifyUserModel](#modifyusermodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data is returned, containing updated information about the user.|[UserModel](#usermodel)|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**409**|The user couldn’t be modified due to some internal conflict.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



