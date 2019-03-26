---
description: Add a new security to ETNA Trader
---

# Add a New Security

### Overview

This POST endpoint enables you to add a new security to ETNA Trader by sending a JSON file with the updated information. Whereas the public API only permits you to retrieve information about existing securities, the private API also permits addition of new securities. It's critical to be cautious with this procedure because providing incorrect information might lead to certain conflicts like the absence of quotes for a particular security.

{% hint style="warning" %}
In order to add a new security, you must use an [authorization token]() of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request]().
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **newSecurity** \(body\). This is a JSON file with the security's parameters that must be updated.

#### Request Body Sample

Following is a sample of a JSON file that contains information about the new security.

#### Common Stock Creations Sample

```javascript
{
  "Symbol": "TESTTICKER",
  "AddedDate": "2019-03-02T10:09:04.543Z",
  "ModifyDate": "2019-03-04T12:15:41.3202822Z",
  "Enabled": true,
  "AllowTrade": true,
  "AllowMargin": true,
  "AllowShort": true,
  "Type": "CommonStock",
  "Source": 1,
  "SourceId": "DFFFFFF",
  "ParentId": -1,
  "MarginRate": 0,
  "ContractSize": 10,
  "Precision": 5,
  "VolumePrecision": 2,
  "Price": 100,
  "Leverage": 1,
  "TickSize": 0.01,
  "Name": "Heyy",
  "ExpirationName": "Jan 0001"
}
```

#### Comprehensive Stock Creation Sample

```javascript
{
    "Symbol":"SGDFFD",
    "Suffix":null,
    "Description":null,
    "Exchange":null,
    "Currency":null,
    "BaseCurrency":null,
    "AddedDate":null,
    "ModifyDate":null,
    "Enabled":true,
    "AllowTrade":true,
    "AllowMargin":true,
    "AllowShort":true,
    "Type":"CommonStock",
    "Source":0,
    "SourceId":"234",
    "ParentId":-1,
    "Unit":null,
    "MarginRate":0,
    "ExpirationDate":null,
    "StrikePrice":0,
    "SeriesId":-1,
    "UnderlyingSecuritySymbol":null,
    "ContractSize":0,
    "Sector":null,
    "Industry":null,
    "Precision":0,
    "VolumePrecision":0,
    "Price":0,
    "Isin":null,
    "Sedol":null,
    "Cusip":null,
    "QuoteSubscriptionKey":null,
    "Leverage":0,
    "TickSize":0,
    "Name":null,
    "ExpirationName":null
}
```

where:

| Parameter | Description |
| :--- | :--- |
| Symbol | This is the ticker symbol of the new security.  |
| Suffix | This is an internal field in ETNA Trader and it shouldn't be used by third-party developers. |
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
| BaseCurrency | This is the currency in which a forex instrument is denominated. |
| Source | This is the identifier of the security in the market provider \(leave it at 0\). |
| SourceId | This is the security's ID in the market provider. Usually it's identical to the security's ticker symbol. |
| MarginRate | This is an internal field in ETNA Trader. It shouldn't be used by third-party developers. |
| Price | This is the security's last closing price. |
| QuoteSubscriptionKey | This is a key that ETNA Trader uses to subscribe to quotes for this security. It's an internal field and should not be used by third-party developers. |
| Leverage | This is an internal field in ETNA Trader. It shouldn't be used by third-party developers. |
| Name | This is the name of the security \(usually it's identical to the Symbol field\). |
| ExpirationName | This is the expiration name of the option. If the value is set to Jan 01 0001, it means that this security is not an option. |
| Isin | This abbreviation stands for International Securities Identification Number and it serves as a security's unique identifier. |
| Sedol | This abbreviation stands for Stock Exchange Daily Official List and it's primarily used by the London Stock Exchange and various other smaller stock exchanges.in the United Kingdom.  |
| Cusip | This abbreviation stands for Committee on Uniform Security Identification Procedures and it serves as an alternative identifier for stocks and bonds circulating in the United States and Canada. |
| ContractSize | This is the minimum number of securities that can be purchased in one trade. |

Here's the final template for this API request:

```text
POST apiURL/v1.0/internalsecurities
```

### Response

In response to this API request, you'll receive a JSON file that contains information about the new security:

```javascript
{
  "Id": 178394,
  "Symbol": "SGDFFD",
  "AddedDate": "2019-03-02T10:09:04.543Z",
  "ModifyDate": "2019-03-04T12:15:41.3202822Z",
  "Enabled": true,
  "AllowTrade": true,
  "AllowMargin": true,
  "AllowShort": true,
  "Type": "CommonStock",
  "Source": 1,
  "SourceId": "AAPL",
  "ParentId": -1,
  "MarginRate": 0,
  "OptionType": "Call",
  "ExpirationType": "Regular",
  "ExpirationDate": "0001-01-01T00:00:00Z",
  "StrikePrice": 0,
  "SeriesId": -1,
  "ContractSize": 10,
  "Precision": 5,
  "VolumePrecision": 0,
  "Price": 100,
  "Leverage": 1,
  "TickSize": 0.01,
  "Name": "AAPL",
  "ExpirationName": "Jan 0001"
}
```

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to create a new security.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for creating new securities, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

#### Failing to Provide All Required Parameters

Another common mistake when making this API request is failing to provide all required parameters in the request's body. In the first table of this page we have outlined all required parameters for this request, so ensure that you provide all of them; otherwise you'll receive the 500 status code and the following error message:

```javascript
{
  "message": "An error occurred while processing your request",
  "error": "Unexpected server error"
}
```

The following article covers the syntax for this API request in detail.



