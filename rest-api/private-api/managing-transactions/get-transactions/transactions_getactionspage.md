# Syntax

## Get transactions page

```text
GET /v{version}/accounts/{accountId}/transactions
```

### Description

Provides transactions Paged result

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | Bearer type token string | string |  |
| **Header** | **Et-App-Key**   _required_ | Application key | string |  |
| **Path** | **accountId**   _required_ | ID of specified account | integer \(int32\) |  |
| **Path** | **version**   _required_ | The requested API version | string | `"1.0"` |
| **Query** | **filter**   _optional_ | Filter query | string \(String\) |  |
| **Query** | **isDesc**   _required_ | Sorting direction. Desc if true, otherwise is asc | boolean |  |
| **Query** | **pageNumber**   _required_ | Page number | integer \(int32\) |  |
| **Query** | **pageSize**   _required_ | Page size | integer \(int32\) |  |
| **Query** | **sortBy**   _required_ | Sorting field | string |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Transactions paging result | [PagingResult\[TransactionMapModel\]](transactions_getactionspage.md#pagingresult-transactionmapmodel) |
| **400** | Filter query is invalid or contains unsupported operations | No Content |
| **401** | Authorization has been denied for this request. | No Content |
| **403** | Application key is not defined or does not exist | No Content |
| **422** | Validation error occurred while processing entity | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

