---
description: Fetch information about a particular option by providing its ticker symbol
---

# Get Option Info by Ticker

## Overview

This GET endpoint enables you to retrieve information about a particular option by providing the option's ticker symbol in the request's header. Whereas the first three methods in the _Securities_ section deal with equities' information, this endpoint provides information exclusively about options.

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/). The value of this header must have the following format: `Bearer BQ898r9fefi` \(`Bearer` + 1 space + the token\).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. symbol \(path\). This is the ticker symbol of the option whose information you'd like to retrieve. This ticker symbol can be fetched using the [API request that lists filtered options](../get-filtered-options/).

Here's the final template for this API request:

```text
GET apiURL/v1.0/options/VSSQ1 260117P00008000
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

<table>
  <thead>
    <tr>
      <th style="text-align:left">Parameter</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Id</td>
      <td style="text-align:left">This is the internal ID of the security in ETNA Trader.</td>
    </tr>
    <tr>
      <td style="text-align:left">Symbol</td>
      <td style="text-align:left">
        <p>This is the ticker symbol under which the option is listed on the exchange.
          Note that the length of this parameter must be equal for all options, and
          this is achieved by adding spaces between the underlying ticker and the
          option&apos;s details (the underlying ticker + the spaces must add up to <code>6</code>).
          For example:</p>
        <ul>
          <li><code>V     210618C00195000</code>. Notice the <b>five</b>  <b>spaces</b> between <code>V</code> and <code>2</code>.
            Underlying ticker (<code>1</code>) + spaces (<code>5</code>) = <code>6</code>.</li>
          <li><code>AAPL  210618C00195000</code>. Notice the <b>two spaces</b> between <code>AAPL</code> and <code>2</code>.
            Underlying ticker (<code>4</code>) + spaces (<code>2</code>) = <code>6</code>.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Description</td>
      <td style="text-align:left">Usually this is the full name of the underlying company.</td>
    </tr>
    <tr>
      <td style="text-align:left">Exchange</td>
      <td style="text-align:left">This is the exchange on which the security is listed.</td>
    </tr>
    <tr>
      <td style="text-align:left">Currency</td>
      <td style="text-align:left">This is the currency in which the security is denominated.</td>
    </tr>
    <tr>
      <td style="text-align:left">AddedDate</td>
      <td style="text-align:left">This is the date on which the security was added to the database.</td>
    </tr>
    <tr>
      <td style="text-align:left">ModifyDate</td>
      <td style="text-align:left">This is the date in which the security&apos;s information was last modified.</td>
    </tr>
    <tr>
      <td style="text-align:left">Type</td>
      <td style="text-align:left">This is the type of the security &#x2014; option in the case of this API
        request.</td>
    </tr>
    <tr>
      <td style="text-align:left">Precision</td>
      <td style="text-align:left">This is the number of decimal places in the security&apos;s price.</td>
    </tr>
    <tr>
      <td style="text-align:left">VolumePrecision</td>
      <td style="text-align:left">This is the number of decimal places in the security&apos;s trading volume
        (might be useful for cryptocurrencies).</td>
    </tr>
    <tr>
      <td style="text-align:left">TickSize</td>
      <td style="text-align:left">This is the minimum price change of the security. For example, if this
        property equals 0.01 for AAPL, the minimum price change for AAPL is 0.01
        (150.67 &#x2014;&gt; 150.68, but not 150.675). For securities with the
        market price of less than $1, the TickSize is equal to 0.0001.</td>
    </tr>
    <tr>
      <td style="text-align:left">Enabled</td>
      <td style="text-align:left">This field indicated if the security is enabled and can be traded by users.</td>
    </tr>
    <tr>
      <td style="text-align:left">AllowTrade</td>
      <td style="text-align:left">This field indicates is the security if permitted for trading.</td>
    </tr>
    <tr>
      <td style="text-align:left">AllowMargin</td>
      <td style="text-align:left">This field indicates if the security is allowed to be traded on margin.</td>
    </tr>
    <tr>
      <td style="text-align:left">AllowShort</td>
      <td style="text-align:left">This field indicates if the security can be sold short.</td>
    </tr>
    <tr>
      <td style="text-align:left">OptionType</td>
      <td style="text-align:left">This is the type of option. Possible values: call, put.</td>
    </tr>
    <tr>
      <td style="text-align:left">ExpirationType</td>
      <td style="text-align:left">This is the expiration type of the option. Possible values: Regular, Quarterly,
        Weekly, Flex, Undefined, Mini, NonStandard.</td>
    </tr>
    <tr>
      <td style="text-align:left">ExpirationDate</td>
      <td style="text-align:left">This is the expiration date of the option.</td>
    </tr>
    <tr>
      <td style="text-align:left">StrikePrice</td>
      <td style="text-align:left">This is the price at which the holder of the option can buy or sell the
        underlying asset.</td>
    </tr>
    <tr>
      <td style="text-align:left">SeriesId</td>
      <td style="text-align:left">This is the internal ID of the option series in ETNA Trader.</td>
    </tr>
    <tr>
      <td style="text-align:left">UnderlyingAssetSymbol</td>
      <td style="text-align:left">This is the ticker symbol of the underlying asset.</td>
    </tr>
    <tr>
      <td style="text-align:left">ContractSize</td>
      <td style="text-align:left">This is the deliverable quantity of the option&apos;s underlying asset.</td>
    </tr>
  </tbody>
</table>

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to retrieve an option's information by their ticker symbol.

### Mistaking the Character Count in Symbol

An extremely common mistake when calling this endpoint is not ensuring that the combined character count of the underlying ticker and the following spaces is `6`. If it's anything other than `6`, the request will fall through.

For example:

* `V     210618C00195000`. Notice the **five** **spaces** between `V` and `2`. Underlying ticker \(`1`\) + spaces \(`5`\) = `6`.
* `AAPL  210618C00195000`. Notice the **two spaces** between `AAPL` and `2`. Underlying ticker \(`4`\) + spaces \(`2`\) = `6`.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

### Specifying the Underlying Security's Ticker instead of the Option's Ticker Symbol

Another common mistake in retrieving information about a particular option is specifying the underlying security's ticker symbol instead of the enquired option's ticker symbol. Doing so will lead to the 409 status code.

The following article covers the syntax for this API request in detail.

