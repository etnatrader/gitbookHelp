---
description: Retrieve security's information by providing its internal identifier
---

# Get Security Info by ID

### Overview

This GET endpoint enables you to retrieve detailed information about a particular security by providing its internal identifier in ETNA Trader. Unlike the [regular security information method](../../securities/get-securitys-info-by-internal-id/), this method provides a more comprehensive set of information about a particular security. 

{% hint style="warning" %}
In order to retrieve information about a particular security, you must use an [authorization token]() of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request]().
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **securityId** \(path\). This is the internal identifier of a security whose information needs to be retrieved.

Here's the final template for this API request:

```text
GET apiURL/v1.0/internalsecurities/{securityID}
```

### Response

In response to this API request, you'll receive a JSON file with detailed information about the enquired security.

```javascript
{
  "Id": 4,
  "Symbol": "AAPL",
  "Description": "Apple Inc.",
  "Exchange": "XNAS",
  "Currency": "USD",
  "AddedDate": "2012-11-29T16:05:43.993Z",
  "ModifyDate": "2018-12-10T08:00:22.2867686Z",
  "Enabled": true,
  "AllowTrade": true,
  "AllowMargin": true,
  "AllowShort": true,
  "Type": "CommonStock",
  "Source": 0,
  "SourceId": "AAPL",
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
  "QuoteSubscriptionKey": "AAPL",
  "Leverage": 0,
  "TickSize": 0.01,
  "Name": "AAPL",
  "ExpirationName": "Jan 01 0001"
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

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve information about a particular security.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for retrieving information about various securities, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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

#### Specifying  the Security's Ticker Symbol Instead of its Internal ID

Another common mistake when making this API request is specifying the ticker symbol of the enquired security instead of its internal ID — for this purpose, there's a [separate API request](../get-security-info-by-ticker/). If you specify the security's ticker symbol in this request, you'll receive the 400 status code and the following error message:

```javascript
{
    "Message": "The request is invalid."
}
```

The following article covers the syntax for this API request in detail.



