---
description: List all trading accounts registered within your company
---

# List All Accounts

### Overview

This GET endpoint enables you to retrieve the list of all trading accounts that have been created by the users of your company. All accounts are split into pages, each of which can be individually retrieved with the help of this endpoint.

{% hint style="warning" %}
In order to list all trading accounts of your company, you must use an [authorization token](../authentication/) of an administrator. Using authorization tokens of regular users will lead to the 401 status code.
{% endhint %}

There are four required parameters that must be provided in the request:

1. **Et-App-Key** \(header\). This is the unique key of your app that identifies your app when communicating with our service. It can be found it in the **BO Companies** widget. When editing the company's settings, navigate to the **WebApi** tab and look for the required key \(it could be a key for the web terminal, the mobile app, or a custom key\).
2. **Authorization** \(header\). This is the authorization token from the very first [token request](../authentication/).
3. **API version** \(path\). Unless necessary, leave it at "1.0".
4. **pageSize** \(query\). This field indicates the number of trading accounts that need to be retrieved per page.
5. **pageNumber** \(query\). This field indicates the number of the page that needs to be retrieved \(all trading accounts are split into a set of pages that can be loaded one by one\).
6. **propertyName** \(query\). This is the field by which the retrieved trading accounts should be sorted. For example, if the value of this parameter is set to **Cash**, the retrieved trading accounts will be sorted by the accounts' cash balance.
7. **isAscending** \(query\). This field indicates if the list of retrieved trading accounts should be sorted in the descending \(false\) or ascending \(true\) order.

Here's the final template for this API request:

```text
GET apiURL/v1.0/accounts
```

### Response

In response to this API request, you'll receive a JSON file with the list of trading accounts sorted by the field that was specified in the **propertyName** parameter in the request query.

