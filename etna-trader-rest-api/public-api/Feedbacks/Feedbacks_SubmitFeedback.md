
<a name="feedbacks_submitfeedback"></a>
#### Submit feedback
```
POST /v{version}/feedbacks
```


##### Description
This API endpoint enables you to submit user feedback into ETNA Trader's support ticket management system.


##### Parameters

|Type|Name|Description|Schema|Default|
|---|---|---|---|---|
|**Header**|**Authorization**  <br>*required*|This is the authorization token that you retrieved from the first endpoint (/token).|string||
|**Header**|**Et-App-Key**  <br>*required*|This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader.|string||
|**Path**|**version**  <br>*required*|This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0.|string|`"1"`|
|**Body**|**body**  <br>*required*|This is a JSON dictionary that contains information about the new user feedback.|[SubmitFeedbackModel](#submitfeedbackmodel)||


##### Responses

|HTTP Code|Description|Schema|
|---|---|---|
|**200**|Successful request, JSON data containing the new feedback is returned.|[PagingResult[SubmitFeedbackModel]](#pagingresult-submitfeedbackmodel)|
|**401**|The access level of the provided authorization token is not sufficient to perform this operation.|No Content|
|**403**|The provided Et-App-Key is incorrect.|No Content|
|**409**|An error occurred while trying to submit the feedback.|No Content|
|**422**|A validation error occurred while processing the request.|No Content|
|**500**|Feedback wasn't submitted. Unknown server error|No Content|


##### Consumes

* `application/json`
* `text/json`


##### Produces

* `application/json`
* `text/json`



