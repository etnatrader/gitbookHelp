---
description: List all ACH relationships of a particular trading account
---

# Get All ACH Relationships

This endpoint enables you to retrieve information about all ACH relationships of a particular trading account.

{% swagger baseUrl="baseURL" path="/v{version}/accounts/{accountId}/ach-relationships" method="get" summary="Get An Account's ACH Relationships" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="apiVersion" type="String" required="true" %}
The version of the API. By default it's 

`1.0`

.
{% endswagger-parameter %}

{% swagger-parameter in="path" name="accountId" type="Integer" required="true" %}
ID of the trading account.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Et-App-Key" type="String" required="true" %}
The unique key of your app that identifies it when communicating with our service. Contact your administrator to get this key.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="String" required="true" %}
Authorization token. Must be provided in the following format: 

`Bearer token`

 (

`Bearer`

 \+ 1 space + the token)
{% endswagger-parameter %}

{% swagger-parameter in="query" name="pageSize" type="Integer" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="query" name="pageNumber" type="Integer" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="query" name="sortBy" type="String" required="true" %}
Parameter by which the returned ACH relationships must be sorted.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="isDesc" type="Boolean" required="true" %}
Determines if returned ACH relationships must be sorted in descending or ascending order.
{% endswagger-parameter %}

{% swagger-parameter in="query" name="status" type="String" %}
Filters ACH relationships by status: Pending, Approved, Canceled, Error, PendingCancel, PendingApproval.
{% endswagger-parameter %}

{% swagger-response status="200" description="Successful request, a collection of ACH relationships is returned." %}
```javascript
{
  "Result": [
    {
      "Id": "91fde713-6c64-4ef3-0606-08d7bacaad26",
      "AccountId": 0,
      "ExternalId": "5e5927470d34ab4080d629a6",
      "RoutingNumber": "011401533",
      "AccountNumber": "1111222233331111",
      "AccountOwnerName": "Alberta Bobbeth Charleson",
      "Name": "Bank of America",
      "Status": "Approved",
      "CreatedAt": "2020-02-28T14:44:22.82Z",
      "ApprovalMethod": "Instant",
      "Default": false
    },
    {
      "Id": "36ffac9c-668f-484a-0607-08d7bacaad26",
      "AccountId": 0,
      "RoutingNumber": "011401533",
      "AccountNumber": "1111222233331111",
      "AccountOwnerName": "Alberta Bobbeth Charleson",
      "Name": "Bank of America",
      "Status": "Pending",
      "CreatedAt": "2020-03-02T09:21:06.01Z",
      "ApprovalMethod": "Instant",
      "Default": false
    },
    {
      "Id": "40ee3617-7a67-45dd-0609-08d7bacaad26",
      "AccountId": 0,
      "ExternalId": "5e6f80963c3477ba9dc1f98a",
      "RoutingNumber": "051000017",
      "AccountNumber": "987654321222",
      "AccountOwnerName": "Eugeny",
      "Name": "Main Citi Bank Account",
      "Status": "Canceled",
      "CreatedAt": "2020-03-16T13:35:18.0133333Z",
      "CancelDate": "2020-03-16T17:53:54.4806035Z",
      "CancelReason": "Closed the banking account",
      "ApprovalMethod": "Instant",
      "Default": false
    },
    {
      "Id": "ff1cdf34-da10-40bc-060a-08d7bacaad26",
      "AccountId": 0,
      "ExternalId": "5e6fc3093c3477ba9dc2438d",
      "RoutingNumber": "051000017",
      "AccountNumber": "987654321222",
      "AccountOwnerName": "Eugeny",
      "Name": "Citi Bank",
      "Status": "Approved",
      "CreatedAt": "2020-03-16T15:38:41.5766667Z",
      "ApprovalMethod": "Instant",
      "Default": false
    }
  ],
  "NextPageLink": "",
  "PreviousPageLink": "",
  "TotalCount": 4
}
```
{% endswagger-response %}
{% endswagger %}
