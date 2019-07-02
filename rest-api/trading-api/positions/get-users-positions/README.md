---
description: List all existing positions of a user
---

# Get User's Positions

## Overview

This GET endpoint enables you to list all existing positions of the user whose authorization token was used in the request's path.

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to get this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/requesting-tokens/).
3. **Trading Account ID** \(path\). This is the numeric ID of the trading account whose positions must be listed. 
4. **API version** \(path\). Unless necessary, leave it at "1.0".

There's also one optional parameter worth examining:

* filter \(query\). This is an SQL query used to retrieve only those positions that satisfy the conditions of the query. The following table outlines the parameter's syntax.

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
          <li>CreateDate (&gt;, &gt;=, &lt;, &lt;=) Date</li>
          <li>CreateDate between Range</li>
        </ul>
      </td>
      <td style="text-align:left">This query enables you to retrieve positions that were created in the
        time period specified in the Range parameter or exactly at the time specified
        in the Date parameter.</td>
      <td style="text-align:left">
        <ul>
          <li>CreateDate between #2019-03-13T18:31:42# and #2019-03-17T18:31:42#</li>
          <li>CreateDate &gt;= #2019-03-13T18:31:42#</li>
          <li>CreateDate &lt; #2019-03-12T19:31:42#</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>ModifyDate (&gt;, &gt;=, &lt;, &lt;=) Date</li>
          <li>ModifyDate between Range</li>
        </ul>
      </td>
      <td style="text-align:left">This query enables you to retrieve positions that were modified in the
        time period specified in the Range parameter or exactly at the time specified
        in the Date parameter.</td>
      <td style="text-align:left">
        <ul>
          <li>ModifyDate between #2019-03-13T18:31:42# and #2019-03-17T18:31:42#</li>
          <li>ModifyDate &gt;= #2019-03-13T18:31:42#</li>
          <li>ModifyDate &lt; #2019-03-12T19:31:42#</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Quantity (&gt;, &gt;=, &lt;, &lt;=) Number</li>
          <li>Quantity between Range</li>
        </ul>
      </td>
      <td style="text-align:left">This query enables you to retrieve positions with the number of securities
        being in the range indicated in the Range parameter or equal to the number
        in the Number parameter.</td>
      <td style="text-align:left">
        <ul>
          <li>Quantity = 100</li>
          <li>Quantity &gt;= 100</li>
          <li>Quantity between 100 and 1000</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>SecurityId = Number</li>
        </ul>
      </td>
      <td style="text-align:left">This query enables you to retrieve positions whose securityId parameter
        is equal to the Id provided in the query.</td>
      <td style="text-align:left">
        <ul>
          <li>SecurityId = 4</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Symbol = String</li>
        </ul>
      </td>
      <td style="text-align:left">This query enables you to retrieve positions whose underlying security&apos;s
        ticker symbol is equal to the string provided in the query.</td>
      <td style="text-align:left">
        <ul>
          <li>Symbol = &apos;AAPL&apos;</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>{% hint style="info" %}
Note that you can combine different queries to create more complex requests:

* SecurityId = 4 and CreateDate &gt;= \#2019-03-13T18:31:42\#
{% endhint %}

Here's the final template for this API request:

```text
GET apiURL/v1.0/accounts/{accountID}/positions?pageNumber=0&pageSize=10&sortField=Id&desc=true&filter=CreateDate%20between%20%232019-03-13T18%3A31%3A42%23%20and%20%232019-03-17T18%3A31%3A42%23
```

## Response

In response to this API request, you'll receive a JSON file with all of the user's existing positions. Following is an example of such response:

```javascript
[
    {
        "Id": 21483,
        "AccountId": 6303,
        "SecurityId": 4,
        "Symbol": "AAPL",
        "Name": "AAPL",
        "CompanyName": "Apple Inc.",
        "SecurityCurrency": "USD",
        "SecurityType": "CommonStock",
        "ContractSize": 1,
        "CostBasis": 23485.5,
        "DailyCostBasis": 25414.5,
        "CreateDate": "2019-01-22T14:30:03.7328576Z",
        "ModifyDate": "2019-01-22T14:30:03.7328576Z",
        "Quantity": 150,
        "RealizedProfitLoss": 0,
        "AverageOpenPrice": 156.57,
        "AverageClosePrice": 0,
        "StopLossPrice": 0,
        "TakeProfitPrice": 0,
        "DailyCloseProfitLoss": 0,
        "ExcessChanges": 0,
        "DayQuantity": 0,
        "MarketValueEOD": 645.19
    }
]
```

