---
description: List all ACH relationships of a particular trading account
---

# Get All ACH Relationships

### Overview

This GET endpoint enables you to retrieve information about all ACH relationships of a particular trading account.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountId** \(path\). This is the [internal identifier](../user-accounts/list-users-accounts/) of the trading account in ETNA Trader whose ACH relationships must be listed.
5. **pageNumber** \(query\). This is the number of the page \(all ACH relationships are split in pages\).
6. **pageSize** \(query\). This is the preferable size of the page \(maximum value is 99\).
7. **sortField** \(query\). This is a parameter by which all returned ACH relationships must be sorted.
8. **desc** \(query\). This boolean parameter indicates if the returned ACH relationships should be sorted in ascending \(false\) or descending \(true\) order.

Here's the final template for this API request:

```text
GET apiURL/v1.0/accounts/{accountId}/ach-relationships/
```

### Response

In response to this API request, you will receive an array of JSON dictionaries, each containing detailed information about some ACH relationship.

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

where:

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal identifier of the ACH relationship in ETNA Trader. |
| AccountId | This is an ETNA Trader's trading account to which the ACH relationship. |
| RoutingNumber | This is the routing number of the bank who opened the banking account. You can view sample routing number on [this page](https://bankorganizer.com/list-of-routing-numbers/#bank-of-america). |
| AccountNumber | This is the number of the banking account in the target bank. For example: **987654321222**. |
| AccountOwnerName | This is the name of the banking account owner. For example: **Robert**. |
| Name | This is the name of the target bank. For example: **Citi Bank**. |
| Status | This is the status of the ACH relationship. |
| CreatedAt | This is the precise time and date at which the ACH relationship was created. |
| ApprovalMethod | This is the approval method. The value of this parameter can be either **Instant** \(Plaid\) or **Manual** \(Micro deposits\). |
| Default | This boolean value indicates if this ACH relationship is a default one for this trading account. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve a list of ACH relationships. 

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

