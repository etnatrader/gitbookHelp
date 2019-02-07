# Syntax

## Replace order

```text
PUT /v{version}/accounts/{accountId}/orders/{orderId}
```

### Description

Replace or verify order

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **accountId**   _required_ |  | integer \(int32\) |  |
| **Path** | **orderId**   _required_ | Order internal identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1"` |
| **Query** | **dryRun**   _optional_ | Preview order replace results without sending it to the market | boolean | `"false"` |
| **Body** | **body**   _required_ | Order modify params | [ModifyOrderModel](orders_replaceorder.md#modifyordermodel) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Replaced order model | [OrderModel](orders_replaceorder.md#ordermodel) |
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

