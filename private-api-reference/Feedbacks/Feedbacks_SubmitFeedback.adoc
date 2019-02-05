
[[_feedbacks_submitfeedback]]
==== Submit feedback
....
POST /v{version}/feedbacks
....


===== Description
Submits a new feedback


===== Parameters

[options="header", cols=".^2,.^3,.^9,.^4,.^2"]
|===
|Type|Name|Description|Schema|Default
|**Header**|**Authorization** +
__required__|Bearer type token string|string|
|**Header**|**Et-App-Key** +
__required__|Application key|string|
|**Path**|**version** +
__required__|The requested API version|string|`"1"`
|**Body**|**body** +
__required__|Feedback model|<<_submitfeedbackmodel,SubmitFeedbackModel>>|
|===


===== Responses

[options="header", cols=".^2,.^14,.^4"]
|===
|HTTP Code|Description|Schema
|**200**|Feedback was successfully submitted|<<_pagingresult_submitfeedbackmodel,PagingResult[SubmitFeedbackModel]>>
|**401**|Authorization has been denied for this request.|No Content
|**403**|Application key is not defined or does not exist|No Content
|**409**|There is an error occurred in attempt to submit a feedback|No Content
|**422**|Validation error occurred while processing entity|No Content
|**500**|Feedback wasn't submitted. Unknown server error|No Content
|===


===== Consumes

* `application/json`
* `text/json`


===== Produces

* `application/json`
* `text/json`



