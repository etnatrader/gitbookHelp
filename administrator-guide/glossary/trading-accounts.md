---
description: Learn in-depth about trading accounts in ETNA Trader
---

# Trading Accounts

### Introduction

In ETNA Trader, a trading account is a separate entity used for performing trades. Whenever you need to purchase or sell some security, you must have an active trading account that was approved by a clearing firm that handles the confirmation, settlement, and delivery of transactions. The clearing firm can also reject trades if, for example, the account's equity falls below a certain level.

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

### Cash

Cash indicates the amount of funds that the account's user can withdraw or spend to open new positions. 

### NetCash

NetCash represents the amount of available funds adjusted for the option maintenance margin. It is calculated according to the following formula:

$$
NetCash = Cash - OptionMaintenanceMargin
$$

### Base Cash

Base cash is an indicator that is retrieved daily from the clearing firm.

### Pending Cash

Pending Cash indicates the amount of money that is reserved to carry out current transactions. This reserve is withheld from the Cash parameter and it is calculated as the sum of the transaction commission and the cost of the securities purchased during the transaction.

$$
Pending Cash = Σ Commissions + ΣOrderCost
$$

### Account Value

Account value represents the sum of the available Cash and the aggregate market value of all long and short positions.

$$
AccountValue = Cash + Market Value
$$

### Market Value

Market Value represents the sum of four other trading account parameters:

1. stockLongMarketValue — the aggregate market value of all long positions in stocks.
2. stockShortMarketValue — the aggregate market value of all short positions in stocks.
3. optionLongMarketValue — the aggregate market value of all long positions in options.
4. optionShortMarketValue — the aggregate market value of all short positions in options.

$$
MarketValue = stockLongMarketValue + stockShortMarketValue + optionLongMarketValue + optionShortMarketValue
$$

### Excess

Excess represents the available funds that can be used to open new positions. This is a base parameter that is retrieved daily from the clearing firm. Throughout the trading session, this parameter is calculated differently depending on the configuration of your environment:

* **Default**

$$
Excess = Cash + StockMarketValue - MaintenanceMargin - PendingCash
$$

* **Real-time Excess**

$$
Excess=Cash+StockMarketValue−MaintenanceMargin−PendingCash
$$

* **Excess with Unsettled Cash**

$$
Excess = Base Cash - UnsettledCash - PendingCash
$$

### Excess Back

Excess back is in most cases identical to **Base Cash** except for the **Real-time Excess** configuration where it is calculated as:

$$
ExcessBack = Equity - MaintenanceMargin
$$

### Equity

Equity represents the sum of Cash and the net market value of all positions in stocks:

$$
Equity = Cash + StockMarketValue
$$

### Stock Market Value

Stock market value is calculated as the net market value of all positions is stocks. The aggregate market value of all long stock positions is added to the aggregate market value of all short stock positions.

$$
StockMarketValue = StockLongMarketValue + StockShortMarketValue
$$

### Day Trades

Day trades is the number of day trades that have been executed on this trading account during the last five trading sessions \(including the current one\).

### Stock Buying Power

This is the gross number of stocks that can be purchased on this trading account, adjusted for the available margin debt. 

$$
StockBuyingPower = Excess / MarginRate
$$

### Option Buying Power

This is the gross number of options that can be purchased on this trading account, adjusted for the available margin debt. 

$$
OptionBuyingPower = Excess
$$

### Day Trading Buying Power

Day trading buying power is a critical indicator that represents the amount of funds that the user can spend to open new positions. At the beginning of every trading session, this value is retrieved from the clearing firm. Throughout the trading session, Day Trading Buying Power fluctuates based on the performed trades — it decreases with each new long position and it increases with each position closing.

It's calculated differently for stocks and options. For stocks, when you open a new long position, Day Trading Buying Power decreases according to the following formula:

$$
DayTradingBuyingPower -=  OrderCost * 4 * MarginRate + Commission * 4
$$

where:

| Parameter | Description |
| :--- | :--- |
| OrderCost | This is the cost of the order calculated as the order price multiplied by the number of purchased securities. |
| 4 | Because brokers let their users borrow up to three times as much money to finance positions, the buying power of the entire account has to be decreased by the position cost multiplied by four \(1 is the user's funds and 3 is the margin debt\). |
| MarginRate | This is the fraction of funds that the user must contribute if they're using margin debt. |
| Commission | This is the commission that was applied to this order.  |

{% hint style="info" %}
Please note that the cost of the margin debt provided by the broker is not taken into account when calculating Day Trading Buying Power.
{% endhint %}

### Net Liquidity

Net liquidity is identical to Market Value.

### Maintenance Margin

Maintenance margin represents the minimum amount of equity that should be maintained in a margin account.

### Option Maintenance Margin

This is the minimum amount of equity that must be maintained on the trading account in order to cover the existing option positions.

### OpenPL

OpenPL stands for **Open Profit/Loss** and it represents the amount of unrealized profit or loss of the trading account at the opening of the current trading session.

### ClosePL

ClosePL stands for **Close Profit/Loss** and it represents the amount of unrealized profit or loss of the trading account at the closing of the current trading session.

### Status

This is the current status of the trading account. The range of possible account statuses is as follows:

* **New** — the trading account has been created;
* **SentToClearing** — the trading account has been sent to the clearing firm;
* **Approved** — the trading account has been approved by the clearing firm;
* **Rejected** — the trading account has been rejected by the clearing firm.

### MarginInterestRate

Margin interest rate is the interest rate applied to the funds borrowed to finance margin positions.

### OwnerType

This is the type of the trading account's owner. The range of possible account statuses is as follows:

* **IndividualCustomer** = 0
* **InstitutionalCustomer** = 1, 
* **Combined** = 2, 
* **EmployeeAccount** = 3, 
* **MarketMaking** = 4,
* **OtherProprietary** = 5, 
* **Unknown** = 6, 
* **ErrorAccount** = 7.

### Maintenance Call

This field indicates the amount of funds that need to be deposited into the account in order to prevent a maintenance call.

### Equity Call

This field indicates the amount of funds that need to be deposited into the account in order to prevent a minimum equity call.

### Initial Call

This field indicates the amount of funds that need to be deposited into the account in order to prevent an initial call.

### Day Trade Call

This field indicates the amount of funds that need to be deposited into the account in order to prevent a day trade call.

### Trade Day Balance

Trade Day Balance represents the amount of funds this trading account owes to the broker.

### Cip

Cip is the Carriage and Insurance Paid To \(CIP\). This value is retrieved daily from the clearing firm.

### SmaBalance

SmaBalance is the amount of funds in a special memorandum account. This value is retrieved daily from the clearing firm.

### Option Level

Option level indicates which operations with options are permitted on this account. 

### ChangeAbsolute

ChangeAbsolute indicates the difference between the current market value of all positions less their market value at the closing of the previous trading session. 

### ChangePercent

ChangeAbsolute indicates the difference between the current market value of all positions less their market value at the closing of the previous trading session expressed in percentage terms.

