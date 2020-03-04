# Get an Option Chain

## Overview

This GET endpoint enables you to retrieve an option chain for a specific security.  An option chain is a series of options with a fixed number of options with the strike price above and below a center strike price. For instance, if you want an option chain with `Range` set to `1`, you will receive two pairs \(Call + Put\) of options: one above the center strike price and another below the center strike price. 

There are four required parameters that must be provided in the request's header and query:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\). 
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/requesting-tokens/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **symbol** \(path\). This is the ticker symbol of the underlying security for which the option series must be fetched.

There's also one optional parameter worth examining:

* filter \(query\). This is an SQL query used to retrieve only those options that satisfy the conditions of the query. The following table outlines the parameter's syntax.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Syntax</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Example</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Expiration = {Date}</li>
        </ul>
      </td>
      <td style="text-align:left">This query enables you to retrieve options with a specific expiration
        date.</td>
      <td style="text-align:left">
        <ul>
          <li>Expiration = #2020-01-17T00:00:00Z#</li>
        </ul>
        <p></p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Range = {integer}</li>
        </ul>
      </td>
      <td style="text-align:left">This query enables you to retrieve the specified number of options below
        and above the center strike price. For instance, if you want an option
        chain with <code>Range</code> set to <code>1</code>, you will receive two
        pairs (Call + Put) of options: one above the center strike price and another
        below the center strike price.</td>
      <td style="text-align:left">
        <ul>
          <li>Range = 1</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>ExpirationType</li>
        </ul>
      </td>
      <td style="text-align:left">
        <p>This query enables you to retrieve options of the specified expiration
          type.</p>
        <ul>
          <li>Regular = 0</li>
          <li>Quarterly = 1</li>
          <li>Weekly = 2</li>
          <li>Flex = 3</li>
          <li>Undefined = 4</li>
          <li>Mini = 5</li>
          <li>NonStandard = 6</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>ExpirationType = 0</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>Here's the final template for this API request:

```text
GET apiURL/v1.0/options/optionChain/AAPL?filter=Range%20%3D%201%20
```

### Response

In response to this API request, you will receive an option chain filtered according to the specified query:

