# Syntax

## Add position manually

```text
POST /v{version}/positions
```

### Description

Add position without sending order request

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Query** | **recalculate**   _required_ | Recalculate account cash | boolean |  |
| **Body** | **body**   _required_ | Position to add | [InternalPositionModel](../../definitions/#internalpositionmodel) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Created position | [InternalPositionModel](../../definitions/#internalpositionmodel) |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **409** | Add position failed | [InternalPositionModel](../../definitions/#internalpositionmodel) |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Consumes

* `application/json`
* `text/json`

### Produces

* `application/json`
* `text/json`

