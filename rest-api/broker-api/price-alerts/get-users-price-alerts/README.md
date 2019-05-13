---
description: List a user's price alerts
---

# Get User's Price Alerts

## Overview

This GET endpoint enables you to retrieve the list of a user's price alerts. Price alerts are essentially notifications that are sent to the user when the alert's conditions are satisfied by the market. For example, a user may have a price alert that will notify them when the price of the Apple stock exceeds $200.

There are eight required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **userID** \(path\). This is the ID of the user whose particular watchlist needs to be have one security removed.
5. **pageSize** \(query\). This field indicates the number of price alerts that needs to be retrieved per page.
6. **pageNumber** \(query\). This field indicates the number of the page that needs to be retrieved \(all price alerts are split into a set of pages that can be loaded one by one\).
7. **sortBy** \(query\). This is the field by which the retrieved alerts should be sorted. For example, if you the value of this parameter is set to **State**, the retrieved alerts will be sorted by their state.
8. **isDesc** \(query\). This field indicates if the list of retrieved price alerts should be sorted in the descending \(true\) or ascending \(false\) order.

Here's the final template for this API request:

```text
GET apiURL/v1.0/users/@me/pricealerts?pageSize=10&pageNumber=0&sortBy=State&isDesc=true
```

## Response

In response to this API request, you'll receive a JSON file with the list of the user's price alerts.

```javascript
{
    "Result": [
        {
            "Id": 735,
            "State": "Expired",
            "CreatedDate": 1548163610,
            "Operator": "GTEQ",
            "SecurityId": 4,
            "Field": "Ask",
            "Argument": 155.8,
            "ExpirationDate": 1548250001
        },
        {
            "Id": 871,
            "State": "New",
            "CreatedDate": 1550588008,
            "Operator": "GTEQ",
            "SecurityId": 2829,
            "Field": "Bid",
            "Argument": 170,
            "ExpirationDate": 1550674384
        },
        {
            "Id": 872,
            "State": "New",
            "CreatedDate": 1550591120,
            "Operator": "LTEQ",
            "SecurityId": 685714,
            "Field": "Last",
            "Argument": 250,
            "ExpirationDate": 1550677486
        }
    ],
    "NextPageLink": "",
    "PreviousPageLink": "",
    "TotalCount": 3
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal identifier of the price alert. |
| State | This is the state of the price alert. Possible values: New, Expired, Completed, Stopped. |
| CreatedDate | This is the date on which the price alert was created \(in ticks\). |
| Operator | This is the condition of the price alert. Possible values: GTEQ \(greater or equal to\), LTEQ \(less than or equal to\). |
| SecurityId | This is the ID of the security for which the price alert is configured. |
| Field | This is the referent price for the price alert. Possible values: Ask, Bid, Last. |
| Argument | This is the price point at which the price alert will be triggered and the user will be notified. |
| ExpirationDate | This is the expiration date of the price alert \(in ticks\). |

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve the list of a user's price alerts.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

### Failing to Specify the Query Parameters

It's crucial to understand that the _**pageSize, pageNumber, isDesc, and sortBy**_ parameters must be provided in the request; otherwise you'll receive the 404 status code and the following message:

```javascript
{
    "Error": {
        "Code": "UnsupportedApiVersion",
        "Message": "The requested resource with API version '1.0' does not support HTTP method 'GET'."
    }
}
```

The following article covers the syntax for this API request in detail.

