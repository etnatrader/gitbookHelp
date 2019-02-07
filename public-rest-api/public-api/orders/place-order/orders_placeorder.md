# Syntax

## Place order

```text
POST /v{version}/accounts/{accountId}/orders
```

### Description

Place or verify order

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **accountId**   _required_ | Account identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1"` |
| **Query** | **dryRun**   _optional_ | Preview order place results without sending it to the market | boolean | `"false"` |
| **Body** | **body**   _required_ | Place order parameters | [CreateOrderModel](orders_placeorder.md#createordermodel) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Placed order model | [OrderModel](orders_placeorder.md#ordermodel) |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`

