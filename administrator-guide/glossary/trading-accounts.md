---
description: Learn in-depth about trading accounts in ETNA Trader
---

# Trading Accounts

### Introduction

In ETNA Trader, a trading account is a separate entity used for performing trades. Whenever you need to purchase or sell some security, you must have an active trading account that was approved by a clearing firm who handles the confirmation, settlement, and delivery of transactions. The clearing firm can also reject trades if, for example, the account's equity falls below a certain level.

Trading accounts are distinct from users, as one user might have multiple trading accounts and vice versa. For example, a user might have separate trading accounts for stock trading, options trading, and Forex trading. Similarly, one trading account might have multiple associated users. For example, all members of a family are using the same account to place orders.

Trading accounts can be created in one of the two following ways:

1. Through ETNA Trader's [web terminal](../administrators-widgets/managing-users/#trading-accounts);  

   ![](../../.gitbook/assets/screenshot-2019-03-13-at-15.01.24.png) 

2. Through our [private REST API](../../rest-api/private-api/internal-accounts/create-a-new-trading-account.md).

As an administrator, you need to review each newly created trading account before ETNA Trader sends it for review to the clearing firm. After the account is approved by the clearing firm, it is becomes active and can be used to perform trades.

### Account Types

All trading accounts fall into one of the three FINRA-defined types: _Cash_, _Margin_, and _Day Trader_. 

| Account  Type | Description |
| :--- | :--- |
| Cash | This type of account only permits trading operations with the trader's funds  without the ability to trade on margin. Cash accounts are not allowed to open short positions and write call and put options \(except for covered calls\). |
| Margin | In addition to personal funds, margin accounts permit trading with borrowed money. As per FINRA's requirements, the owner of a margin account can trade on margin only if their equity is no less than $2'000. If the owner's equity falls below the $2'000 mark due to market fluctuations, the account is automatically converted to _Cash_. If at that point the account has any short or margin positions, the owner will get a required maintenance call. |
| Day Trader | This type of margin account is aimed at day traders and allows them to buy and sell the same security on the same trade date. To qualify for the day trader account, the owner of the account should have at least $25'000 of equity. If the equity falls below the $25'000 mark due to market fluctuations, the owner of the account will get an equity maintenance call the next business day. |

Each of these types has its own requirements; if they are not met, the account becomes inactive and the user can no longer perform trades.

![](../../.gitbook/assets/screenshot-2019-03-13-at-15.22.15.png)

### Account Access Level

If you've created a new trading account, it's not automatically available to any of your company's users — it has to be bound to each user individually. Binding trading accounts to users can be done through:

* **BO Users** widget

  ![](../../.gitbook/assets/screenshot-2019-03-13-at-15.49.39.png) 

* ETNA Trader's [private REST API](../../rest-api/private-api/internal-accounts/bind-an-account-to-a-user.md).

During the binding process, you have to specify the access level that the user must have when operating this trading account.

| Access Level Value | Permissions |
| :--- | :--- |
| Full | **Full**. All operations are allowed. |
| ReadOnly | **Read Only**. The user can only examine the existing orders and positions \(without having the ability to place new orders or modify the existing ones\). |
| ClosePositionsOnly | **Close Positions Only**. The user can only close the positions without the ability to open new ones. |

{% hint style="info" %}
Access Level Value must be specified only when an account is bound to a user via ETNA Trader's [REST API](../../rest-api/private-api/internal-accounts/bind-an-account-to-a-user.md).
{% endhint %}

### Trading Account Parameters

Each trading account consists of an array of different parameters, some of which are retrieved from the clearing firm — **base parameters** — while others are dynamically calculated based on the aforementioned base parameters.

Some these parameters can be examined in the **Account Info** widget.

![](../../.gitbook/assets/screenshot-2019-03-13-at-17.52.30.png)

Let's examine each of these parameters in detail.

#### Cash

Cash indicates the amount of funds that the account's user can withdraw or spend to open new positions. 

#### Pending Cash

Pending Cash indicates the amount of money that is reserved to carry out current transactions. This reserve is withheld from the Cash parameter and it is calculated as the sum of the transaction commission and the cost of the securities purchased during the transaction.

$$
Pending Cash = Cash - Commissions - OrderCost
$$

#### Account Value

Account value represents the sum of the available Cash and the aggregate market value of all long and short positions.

$$
AccountValue = Cash + Market Value
$$

#### Market Value

Market Value represents the sum of four other trading account parameters:

1. stockLongMarketValue — the aggregate market value of all long positions in stocks.
2. stockShortMarketValue — the aggregate market value of all short positions in stocks.
3. optionLongMarketValue — the aggregate market value of all long positions in options.
4. optionShortMarketValue — the aggregate market value of all short positions in options.

$$
MarketValue = stockLongMarketValue + stockShortMarketValue + optionLongMarketValue + optionShortMarketValue
$$

#### Base Cash

Base cash indica

#### 

#### 

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
      <td style="text-align:left">CommissionPlan</td>
      <td style="text-align:left">This is the commission plan (as provided by the clearing firm).</td>
    </tr>
    <tr>
      <td style="text-align:left">RepCode</td>
      <td style="text-align:left">This is a commission-related field (as provided by the clearing firm).</td>
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
      <td style="text-align:left">This is the account type. Read more about it <a href="../administrators-widgets/managing-users/#trading-accounts">here</a>.</td>
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
      <td style="text-align:left">ClearingFirm</td>
      <td style="text-align:left">This is the clearing firm that handles this trading account.</td>
    </tr>
    <tr>
      <td style="text-align:left">ExcessEquity</td>
      <td style="text-align:left">This is the withdrawable portion of the equity.</td>
    </tr>
  </tbody>
</table>



