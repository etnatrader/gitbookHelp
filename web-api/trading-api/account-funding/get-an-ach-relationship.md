---
description: Fetch information about a specific ACH relationship
---

# Get an ACH Relationship

### Overview

This GET endpoint enables you to retrieve information about a specific ACH relationship.

There are five required parameters that must be provided in the request:

1. **Et-App-Key** (header). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** (header). This is the authorization token from the very first [token request](../authentication/). The value of this header must have the following format: `Bearer BQ898r9fefi` (`Bearer` + 1 space + the token).
3. **API version** (path). Unless necessary, leave it at "1.0".
4. **accountId** (path). This is the [internal identifier](../user-accounts/list-users-accounts/) of the trading account in ETNA Trader.
5. **id** (path). This is the ID of the ACH relationship whose information you would like to retrieve.

Here's the final template for this API request:

```
GET apiURL/v1.0/accounts/{accountId}/ach-relationships/{id}
```

### Response

In response to this API request, you will receive a JSON dictionary containing detailed information about the enquired ACH relationship.

```javascript
{
  "Id": "someID-da10-40bc-060a-08d7bacaad26",
  "AccountId": 0,
  "RoutingNumber": "051000017",
  "AccountNumber": "987654321222",
  "AccountOwnerName": "Eugeny",
  "Name": "Citi Bank",
  "Status": "Pending",
  "CreatedAt": "2020-03-16T15:38:41.5766667Z",
  "ApprovalMethod": "Instant",
  "Default": false
}
```

where:

| Parameter        | Description                                                                                                                                                                                   |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Id               | This is the internal identifier of the ACH relationship in ETNA Trader.                                                                                                                       |
| AccountId        | This is an ETNA Trader's trading account to which the ACH relationship.                                                                                                                       |
| RoutingNumber    | This is the routing number of the bank who opened the banking account. You can view sample routing number on [this page](https://bankorganizer.com/list-of-routing-numbers/#bank-of-america). |
| AccountNumber    | This is the number of the banking account in the target bank. For example: **987654321222**.                                                                                                  |
| AccountOwnerName | This is the name of the banking account owner. For example: **Robert**.                                                                                                                       |
| Name             | This is the name of the target bank. For example: **Citi Bank**.                                                                                                                              |
| Status           | <p>This is the status of the ACH relationship. </p><p>Possible values:</p><ul><li>Pending = 0, </li><li>Approved = 1</li><li>Canceled = 2</li><li>Error = 3</li></ul>                         |
| CreatedAt        | This is the precise time and date at which the ACH relationship was created.                                                                                                                  |
| ApprovalMethod   | This is the approval method. The value of this parameter can be either **Instant **(Plaid) or **Manual** (Micro deposits).                                                                    |
| Default          | This boolean value indicates if this ACH relationship is a default one for this trading account.                                                                                              |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve information about an ACH relationship.&#x20;

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```
