
<a name="internalusers_createuser"></a>
#### Create new user
```
POST /v{version}/users
```


##### Description
This API endpoint enables you to create a new user.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Query**|**sendInvitationEmail**  <br>*required*|This is a boolean parameter that indicates if an invitation email should be sent to the user after the creation.|boolean||
|**Body**|**body**  <br>*required*|This is JSON data that contains detailed information about the new user.|[CreateUserModel](#createusermodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data is returned, containing detailed information about the newly created user.|[UserModel](#usermodel)|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**409**|The user couldn’t be created due to some internal conflict.|< string > array|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