```text
{
  "Expirations": [
    {
      "Expiration": "2020-09-18T00:00:00Z",
      "CentralStrike": 320,
      "Options": [
        {
          "Id": 19358441,
          "Symbol": "AAPL  200918C00320000",
          "Description": "CALL Apple Inc. $320 EXP 09/18/20",
          "Exchange": "OPRAC",
          "Currency": "USD",
          "AddedDate": "2019-08-02T16:31:52.7125148Z",
          "ModifyDate": "2019-10-29T13:13:44.6562343Z",
          "Type": "Option",
          "Precision": 2,
          "VolumePrecision": 0,
          "TickSize": 0.01,
          "Enabled": true,
          "AllowTrade": true,
          "AllowMargin": true,
          "AllowShort": true,
          "OptionType": "Call",
          "ExpirationType": "Regular",
          "ExpirationDate": "2020-09-18T00:00:00Z",
          "StrikePrice": 320,
          "SeriesId": 103,
          "UnderlyingAssetSymbol": "AAPL",
          "ContractSize": 100
        },
        {
          "Id": 20303472,
          "Symbol": "AAPL  200918C00320000",
          "Description": "CALL Apple Inc. $320 EXP 09/18/20",
          "Currency": "USD",
          "AddedDate": "2019-10-23T14:07:32.9789618Z",
          "ModifyDate": "2019-10-23T14:07:32.9789618Z",
          "Type": "Option",
          "Precision": 2,
          "VolumePrecision": 0,
          "TickSize": 0.01,
          "Enabled": true,
          "AllowTrade": true,
          "AllowMargin": true,
          "AllowShort": true,
          "OptionType": "Call",
          "ExpirationType": "Regular",
          "ExpirationDate": "2020-09-18T00:00:00Z",
          "StrikePrice": 320,
          "SeriesId": 103,
          "UnderlyingAssetSymbol": "AAPL",
          "ContractSize": 100
        },
        {
          "Id": 20303475,
          "Symbol": "AAPL  200918P00320000",
          "Description": "PUT Apple Inc. $320 EXP 09/18/20",
          "Currency": "USD",
          "AddedDate": "2019-10-23T14:07:32.9789618Z",
          "ModifyDate": "2019-10-23T14:07:32.9789618Z",
          "Type": "Option",
          "Precision": 2,
          "VolumePrecision": 0,
          "TickSize": 0.01,
          "Enabled": true,
          "AllowTrade": true,
          "AllowMargin": true,
          "AllowShort": true,
          "OptionType": "Put",
          "ExpirationType": "Regular",
          "ExpirationDate": "2020-09-18T00:00:00Z",
          "StrikePrice": 320,
          "SeriesId": 103,
          "UnderlyingAssetSymbol": "AAPL",
          "ContractSize": 100
        },
        {
          "Id": 19358441,
          "Symbol": "AAPL  200918C00320000",
          "Description": "CALL Apple Inc. $320 EXP 09/18/20",
          "Exchange": "OPRAC",
          "Currency": "USD",
          "AddedDate": "2019-08-02T16:31:52.7125148Z",
          "ModifyDate": "2019-10-29T13:13:44.6562343Z",
          "Type": "Option",
          "Precision": 2,
          "VolumePrecision": 0,
          "TickSize": 0.01,
          "Enabled": true,
          "AllowTrade": true,
          "AllowMargin": true,
          "AllowShort": true,
          "OptionType": "Call",
          "ExpirationType": "Regular",
          "ExpirationDate": "2020-09-18T00:00:00Z",
          "StrikePrice": 320,
          "SeriesId": 103,
          "UnderlyingAssetSymbol": "AAPL",
          "ContractSize": 100
        },
        {
          "Id": 19358443,
          "Symbol": "AAPL  200918P00320000",
          "Description": "PUT Apple Inc. $320 EXP 09/18/20",
          "Exchange": "OPRAC",
          "Currency": "USD",
          "AddedDate": "2019-08-02T16:31:52.7125148Z",
          "ModifyDate": "2019-10-29T13:13:44.6562343Z",
          "Type": "Option",
          "Precision": 2,
          "VolumePrecision": 0,
          "TickSize": 0.01,
          "Enabled": true,
          "AllowTrade": true,
          "AllowMargin": true,
          "AllowShort": true,
          "OptionType": "Put",
          "ExpirationType": "Regular",
          "ExpirationDate": "2020-09-18T00:00:00Z",
          "StrikePrice": 320,
          "SeriesId": 103,
          "UnderlyingAssetSymbol": "AAPL",
          "ContractSize": 100
        },
        {
          "Id": 19358443,
          "Symbol": "AAPL  200918P00320000",
          "Description": "PUT Apple Inc. $320 EXP 09/18/20",
          "Exchange": "OPRAC",
          "Currency": "USD",
          "AddedDate": "2019-08-02T16:31:52.7125148Z",
          "ModifyDate": "2019-10-29T13:13:44.6562343Z",
          "Type": "Option",
          "Precision": 2,
          "VolumePrecision": 0,
          "TickSize": 0.01,
          "Enabled": true,
          "AllowTrade": true,
          "AllowMargin": true,
          "AllowShort": true,
          "OptionType": "Put",
          "ExpirationType": "Regular",
          "ExpirationDate": "2020-09-18T00:00:00Z",
          "StrikePrice": 320,
          "SeriesId": 103,
          "UnderlyingAssetSymbol": "AAPL",
          "ContractSize": 100
        },
        {
          "Id": 20303472,
          "Symbol": "AAPL  200918C00320000",
          "Description": "CALL Apple Inc. $320 EXP 09/18/20",
          "Currency": "USD",
          "AddedDate": "2019-10-23T14:07:32.9789618Z",
          "ModifyDate": "2019-10-23T14:07:32.9789618Z",
          "Type": "Option",
          "Precision": 2,
          "VolumePrecision": 0,
          "TickSize": 0.01,
          "Enabled": true,
          "AllowTrade": true,
          "AllowMargin": true,
          "AllowShort": true,
          "OptionType": "Call",
          "ExpirationType": "Regular",
          "ExpirationDate": "2020-09-18T00:00:00Z",
          "StrikePrice": 320,
          "SeriesId": 103,
          "UnderlyingAssetSymbol": "AAPL",
          "ContractSize": 100
        },
        {
          "Id": 20303475,
          "Symbol": "AAPL  200918P00320000",
          "Description": "PUT Apple Inc. $320 EXP 09/18/20",
          "Currency": "USD",
          "AddedDate": "2019-10-23T14:07:32.9789618Z",
          "ModifyDate": "2019-10-23T14:07:32.9789618Z",
          "Type": "Option",
          "Precision": 2,
          "VolumePrecision": 0,
          "TickSize": 0.01,
          "Enabled": true,
          "AllowTrade": true,
          "AllowMargin": true,
          "AllowShort": true,
          "OptionType": "Put",
          "ExpirationType": "Regular",
          "ExpirationDate": "2020-09-18T00:00:00Z",
          "StrikePrice": 320,
          "SeriesId": 103,
          "UnderlyingAssetSymbol": "AAPL",
          "ContractSize": 100
        }
      ]
    }
  ]
}
```

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve option chains.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

