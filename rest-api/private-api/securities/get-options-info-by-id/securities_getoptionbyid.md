# Syntax

## Get option by id

```text
GET /v{version}/options/{id}
```

### Description

Get option by internal id

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **id**   _required_ | Internal identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Option resource | [OptionResource](securities_getoptionbyid.md#optionresource) |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **404** | Resource was not found | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