where:

| Parameter | Description |
| :--- | :--- |
| Id | This is the internal ID of the position |
| AccountID | This is the account ID that was provided in the request's header |
| SecurityId | This is the internal ID of the underlying security in the position |
| Symbol | This is the ticker symbol |
| Name | In most cases this field is identical to Symbol |
| CompanyName | This is the full name of the listed company |
| SecurityCurrency | This is the currency in which the security is denominated |
| SecurityType | This is the type of the underlying security.  The range of possible values is listed in the following table. |
| ContractSize | This is the minimum contract size for this financial instrument. |
| CostBasis | This is the average execution price multiplied by the number of shares |
| DailyCostBasis | This is the gross market value of all transactions in this order |
| CreateDate | This is the date on which the order was created |
| ModifyDate | This is the date on which the order was last modified |
| Quantity | This is the number of shares in the order |
| RealizedProfitLoss | This is the realized profit or loss of this position |
| AverageOpenPrice | The average opening price of all positions. This variable is calculated for positions of the same type — either Long or Short \(you can't simultaneously open a long and a short position on the same instrument\) |
| AverageClosePrice | The average closing price of all positions. This variable is calculated for positions of the same type — either Long or Short \(you can't simultaneously open a long and a short position on the same instrument\) |
| StopLossPrice | This the price at which the position should be terminated \(if this price point is reached\) |
| TakeProfitPrice | This is the price point at which the profit should be realized \(if this price point is reached\). |
| DailyCloseProfitLoss | This is the gross profit or loss of all trades of this security made during the current trading session. |
| Excess Changes | This indicates how much this position affects your account's excess. |
| DayQuantity | This is the gross number of shares of this security that have been traded during the current trading session. |
| MarketValueEOD | This is the market value of the position registered at the end of the previous trading session. |

### Security Type

```text
BankersAcceptance                     = 0,
CertificateOfDeposit                  = 1,
CollateralizeMortgageObligation       = 2,
CorporateBond                         = 3,
CommercialPaper                       = 4,
CorporatePrivatePlacement             = 5,
CommonStock                           = 6,
FederalHousingAuthority               = 7,
FederalHomeLoan                       = 8,
FederalNationalMortgageAssociation    = 9,
ForeignExchangeContract               = 10,
Future                                = 11,
GovernmentNationalMortgageAssociation = 12,
TreasuriesPlusAgencyDebenture         = 13,
MutualFund                            = 14,
MortgageInterestOnly                  = 15,
MortgagePrincipleOnly                 = 16,
MortgagePrivatePlacement              = 17,
MiscellaneousPassThru                 = 18,
MunicipalBond                         = 19,
NoIsitcSecurityType                   = 20,
Option                                = 21,      
PreferredStock                        = 22,
RepurchaseAgreement                   = 23,
ReverseRepurchaseAgreement            = 24,
StudentLoanMarketingAssociation       = 25,
TimeDeposit                           = 26,
UsTreasuryBill                        = 27,
Warrant                               = 28,
CatsTigersLions                       = 29,
WildcardEntry                         = 30,
ConvertibleBond                       = 31,
MortgageIoette                        = 32,
Index                                 = 33,
FakeStockForNonStandartOption         = 34,
Right                                 = 35,
Cryptocurrency                        = 36,
ETF                                   = 37,
DepositoryReceipt                     = 38,
CoveredWarrant                        = 39,
Unit                                  = 40
```

## Common Mistakes

Here are some of the common mistakes that developers make when attempting to list the existing positions.

### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

### Specifying the User ID Instead of the Trading Account ID

Another common mistake when making this request is specifying the user ID instead of the user's trading account ID. Doing so will result in the 500 status code and the following error message:

```javascript
{
    "message": "An error occurred while processing your request",
    "error": "Unexpected server error"
}
```

### Specifying a Trading Account of a Different User

It's critical to understand that when you use the authorization token of a particular user in this request's header, only this user's trading accounts can be used for listing current positions. Placing a new order on a trading account of a different user will lead to the 401 error.

```javascript
{
    "Message": "Authorization has been denied for this request."
}
```

In the following article we provide in-depth coverage of the syntax for this API request.

