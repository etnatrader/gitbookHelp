# Syntax

## Replace order

```text
PUT /v{version}/accounts/{accountId}/orders/{orderId}
```

### Description

Replace order

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **accountId**   _required_ | Account identifier | integer \(int32\) |  |
| **Path** | **orderId**   _required_ | Order internal identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Body** | **body**   _required_ | Order modify params | [ModifyOrderResource](orders_replaceorder.md#modifyorderresource) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Replaced order model | [OrderResource](orders_replaceorder.md#orderresource) |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **409** | Conflict | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`

