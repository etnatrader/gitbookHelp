---
description: Retrieve a trading account's collective market value of all security groups
---

# Get Market Value of all Security Groups

### Introduction‌ <a id="introduction"></a>

This GET endpoint enables you to retrieve the collective market value of different security groups in a specific trading account.‌

There are five required parameters that must be provided in the request:‌

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. Contact your administrator to retrieve this key.
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **accountID** \(path\). This is the internal ID of the trading account whose market value of different security groups must be listed.‌

Here's the final template for this API request:

```text
GET apiURL/v1.0/accounts/{accountID}/positions/groups
```

## Response <a id="response"></a>

In response to this API request, you'll receive a JSON file with the collective market value of different security groups in the specified trading account.

```javascript
[
  {
    "Name": "Options",
    "MarketValue": -996.5
  },
  {
    "Name": "Equity",
    "MarketValue": 129835.86
  },
  {
    "Name": "Cash",
    "MarketValue": 342377.84999484
  }
]
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
      <td style="text-align:left">Name</td>
      <td style="text-align:left">
        <p>The security group.</p>
        <p>Possible values:</p>
        <ul>
          <li>FixedIncome</li>
          <li>Equity</li>
          <li>Forex</li>
          <li>Futures</li>
          <li>Other</li>
          <li>Options</li>
          <li>Index</li>
          <li>Cryptocurrency</li>
          <li>Cash</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MarketValue</td>
      <td style="text-align:left">The collective market value of all securities of this group in this trading
        account.</td>
    </tr>
  </tbody>
</table>#### Relationship Between Security Types and Groups

The following table lists security types that populate each security group:

<table>
  <thead>
    <tr>
      <th style="text-align:left">Security Group</th>
      <th style="text-align:left">Corresponding Security Types</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">FixedIncome</td>
      <td style="text-align:left">
        <ul>
          <li>BankersAcceptance</li>
          <li>CertificateOfDeposit</li>
          <li>MortgageObligation</li>
          <li>CorporateBond</li>
          <li>CommercialPaper</li>
          <li>CorporatePrivatePlacement</li>
          <li>FederalHousingAuthority</li>
          <li>FederalHomeLoan</li>
          <li>FederalNationalMortgageAssociation</li>
          <li>GovernmentNationalMortgageAssociation</li>
          <li>TreasuriesPlusAgencyDebenture</li>
          <li>MortgageInterestOnly</li>
          <li>MortgagePrincipleOnly</li>
          <li>MortgagePrivatePlacement</li>
          <li>MunicipalBond</li>
          <li>StudentLoanMarketingAssociation</li>
          <li>TimeDeposit</li>
          <li>UsTreasuryBill</li>
          <li>CatsTigersLions</li>
          <li>ConvertibleBond</li>
          <li>MortgageIoette</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Equity</td>
      <td style="text-align:left">
        <ul>
          <li>CommonStock</li>
          <li>MutualFund</li>
          <li>PreferredStock</li>
          <li>Warrant</li>
          <li>Right</li>
          <li>ETF</li>
          <li>DepositoryReceipt</li>
          <li>CoveredWarrant</li>
          <li>Unit</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Forex</td>
      <td style="text-align:left">
        <ul>
          <li>ForeignExchangeContract</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Futures</td>
      <td style="text-align:left">
        <ul>
          <li>Future</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Options</td>
      <td style="text-align:left">
        <ul>
          <li>Option</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Index</td>
      <td style="text-align:left">
        <ul>
          <li>Index</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Cryptocurrency</td>
      <td style="text-align:left">
        <ul>
          <li>Cryptocurrency</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">Other</td>
      <td style="text-align:left">
        <ul>
          <li>MiscellaneousPassThru</li>
          <li>NoIsitcSecurityType</li>
          <li>RepurchaseAgreement</li>
          <li>ReverseRepurchaseAgreement</li>
          <li>WildcardEntry</li>
          <li>FakeStockForNonStandartOption</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>### Common Mistakes

Here are some of the common mistakes that developers make when attempting to fetch the collective market value of different security groups in a specific trading account.‌

### Failing to Specify the Et-App-Key Parameter <a id="failing-to-specify-the-et-app-key-parameter"></a>

If you specify the wrong Et-App-Key parameter or fail to include it in the header altogether, you'll get the following error:

```text
{    "error": "Application key is not defined or does not exist"}
```

### Specifying the User ID Instead of the Trading Account ID <a id="specifying-the-user-id-instead-of-the-trading-account-id"></a>

Another common mistake when making this request is specifying the user ID instead of the user's trading account ID. Doing so will result in the 500 status code and the following error message:

```text
{    "message": "An error occurred while processing your request",    "error": "Unexpected server error"}
```

