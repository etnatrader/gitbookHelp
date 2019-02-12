---
description: Get transaction history for a particular trading account
---

# Get Account's History

### Overview

This endpoint enables you to retrieve the historical value of a particular trading account. 

{% hint style="warning" %}
In order to request the historical value of a particular trading account, you must use an [authorization token](../../authentication/requesting-tokens/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are seven required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **Trading Account Number** \(path\). This is the numeric ID of the trading account whose historical value you'd like to retrieve. You can get the list of a user's trading accounts with [this API call](../list-users-accounts/).
4. **API version** \(path\). Unless necessary, leave it at "1.0".
5. **startDate** \(query\). This is the starting date from which the account value history will be retrieved.
6. **endDate** \(query\). This is the end date until which the account value history will be retrieved.
7. **step** \(query\). This is the number of items that must be retrieved.

{% hint style="info" %}
The **step** parameter is currently ignored by the service. You can assign any value to it without affecting the content of the response.
{% endhint %}

This API request must be sent to the following URL:

```text
apiURL/v1.0/accounts/accountNumber/history?startDate=2019-01-01T14:20:10.837Z&endDate=2019-02-08T14:20:10.837Z&step=5
```

### Response

In response to this request, you'll receive a JSON file with the list of account valuation throughout the specified period.

```javascript
[
    {
        "Date": "2019-01-14T00:00:00Z",
        "Value": 1000000
    },
    {
        "Date": "2019-01-15T00:00:00Z",
        "Value": 1000000
    },
    {
        "Date": "2019-01-16T00:00:00Z",
        "Value": 1000000
    },
    {
        "Date": "2019-01-17T00:00:00Z",
        "Value": 1000000
    },
    {
        "Date": "2019-01-18T00:00:00Z",
        "Value": 1000000
    },
    {
        "Date": "2019-01-22T00:00:00Z",
        "Value": 999534.25
    },
    {
        "Date": "2019-01-23T00:00:00Z",
        "Value": 999598.75
    },
    {
        "Date": "2019-01-24T00:00:00Z",
        "Value": 999400.75
    },
    {
        "Date": "2019-01-25T00:00:00Z",
        "Value": 1000183.75
    },
    {
        "Date": "2019-01-28T00:00:00Z",
        "Value": 999850.75
    },
    {
        "Date": "2019-01-29T00:00:00Z",
        "Value": 1001035.75
    },
    {
        "Date": "2019-01-30T00:00:00Z",
        "Value": 1001328.25
    },
    {
        "Date": "2019-01-31T00:00:00Z",
        "Value": 1001530.75
    },
    {
        "Date": "2019-02-01T00:00:00Z",
        "Value": 1001488.75
    }
]
```

where:

| Parameter | Description |
| :--- | :--- |
| Date | The precise date on the valuation |
| Value | The value of the account for the date |

### Common Mistakes

Here are some of the common mistakes that developers make when requesting the historical value of a particular trading account:

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for retrieving historical values of a particular trading account, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

So be sure to use the authorization token generated with an administrator's credentials.

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Incorrect or Missing Query Parameters

If the query parameters are missing or incorrectly specified , the following error message will be returned:

```javascript
{
    "Message": "No HTTP resource was found that matches the request URI 'https://pub-api-et-demo-prod.etnasoft.us/api/v1.0/accounts/6303/history'."
}
```

In the following article we provide in-depth coverage of the syntax for this API request.

