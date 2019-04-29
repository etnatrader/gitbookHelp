# Syntax

## Get all accounts

```text
GET /v{version}/accounts
```

### Description

Provides paged result of account items collection

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Query** | **filter**   _optional_ | Filter query | string \(String\) |  |
| **Query** | **isAscending**   _required_ | Query direction | boolean |  |
| **Query** | **pageNumber**   _required_ | Page number | integer \(int32\) |  |
| **Query** | **pageSize**   _required_ | Page size | integer \(int32\) |  |
| **Query** | **propertyName**   _required_ | Models property name to filter | string |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Paged result of account items | [PagingResult\[AccountModel\]](../../definitions/#pagingresult-accountmodel) |
| **400** | Filter query is invalid or contains unsupported operations | No Content |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

