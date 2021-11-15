---
description: Retrieve all deposits and withdrawals of a particular trading account
---

# Get All Transfers

### Overview

This GET endpoint enables you to retrieve all deposits and withdrawals of a particular trading account.&#x20;

There are eight required parameters that must be provided in the request:

1. **Et-App-Key** (header). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** (header). This is the authorization token from the very first [token request](../authentication/). The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
3. **API version** (path). Unless necessary, leave it at "1.0".
4. **accountId** (path). This is the [internal identifier](../user-accounts/list-users-accounts/) of the trading account in ETNA Trader.
5. **pageNumber **(query). This is the number of the page (all transfers are split in pages).
6. **pageSize **(query). This is the preferable size of the page (maximum value is 99).
7. **sortField **(query). This is a parameter by which all returned transfers must be sorted.
8. **desc **(query). This boolean parameter indicates if the returned transfers should be sorted in ascending (false) or descending (true) order.

Here's the final template for this API request:

```
GET apiURL/v1.0/accounts/{accountId}/transfers
```

### Response

In response to this API request, you will receive an array of JSON dictionaries containing detailed information about all transfers on this trading account.

```javascript
{
  "Result": [
    {
      "Id": "a59448f5-176d-4473-6ce2-08d7bc5cbf81",
      "AccountId": 0,
      "ExternalId": "20200228003627",
      "Mechanism": "ACH",
      "IsDeposit": true,
      "Status": "Complete",
      "Comment": "Deposit allowed",
      "Amount": 100,
      "TotalAmount": 100,
      "TransferDate": "2020-02-28T14:45:57.5867903Z",
      "CreatedAt": "2020-02-28T14:44:43.3666667Z",
      "ClearingAccountNumber": "5DP05506"
    },
    {
      "Id": "99c0509e-04ee-46a4-6ce4-08d7bc5cbf81",
      "AccountId": 0,
      "Mechanism": "ACH",
      "IsDeposit": true,
      "Status": "Submitted",
      "Amount": 50,
      "TotalAmount": 0,
      "CreatedAt": "2020-02-28T16:26:02.7133333Z",
      "ClearingAccountNumber": "5DP05506"
    }
  ],
  "NextPageLink": "",
  "PreviousPageLink": "",
  "TotalCount": 2
}
```

where:

| Parameter    | Description                                                                                                                                                                                                              | Value   |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------- |
| Id           | Internal ID of the transfer.                                                                                                                                                                                             | String  |
| AccountId    | Internal ID of the trading account on whose behalf the transfer was performed.                                                                                                                                           | Integer |
| Mechanism    | <p>The transfer mechanism. <br>Possible values:</p><ul><li>ACH,</li><li>Check,</li><li>Wire.</li></ul>                                                                                                                   | String  |
| IsDeposit    | Indicates if this transfer is a deposit.                                                                                                                                                                                 | Boolean |
| Status       | The status of the transfer.                                                                                                                                                                                              | String  |
| Comment      | An accompanying comment.                                                                                                                                                                                                 | String  |
| Amount       | The amount transferred in USD.                                                                                                                                                                                           | Double  |
| TransferDate | The date on which the transfer was finalized at the clearing firm. The funds will be available in the trading account the following trading session when ETNA Trader receives Start-of-Day files from the clearing firm. | String  |
| CreatedAt    | The date on which the transfer was initiated.                                                                                                                                                                            | String  |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to send a request to list all transfers.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```
