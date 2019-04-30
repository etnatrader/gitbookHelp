# Syntax

## Get securities by symbol

```text
GET /v{version}/internalsecurities
```

### Description

Provides securities collection by specified symbol

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Query** | **pageNumber**   _required_ | Page number | integer \(int32\) |  |
| **Query** | **pageSize**   _required_ | Page size | integer \(int32\) |  |
| **Query** | **symbol**   _required_ | Symbol to search by | string |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Internal securities models collection | [PagingResult\[InternalSecurityResource\]]() |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

