---
description: Fetch information about a particular option by providing its internal ID
---

# Get Option Info by Internal ID

## Overview

This GET endpoint enables you to retrieve information about a particular option. Whereas the last three methods deal with equities' information, this endpoint provides information exclusively about options.

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **ID** \(path\). This is the ID of the option whose information you'd like to retrieve. This ID can be fetched using the [API request that lists filtered options](../get-filtered-options/).

Here's the final template for this API request:

```text
apiURL/v1.0/options/13210821
```

## Response

In response to this API request, you'll receive a JSON file with comprehensive information about the enquired option:

```javascript
{
    "Id": 13210821,
    "Symbol": "VSSQ1 260117P00008000",
    "Description": "PUT Virtual Stock (static quotes) $8.00000000 EXP 01/17/26",
    "Exchange": "VIRTEX",
    "Currency": "USD",
    "AddedDate": "2018-09-11T07:20:10.318803Z",
    "ModifyDate": "2018-12-19T17:10:36.943Z",
    "Type": "Option",
    "Precision": 2,
    "VolumePrecision": 0,
    "TickSize": 0.01,
    "Enabled": true,
    "AllowTrade": true,
    "AllowMargin": true,
    "AllowShort": true,
    "OptionType": "Put",
    "ExpirationType": "Flex",
    "ExpirationDate": "2026-01-17T00:00:00Z",
    "StrikePrice": 8,
    "SeriesId": 125685,
    "UnderlyingAssetSymbol": "VSSQ1",
    "ContractSize": 100
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
| Type | This is the type of the security — option in the case of this API request. |
| Precision | This is the number of decimal places in the security's price. |
| VolumePrecision | This is the number of decimal places in the security's trading volume \(might be useful for cryptocurrencies\). |
| TickSize | This is the minimum price change of the security. For example, if this property equals 0.01 for AAPL, the minimum price change for AAPL is 0.01 \(150.67 —&gt; 150.68, but not 150.675\). For securities with the market price of less than $1, the TickSize is equal to 0.0001. |
| Enabled | This field indicated if the security is enabled and can be traded by users. |
| AllowTrade | This field indicates is the security if permitted for trading. |
| AllowMargin | This field indicates if the security is allowed to be traded on margin. |
| AllowShort | This field indicates if the security can be sold short. |
| OptionType | This is the type of option. Possible values: call, put. |
| ExpirationType | This is the expiration type of the option. Possible values: Regular, Quarterly, Weekly, Flex, Undefined, Mini, NonStandard. |
| ExpirationDate | This is the expiration date of the option. |
| StrikePrice | This is the price at which the holder of the option can buy or sell the underlying asset. |
| SeriesId | This is the internal ID of the option series in ETNA Trader. |
| UnderlyingAssetSymbol | This is the ticker symbol of the underlying asset. |
| ContractSize | This is the deliverable quantity of the option's underlying asset. |

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve an option's information by their internal ID.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

### Specifying the Underlying Security's Ticker instead of the Option ID

Another common mistake in retrieving information about a particular option is specifying the underlying security's ticker symbol instead of the enquired option's ID. Doing so will lead to the 409 status code.

The following article covers the syntax for this API request in detail.

