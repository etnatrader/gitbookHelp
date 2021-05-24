---
description: Delete an existing ACH relationship
---

# Delete an ACH Relationship

### Overview

This DELETE endpoint enables you to delete an existing ACH relationship from a particular trading account.

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/). The value of this header must have the following format: `Bearer BQ898r9fefi` \(`Bearer` + 1 space + the token\).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountId** \(path\). This is the [internal identifier](../user-accounts/list-users-accounts/) of the trading account in ETNA Trader to which the ACH relationship is bound.
5. **id** \(path\). This is the ID of the to-be-deleted ACH relationship in ETNA Trader.
6. **reason** \(query\). This is a string that contains the reason for closing the ACH relationship.

Here's the final template for this API request:

```text
DELETE apiURL/v1.0/accounts/{accountId}/ach-relationships/{id}?reason=Closed%20the%20banking%20account
```

### Response

In response to this API request, you will receive a JSON dictionary containing information about the deleted ACH relationship, including the **Canceled** status and the cancelation reason.

```javascript
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
}
```

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to send a request to delete an existing ACH relationship.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

