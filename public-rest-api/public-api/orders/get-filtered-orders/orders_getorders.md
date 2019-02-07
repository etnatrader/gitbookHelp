# Syntax

## Get orders

```text
GET /v{version}/accounts/{accountId}/orders
```

### Description

Get orders by type and statuses

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **accountId**   _required_ | Account internal identifier | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1"` |
| **Query** | **filter**   _optional_ | Order filter query | string \(String\) |  |
| **Query** | **pageNumber**   _required_ | Page number | integer \(int32\) |  |
| **Query** | **pageSize**   _required_ | Page size | integer \(int32\) |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Collection of order models | &lt; [OrderModel](orders_getorders.md#ordermodel) &gt; array |
| **400** | Filter query is invalid or contains unsupported operations | No Content |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