```javascript
{
  "Result": [
    {
      "Id": 1945,
      "SubscriptionPlanId": 0,
      "ClearingAccount": "1945",
      "CreatedDate": "2016-06-08T16:29:49.893Z",
      "ModifiedDate": "2019-03-10T11:01:22.5939919Z",
      "Enabled": true,
      "IsChanged": false,
      "Cash": -39784716,
      "Currency": "USD",
      "Status": "Approved",
      "MarginInterestRate": 0,
      "CashInterestRate": 0,
      "CloseEquity": -39784716,
      "OpenExcess": -39784716,
      "OptionLevel": 4,
      "MarginType": "Margin",
      "Permissions": "LongStock, ShortStock, LongOption, ShortOption, AllowTrade, AllowMargin, AllowOpen",
      "BaseCash": -39784716,
      "Sweep": 0,
      "OwnerType": "IndividualCustomer",
      "DayTradingBuyingPower": -159138864,
      "DayTrades": 0,
      "SmaBalance": 0,
      "HouseCall": 0,
      "MaintenanceCall": 0,
      "EquityCall": 0,
      "InitialCall": 0,
      "DayTradeCall": 0,
      "TradeDayBalance": -39397110,
      "MoneyMarket": 0,
      "Cip": 0,
      "IsAverageAccount": false,
      "MarginEquity": -39784716,
      "ExcessEquity": 0
    },
    {
      "Id": 4216,
      "SubscriptionPlanId": 0,
      "ClearingAccount": "4216",
      "CreatedDate": "2018-05-10T09:20:30.0711982Z",
      "ModifiedDate": "2019-02-04T12:03:56.1767255Z",
      "Enabled": true,
      "IsChanged": false,
      "Cash": -8999000.77433717,
      "Currency": "USD",
      "Status": "Approved",
      "MarginInterestRate": 0,
      "CashInterestRate": 0,
      "CloseEquity": -8285522.31067809,
      "OpenExcess": -8285522.31067809,
      "OptionLevel": 4,
      "MarginType": "Cash",
      "Permissions": "LongStock, ShortStock, LongOption, ShortOption, AllowTrade, AllowMargin, AllowOpen",
      "BaseCash": -8285522.31067809,
      "Sweep": 0,
      "OwnerType": "IndividualCustomer",
      "DayTradingBuyingPower": -33142089.24271235,
      "DayTrades": 0,
      "SmaBalance": 0,
      "HouseCall": 0,
      "MaintenanceCall": 0,
      "EquityCall": 0,
      "InitialCall": 0,
      "DayTradeCall": 0,
      "TradeDayBalance": -8999000.77433717,
      "MoneyMarket": 0,
      "Cip": 0,
      "IsAverageAccount": false,
      "MarginEquity": -8285522.31067809,
      "ExcessEquity": 0
    },
    {
      "Id": 3225,
      "SubscriptionPlanId": 0,
      "ClearingAccount": "3225",
      "CreatedDate": "2017-04-25T14:39:14.257Z",
      "ModifiedDate": "2019-03-10T11:03:04.9904706Z",
      "Enabled": true,
      "IsChanged": false,
      "Cash": -2923219,
      "Currency": "USD",
      "Status": "Approved",
      "MarginInterestRate": 0,
      "CashInterestRate": 0,
      "CloseEquity": -2923219,
      "OpenExcess": -11692876,
      "OptionLevel": 4,
      "MarginType": "DayTrader",
      "Permissions": "LongStock, ShortStock, LongOption, ShortOption, AllowTrade, AllowMargin, AllowOpen",
      "BaseCash": -2923219,
      "Sweep": 0,
      "OwnerType": "IndividualCustomer",
      "DayTradingBuyingPower": -11692876,
      "DayTrades": 0,
      "SmaBalance": 0,
      "HouseCall": 0,
      "MaintenanceCall": 0,
      "EquityCall": 0,
      "InitialCall": 0,
      "DayTradeCall": 0,
      "TradeDayBalance": -2923219,
      "MoneyMarket": 0,
      "Cip": 0,
      "IsAverageAccount": false,
      "MarginEquity": -2923219,
      "ExcessEquity": 0
    }
  ],
  "NextPageLink": "https://priv-api-etnatrader-dev.etnasoft.us/api/v1.0/accounts?pageNumber=1&pageSize=3&propertyName=Cash&isAscending=true",
  "PreviousPageLink": "",
  "TotalCount": 6671
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
      <td style="text-align:left">Result</td>
      <td style="text-align:left">This is an array that contains the requested trading accounts.</td>
    </tr>
    <tr>
      <td style="text-align:left">Id</td>
      <td style="text-align:left">This is the internal identifier of the trading account that was provided
        in the request path.</td>
    </tr>
    <tr>
      <td style="text-align:left">SubscriptionPlanId</td>
      <td style="text-align:left">This is an internal field in ETNA Trader and it shouldn&apos;t be used
        by third-party developers.</td>
    </tr>
    <tr>
      <td style="text-align:left">ClearingAccount</td>
      <td style="text-align:left">This is the id of this account at the clearing firm.</td>
    </tr>
    <tr>
      <td style="text-align:left">CreatedDate</td>
      <td style="text-align:left">This is the date on which the trading account was created.</td>
    </tr>
    <tr>
      <td style="text-align:left">ModifiedDate</td>
      <td style="text-align:left">This is the date on which the trading account was last modified.</td>
    </tr>
    <tr>
      <td style="text-align:left">Enabled</td>
      <td style="text-align:left">This field indicates if the trading account is enabled.</td>
    </tr>
    <tr>
      <td style="text-align:left">IsChanged</td>
      <td style="text-align:left">This is an internal field in ETNA Trader and it shouldn&apos;t be used
        by third-party developers.</td>
    </tr>
    <tr>
      <td style="text-align:left">Cash</td>
      <td style="text-align:left">This is the amount of funds on the trading account that the user can expend
        on new positions.</td>
    </tr>
    <tr>
      <td style="text-align:left">Currency</td>
      <td style="text-align:left">This is the currency of the trading account. At the moment only US dollars
        are supported.</td>
    </tr>
    <tr>
      <td style="text-align:left">Status</td>
      <td style="text-align:left">
        <p>This is the status of the trading account. Possible values:</p>
        <ul>
          <li>New &#x2014; the trading account has been created;</li>
          <li>SentToClearing &#x2014; the trading account has been sent to the clearing
            firm;</li>
          <li>Approved &#x2014; the trading account has been approved by the clearing
            firm;</li>
          <li>Rejected &#x2014; the trading account has been rejected by the clearing
            firm.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MarginInterestRate</td>
      <td style="text-align:left">This is the interest rate applied to the funds borrowed to finance margin
        positions.</td>
    </tr>
    <tr>
      <td style="text-align:left">CashInterestRate</td>
      <td style="text-align:left">This is an obsolete field and it shouldn&apos;t be used by third-party
        developers.</td>
    </tr>
    <tr>
      <td style="text-align:left">CloseEquity</td>
      <td style="text-align:left">This is the trading account&apos;s equity before the start of a new trading
        session (calculated based on the closing price of the previous trading
        session).</td>
    </tr>
    <tr>
      <td style="text-align:left">OpenExcess</td>
      <td style="text-align:left">This field indicates the account&apos;s excess funds calculated at the
        opening of the trading session.</td>
    </tr>
    <tr>
      <td style="text-align:left">OptionLevel</td>
      <td style="text-align:left">This field indicates which operations with options are permitted on this
        account.</td>
    </tr>
    <tr>
      <td style="text-align:left">MarginType</td>
      <td style="text-align:left">This is the account type. Read more about it <a href="../../../administrator-guide/administrators-widgets/managing-users/#trading-accounts">here</a>.</td>
    </tr>
    <tr>
      <td style="text-align:left">Permissions</td>
      <td style="text-align:left">
        <p>This field lists the operations permitted on this trading account. Possible
          values:</p>
        <ul>
          <li>LongStock &#x2014; opening long positions in stocks is permitted;</li>
          <li>ShortStock &#x2014; opening short positions in stocks is permitted;</li>
          <li>LongOption &#x2014; opening long positions in options is permitted;</li>
          <li>ShortOption &#x2014; opening short positions in options is permitted;</li>
          <li>AllowTrade &#x2014; trading is permitted;</li>
          <li>AllowMargin &#x2014; trading on margin is permitted;</li>
          <li>AllowOpen &#x2014; opening positions on this account is permitted.</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">BaseCash</td>
      <td style="text-align:left">This is the trading account&apos;s excessive funds that are used for calculating
        DayTradingBuyingPower.</td>
    </tr>
    <tr>
      <td style="text-align:left">Sweep</td>
      <td style="text-align:left">This is an internal field and it shouldn&apos;t be used by third-party
        developers.</td>
    </tr>
    <tr>
      <td style="text-align:left">OwnerType</td>
      <td style="text-align:left">
        <p>This is the type of the trading account&apos;s owner. Possible values:</p>
        <ul>
          <li>IndividualCustomer = 0</li>
          <li>InstitutionalCustomer = 1,</li>
          <li>Combined = 2,</li>
          <li>EmployeeAccount = 3,</li>
          <li>MarketMaking = 4,</li>
          <li>OtherProprietary = 5,</li>
          <li>Unknown = 6,</li>
          <li>ErrorAccount = 7</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DayTradingBuyingPower</td>
      <td style="text-align:left">This is the amount of funds that can be employed to make trades on day
        trading accounts. Usually the value of this field is equal to <em>BaseCash</em> multiplied
        by four.</td>
    </tr>
    <tr>
      <td style="text-align:left">DayTrades</td>
      <td style="text-align:left">This is the number of active day trades on the account.</td>
    </tr>
    <tr>
      <td style="text-align:left">SmaBalance</td>
      <td style="text-align:left">This is the amount of funds in a special memorandum account.</td>
    </tr>
    <tr>
      <td style="text-align:left">HouseCall</td>
      <td style="text-align:left">This field indicates the amount of funds that need to be deposited into
        the account in order to prevent a house call.</td>
    </tr>
    <tr>
      <td style="text-align:left">MaintenanceCall</td>
      <td style="text-align:left">This field indicates the amount of funds that need to be deposited into
        the account in order to prevent a maintenance call.</td>
    </tr>
    <tr>
      <td style="text-align:left">EquityCall</td>
      <td style="text-align:left">This field indicates the amount of funds that need to be deposited into
        the account in order to prevent a minimum equity call.</td>
    </tr>
    <tr>
      <td style="text-align:left">InitialCall</td>
      <td style="text-align:left">This field indicates the amount of funds that need to be deposited into
        the account in order to prevent an initial call.</td>
    </tr>
    <tr>
      <td style="text-align:left">DayTradeCall</td>
      <td style="text-align:left">This field indicates the amount of funds that need to be deposited into
        the account in order to prevent a day trade call.</td>
    </tr>
    <tr>
      <td style="text-align:left">TradeDayBalance</td>
      <td style="text-align:left">This is the amount of funds that the trading account owes to the broker.</td>
    </tr>
    <tr>
      <td style="text-align:left">MoneyMarket</td>
      <td style="text-align:left">These are the money market funds on the trading account.</td>
    </tr>
    <tr>
      <td style="text-align:left">Cip</td>
      <td style="text-align:left">This is the Carriage and Insurance Paid To (CIP).</td>
    </tr>
    <tr>
      <td style="text-align:left">IsAverageAccount</td>
      <td style="text-align:left">This field indicates if this trading account is used to allocate shares
        to other trading accounts.</td>
    </tr>
    <tr>
      <td style="text-align:left">MarginEquity</td>
      <td style="text-align:left">This is the portion of the account&apos;s equity that was purchased on
        margin.</td>
    </tr>
    <tr>
      <td style="text-align:left">ExcessEquity</td>
      <td style="text-align:left">This is the withdrawable portion of the equity.</td>
    </tr>
    <tr>
      <td style="text-align:left">NextPageLink</td>
      <td style="text-align:left">This is the next page of trading accounts.</td>
    </tr>
    <tr>
      <td style="text-align:left">PreviousPageLink</td>
      <td style="text-align:left">This is the previous page of trading accounts.</td>
    </tr>
    <tr>
      <td style="text-align:left">TotalCount</td>
      <td style="text-align:left">This is the total number of trading accounts within the company.</td>
    </tr>
  </tbody>
</table>### Common Mistakes

Here are some of the common mistakes that developers make when attempting to list a company's trading accounts.

#### Requesting as a Non-Administrator

One of the most common mistakes that developers make when making this API request is to use the authorization token of a non-administrator. It's critical to understand that in order to be eligible for listing a company's trading accounts, the requester must be an administrator. Otherwise you'll receive the 401 status code with the following message:

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



