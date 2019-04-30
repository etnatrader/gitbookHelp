---
description: Retrieve all positions of a user in a particular security
---

# Get User's Positions in a Security

### Overview

This GET endpoint enables you to list all positions in a particular security of the user whose authorization token was used in the request's body. 

There are five required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\). 
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../../authentication/).
3. **Trading Account ID** \(path\). This is the numeric ID of the trading account whose positions in a particular security must be listed. 
4. **API version** \(path\). Unless necessary, leave it at "1.0".
5. **Ticker Symbol** \(path\). This is the ticker symbol of the security whose positions you'd like to list. 

Here's the final template for this API request:

```text
GET apiURL/v1.0/accounts/{accountID}/positions/AAPL
```

### Response

In response to this API request, you'll receive a JSON file with all of the user's positions in the security. Following is an example of such response:

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
        "DailyCostBasis": 25422,
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
        "DayQuantity": 0
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
| CompanyName | This is the full name of the listed company  |
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

#### Security Type

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

### Common Mistakes

Here are some of the common mistakes that developers make when attempting to list a user's positions in a particular security. 

#### Failing to Specify the Et-App-Key Parameter

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```javascript
{
    "error": "Application key is not defined or does not exist"
}
```

#### Specifying the User ID Instead of the Trading Account ID

Another common mistake when making this request is specifying the user ID instead of the user's trading account ID. Doing so will result in the 500 status code and the following error message:

```javascript
{
    "message": "An error occurred while processing your request",
    "error": "Unexpected server error"
}
```

#### Specifying the Internal ID of the Security instead of the Ticker

Bear in mind that this request requires the ticker symbol of the security \(as displayed on the exchange\) and not the internal ID in ETNA Trader. Specifying the internal ID will lead to the 500 status code and the following error message:

```javascript
{
    "message": "An error occurred while processing your request",
    "error": "Unexpected server error"
}
```

The following article covers the syntax for this API request in detail.

