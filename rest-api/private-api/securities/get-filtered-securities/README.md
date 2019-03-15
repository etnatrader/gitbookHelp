---
description: Fetch securities filtered by a particular field and split into multiple pages
---

# Get Filtered Equities

### Overview

This GET endpoint enables you to retrieve equites sorted by a specified field. 

{% hint style="warning" %}
In order to retrieve the a list of filtered equities, you must use an [authorization token]() of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are seven required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\). 
2. **Authorization** \(header\). This is the authorization token from the very first [token request]().
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **pageNumber** \(query\). This is the page number \(there are thousands of equities split into pages\).
5. **pageSize** \(query\). This is the number of equities that should be retrieved from this page. 
6. **sortField** \(query\). This is the field by which all equities should be sorted. For example, if you specify **Type**, first you'll receive stocks, then ETFs, etc.
7. **Desc** \(query\). This is a boolean field that indicates if the returned equities should be sorted in the descending order.

Here's the final template for this API request:

```text
GET apiURL/v1.0/equities?pageNumber=0&pageSize=2&sortField=Type&desc=true
```

### Response

In response to this API request, you'll receive the following JSON that lists the equities sorted by the specified parameter.

```javascript
{
    "Result": [
        {
            "Id": 681777,
            "Symbol": "INDY",
            "Description": "iShares S&P India Nifty 50 Index Fund",
            "Exchange": "XNAS",
            "Currency": "USD",
            "AddedDate": "2012-11-30T07:22:20.667Z",
            "ModifyDate": "2018-03-26T07:00:05.944571Z",
            "Type": "ETF",
            "Precision": 2,
            "VolumePrecision": 0,
            "TickSize": 0.01,
            "Enabled": true,
            "AllowTrade": true,
            "AllowMargin": true,
            "AllowShort": true
        },
        {
            "Id": 684344,
            "Symbol": "QQQ",
            "Description": "Invesco QQQ Trust, Series 1",
            "Exchange": "XNAS",
            "Currency": "USD",
            "AddedDate": "2012-11-30T07:22:20.67Z",
            "ModifyDate": "2018-05-29T07:00:05.8792207Z",
            "Type": "ETF",
            "Precision": 2,
            "VolumePrecision": 0,
            "TickSize": 0.01,
            "Enabled": true,
            "AllowTrade": true,
            "AllowMargin": true,
            "AllowShort": true
        }
    ],
    "NextPageLink": "https://pub-api-etnatrader-dev.etnasoft.us/api/v1.0/equities?pageNumber=1&pageSize=2&sortField=Type&desc=true",
    "PreviousPageLink": "",
    "TotalCount": 12130
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal ID of the security in ETNA Trader. |
| Symbol | This is the ticker symbol under which the security is listed on the exchange. |
| Description | Usually this is the full name of the underlying company. |
| Exchange | This is the exchange on which the security is listed. |
| Currency | This is the currency in which the security is denominated. |
| AddedDate | This is the date on which the security was added to the database. |
| ModifyDate | This is the date in which the security's information was last modified. |
| Type | This is the type of the security. |
| Precision | This is the number of decimal places in the security's price. |
| VolumePrecision | This is the number of decimal places in the security's trading volume \(might be useful for cryptocurrencies\). |
| TickSize | This is the minimum price change of the security. For example, if this property equals 0.01 for AAPL, the minimum price change for AAPL is 0.01 \(150.67 —&gt; 150.68, but not 150.675\). For securities with the market price of less than $1, the TickSize is equal to 0.0001. |
| Enabled | This field indicated if the security is enabled and can be traded by users. |
| AllowTrade | This field indicates is the security if permitted for trading. |
| AllowMargin | This field indicates if the security is allowed to be traded on margin. |
| AllowShort | This field indicates if the security can be sold short. |
| NextPageLink | The link of the next page of equities |
| PreviousPageLink | The link of the previous page of equities |
| TotalCount | The total number of equities available. |

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve sorted equities. 

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for retrieving sorted equities, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

#### Failing to Specify the Query Parameters

It's crucial to understand that all four query parameters must be indicated in the request; otherwise you'll receive the 404 status code and the following message:

```javascript
{
    "Message": "No HTTP resource was found that matches the request URI 'https://pub-api-etnatrader-dev.etnasoft.us/api/v1.0/equities?pageNumber=0&pageSize=2&sortField=Type'."
}
```

The following article covers the syntax for this API request in detail.

