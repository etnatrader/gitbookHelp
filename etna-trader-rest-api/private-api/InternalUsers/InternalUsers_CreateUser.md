
<a name="internalusers_createuser"></a>
#### Create new user
```
POST /v{version}/users
```


##### Description
Create new user


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|Bearer type token string|string||
|**Header**|**Et-App-Key**  <br>*required*|Application key|string||
|**Path**|**version**  <br>*required*|The requested API version|string|`"1"`|
|**Query**|**sendInvitationEmail**  <br>*required*|Send email for created user|boolean||
|**Body**|**body**  <br>*required*|User to create|[ModifyUserModel](#modifyusermodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Created user|[UserModel](#usermodel)|
|**401**|Authorization has been denied for this request.|No Content|
|**403**|Application key is not defined or does not exist|No Content|
|**409**|Conflict occured while creating user|< string > array|
|**422**|Validation error occurred while processing entity|No Content|
|**500**|Internal server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



