# Syntax

## Submit feedback

```text
POST /v{version}/feedbacks
```

### Description

Submits a new feedback

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Body** | **body**   _required_ | Feedback model | [SubmitFeedbackModel](../../definitions/#submitfeedbackmodel) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Feedback was successfully submitted | [PagingResult\[SubmitFeedbackModel\]](../../definitions/#pagingresult-submitfeedbackmodel) |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **409** | There is an error occurred in attempt to submit a feedback | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Feedback wasn't submitted. Unknown server error | No Content |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`

