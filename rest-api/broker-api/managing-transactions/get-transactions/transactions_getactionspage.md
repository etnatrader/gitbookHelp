# Syntax

## Get transactions page

```text
GET /v{version}/accounts/{accountId}/transactions
```

### Description

This API endpoint enables you to retrieve a list of transactions that have been made on a particular trading account.

### Parameters

| Type | Name | Description | Schema | Default |
| :--- | :--- | :--- | :--- | :--- |
| **Header** | **Authorization**   _required_ | This is the authorization token that you retrieved from the first endpoint \(/token\). | string |  |
| **Header** | **Et-App-Key**   _required_ | This is your app’s unique key that can be retrieved from the BO Companies widget in ETNA Trader. | string |  |
| **Path** | **accountId**   _required_ | This is the internal identifier of the trading account whose transactions must be retrieved. | integer \(int32\) |  |
| **Path** | **version**   _required_ | This is the version of the API. Unless you have multiple versions of ETNA Trader’s API deployed in your environment, leave it at 1.0. | string | `"1"` |
| **Query** | **filter**   _optional_ | This is a filter query used to retrieve only those transactions that satisfy the conditions of the query. | string \(String\) |  |
| **Query** | **isDesc**   _required_ | This is a boolean field that indicates if the returned transactions should be sorted in  descending \(true\) or ascending \(false\) order. | boolean |  |
| **Query** | **pageNumber**   _required_ | This is the page number \(all transactions are split into pages\). | integer \(int32\) |  |
| **Query** | **pageSize**   _required_ | This is the number of transactions that should be retrieved from the specified page. | integer \(int32\) |  |
| **Query** | **sortBy**   _required_ | This parameter indicates by which field the retrieved transactions should be sorted. | string |  |

### Responses

| HTTP Code | Description | Schema |
| :--- | :--- | :--- |
| **200** | Successful request, JSON data containing the filtered transactions is returned. | [PagingResult\[TransactionMapModel\]](transactions_getactionspage.md#pagingresult-transactionmapmodel) |
| **400** | Filter query is invalid or contains unsupported operations | No Content |
| **401** | The access level of the provided authorization token is not sufficient to perform this operation. | No Content |
| **403** | The provided Et-App-Key is incorrect. | No Content |
| **422** | A validation error occurred while processing the request. | No Content |
| **500** | Internal server error | No Content |

### Produces

* `application/json`
* `text/json`

