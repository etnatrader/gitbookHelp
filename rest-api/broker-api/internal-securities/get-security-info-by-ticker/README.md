---
description: Retrieve security's information by providing the company's ticker symbol
---

# Get Security Info by Ticker

## Overview

This GET endpoint enables you to retrieve detailed information about a collection of securities with a common keyword in their ticker symbol. Unlike the [regular security information method](../../securities/get-securitys-info-by-mask/), this method provides a more comprehensive set of information about a particular security.

{% hint style="warning" %}
In order to retrieve information about a particular security, you must use an [authorization token](../../authentication/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are six required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **symbol** \(path\). This is the keyword that will be queried in all securities' ticker symbol field.
5. **pageSize** \(query\). This field indicates the number of securities that needs to be retrieved per page.
6. **pageNumber** \(query\). This field indicates the number of the page that needs to be retrieved \(all securities are split into a set of pages that can be loaded one by one\).

Here's the final template for this API request:

```text
GET apiURL/v1.0/internalsecurities
```

## Response

In response to this API request, you'll receive a JSON file with detailed information about the securities that contain the keyword in their ticker symbol.

```javascript
{
  "Result": [
    {
      "Id": 680410,
      "Symbol": "F",
      "Description": "Ford Motor Company Common Stock",
      "Exchange": "XNYS",
      "Currency": "USD",
      "AddedDate": "2012-11-30T07:22:20.667Z",
      "ModifyDate": "2017-12-14T08:00:29.2429719Z",
      "Enabled": true,
      "AllowTrade": true,
      "AllowMargin": true,
      "AllowShort": true,
      "Type": "CommonStock",
      "Source": 0,
      "SourceId": "F",
      "ParentId": -1,
      "MarginRate": 0,
      "OptionType": "Undefined",
      "ExpirationType": "Undefined",
      "ExpirationDate": "0001-01-01T00:00:00Z",
      "StrikePrice": 0,
      "SeriesId": -1,
      "ContractSize": 1,
      "Precision": 2,
      "VolumePrecision": 0,
      "Price": 0,
      "QuoteSubscriptionKey": "F",
      "Leverage": 0,
      "TickSize": 0.01,
      "Name": "F",
      "ExpirationName": "Jan 01 0001"
    },
    {
      "Id": 1580397,
      "Symbol": "F     170317C00005000",
      "Description": "CALL Ford Motor Company Common Stock $5 EXP 03/17/17",
      "Currency": "USD",
      "AddedDate": "2016-06-14T10:17:48.4142203Z",
      "ModifyDate": "2017-05-24T07:07:56.6602373Z",
      "Enabled": false,
      "AllowTrade": true,
      "AllowMargin": true,
      "AllowShort": false,
      "Type": "Option",
      "Source": 0,
      "SourceId": "F     170317C00005000",
      "ParentId": 680410,
      "MarginRate": 0,
      "OptionType": "Call",
      "ExpirationType": "Regular",
      "ExpirationDate": "2017-03-17T00:00:00Z",
      "StrikePrice": 5,
      "SeriesId": 120238,
      "UnderlyingSecuritySymbol": "F",
      "ContractSize": 100,
      "Precision": 2,
      "VolumePrecision": 0,
      "Price": 0,
      "QuoteSubscriptionKey": "",
      "Leverage": 0,
      "TickSize": 0.01,
      "Name": "F Mar 2017 5.00 Call",
      "ExpirationName": "Mar 2017"
    },
    {
      "Id": 1884503,
      "Symbol": "F     170317C00014000",
      "Description": "CALL Ford Motor Company Common Stock $14 EXP 03/17/17",
      "Currency": "USD",
      "AddedDate": "2016-06-21T03:00:37.7302406Z",
      "ModifyDate": "2017-05-24T07:07:56.6602373Z",
      "Enabled": false,
      "AllowTrade": true,
      "AllowMargin": true,
      "AllowShort": false,
      "Type": "Option",
      "Source": 0,
      "SourceId": "F     170317C00014000",
      "ParentId": 680410,
      "MarginRate": 0,
      "OptionType": "Call",
      "ExpirationType": "Regular",
      "ExpirationDate": "2017-03-17T00:00:00Z",
      "StrikePrice": 14,
      "SeriesId": 120238,
      "UnderlyingSecuritySymbol": "F",
      "ContractSize": 100,
      "Precision": 2,
      "VolumePrecision": 0,
      "Price": 0,
      "QuoteSubscriptionKey": "",
      "Leverage": 0,
      "TickSize": 0.01,
      "Name": "F Mar 2017 14.00 Call",
      "ExpirationName": "Mar 2017"
    },
    {
      "Id": 1884504,
      "Symbol": "F     170317P00014000",
      "Description": "PUT Ford Motor Company Common Stock $14 EXP 03/17/17",
      "Currency": "USD",
      "AddedDate": "2016-06-21T03:00:37.7302406Z",
      "ModifyDate": "2017-05-24T07:07:56.6602373Z",
      "Enabled": false,
      "AllowTrade": true,
      "AllowMargin": true,
      "AllowShort": false,
      "Type": "Option",
      "Source": 0,
      "SourceId": "F     170317P00014000",
      "ParentId": 680410,
      "MarginRate": 0,
      "OptionType": "Put",
      "ExpirationType": "Regular",
      "ExpirationDate": "2017-03-17T00:00:00Z",
      "StrikePrice": 14,
      "SeriesId": 120238,
      "UnderlyingSecuritySymbol": "F",
      "ContractSize": 100,
      "Precision": 2,
      "VolumePrecision": 0,
      "Price": 0,
      "QuoteSubscriptionKey": "",
      "Leverage": 0,
      "TickSize": 0.01,
      "Name": "F Mar 2017 14.00 Put",
      "ExpirationName": "Mar 2017"
    },
    {
      "Id": 2155153,
      "Symbol": "F     170616C00012000",
      "Description": "CALL Ford Motor Company Common Stock $12 EXP 06/16/17",
      "Currency": "USD",
      "AddedDate": "2016-07-15T03:00:35.8471243Z",
      "ModifyDate": "2017-06-20T07:07:24.0705146Z",
      "Enabled": false,
      "AllowTrade": true,
      "AllowMargin": true,
      "AllowShort": true,
      "Type": "Option",
      "Source": 0,
      "SourceId": "F     170616C00012000",
      "ParentId": 680410,
      "MarginRate": 0,
      "OptionType": "Call",
      "ExpirationType": "Regular",
      "ExpirationDate": "2017-06-16T00:00:00Z",
      "StrikePrice": 12,
      "SeriesId": 120238,
      "UnderlyingSecuritySymbol": "F",
      "ContractSize": 100,
      "Precision": 2,
      "VolumePrecision": 0,
      "Price": 0,
      "QuoteSubscriptionKey": "",
      "Leverage": 0,
      "TickSize": 0.01,
      "Name": "F Jun 2017 12.00 Call",
      "ExpirationName": "Jun 2017"
    }
  ],
  "NextPageLink": "https://priv-api-etnatrader-dev.etnasoft.us/api/v1.0/internalsecurities?symbol=F&pageSize=5&pageNumber=1",
  "PreviousPageLink": "",
  "TotalCount": 2057
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
| Source | This is an internal field in ETNA Trader. It shouldn't be used. |
| SourceId | This is an internal field in ETNA Trader. It shouldn't be used. |
| ParentId | This is the internal identifier of the underlying security of an option series. If the value is set to -1, it means that this security is not an option. |
| MarginRate | This is an internal field in ETNA Trader. It shouldn't be used by third-party developers. |
| OptionType | This is the type of the option. Possible values: Call, Put. |
| ExpirationType | This is the type of options' expiration date. Possible values: Regular, Quarterly, Weekly, Flex, Undefined, Mini. |
| ExpirationDate | This the expiration date of the option. |
| StrikePrice | This is the strike price of the option. |
| SeriesId | This is the internal identifier of the option series. If the value is set to -1, it means that this security is not an option. |
| Price | This is the security's price. |
| QuoteSubscriptionKey | This is a key that ETNA Trader uses to subscribe to quotes for this security. It's an internal field and should not be used by third-party developers. |
| Leverage | This is an internal field in ETNA Trader. It shouldn't be used by third-party developers. |
| Name | This is the name of the security \(usually it's identical to the Symbol field\). |
| ExpirationName | This is the expiration name of the option. If the value is set to Jan 01 0001, it means that this security is not an option. |
| NextPageLink | This is the next page with the requested securities. |
| PreviousPageLink | This is the previous page with the requested securities. |
| TotalCount | This is the total number of securities with the specified keyword in their ticker symbol. |

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve information about securities with a specific keyword in their tucker symbol.

### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for retrieving information about securities, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

So be sure to use the authorization token generated with an administrator's credentials.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

### Specifying  the Security's Internal ID Instead of its Ticker Symbol

Another common mistake when making this API request is specifying the internal ID of the enquired security instead of its ticker symbol — for this purpose, there's a [separate API request](../get-security-by-id/). If you specify the security's ticker symbol in this request, you'll receive the 400 status code and the following error message:

```javascript
{
    "Message": "The request is invalid."
}
```

The following article covers the syntax for this API request in detail.

