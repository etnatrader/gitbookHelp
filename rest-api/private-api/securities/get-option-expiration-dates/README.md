---
description: Fetch expiration dates of options with a particular underlying security
---

# Get Option Expiration Dates

### Overview

This endpoint enables you to retrieve the expiration dates of all options in which the underlying security is provided in the request's query. 

There are four required parameters that must be provided in the request's header and query:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\). 
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **underlying** \(query\). This is the ticker symbol of the option's underlying security.

Here's the final template for this API request:

```text
GET apiURL/v1.0/options/expirations?underlying=AAPL
```

### Response

In response to this API request, you'll receive a list of expiration dates for options in which the underlying security was specified in the request query.

```javascript
[
    {
        "SeriesId": 103,
        "SeriesType": "Standard",
        "ExpirationDate": "2019-02-15T00:00:00Z",
        "ExpirationType": "Regular"
    },
    {
        "SeriesId": 103,
        "SeriesType": "Standard",
        "ExpirationDate": "2019-02-22T00:00:00Z",
        "ExpirationType": "Weekly"
    },
    {
        "SeriesId": 103,
        "SeriesType": "Standard",
        "ExpirationDate": "2019-03-01T00:00:00Z",
        "ExpirationType": "Weekly"
    },
    {
        "SeriesId": 103,
        "SeriesType": "Standard",
        "ExpirationDate": "2019-03-08T00:00:00Z",
        "ExpirationType": "Weekly"
    },
]
```

where:

| Parameter | Description |
| :--- | :--- |
| SeriesId | This is the internal identifier of the option series to which this option belongs. |
| SeriesType | This is the type of option series. Possible values: Standard, NonStandard, Binary, Flex, Undefined.  |
| ExpirationDate | This is the expiration date of the option. |
| ExpirationType | This is the expiration type of the option. Possible values: Regular, Quarterly, Weekly, Flex, Undefined, Mini, NonStandard.  |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve expiration data of options with a particular underlying security. 

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Failing to Specify the Query Parameters

It's crucial to understand that the _**underlying**_ query parameter must be indicated in the request; otherwise you'll receive the 404 status code and the following message:

```javascript
{
    "Message": "No HTTP resource was found that matches the request URI 'https://pub-api-etnatrader-dev.etnasoft.us/api/v1.0/equities?pageNumber=0&pageSize=2&sortField=Type'."
}
```

The following article covers the syntax for this API request in detail.

