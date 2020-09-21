# Mutual Funds

### Introduction

Mutual funds are a popular investment vehicle for investors who wish to delegate the responsibility of managing their funds to a group of professional investment managers that run these funds. The nature of mutual funds somewhat differs from stocks and bonds that can simply be purchased and sold on the exchange. Specifically, mutual funds can be exchanged or liquidated, the dividends received by the mutual fund from its holdings can be further reinvested or distributed back to the stockholder, etc. 

Furthermore, mutual funds have their own technicalities like the time of order execution, order processing workflow, supported quantity qualifiers, etc. And in this article we will clarify the implementation of mutual funds trading in ETNA Trader before you proceed to use our API.

### Mutual Funds Trading Schedule

During the night, from 12 AM to 9:30 AM Eastern Time, ETNA Trader collects the ticker symbols and quotes for all available mutual funds. 

Mutual fund orders are accepted from 9:30 AM ET until the cut-off time \(defined by the broker during deployment\). 

Prior to the start of the following trading session, positions in mutual funds will either appear or disappear depending on the order's type and status.

### Order Placement Rules

Before a mutual fund order can be placed, first ensure that the following requirements are met:

| Parameter | Requirements |
| :--- | :--- |
| Order type | Strictly **Market**. |
| Order duration | Strictly **Day**. |
| Order quantity | Integer or a fractional number. |
| Account Type | Not an average price account. |

### Mutual Fund Quote Updates

The quotes for all available mutual funds are updated daily before the start of each trading session.

### Mutual Fund Order Processing

Whenever a new mutual fund order is placed, its status is initially set to **New** \(0\) and its execution status is set to **Stopped** \(7\). Both statuses persist until the end of the trading session at which point the order's status becomes either filled or rejected.

### Reinvestment of Proceeds

ETNA Trader enables investors to instruct mutual fund managers to either distribute the dividends and capital gains back to the investor or, alternatively, further reinvest them. This can be achieved by setting three parameters to `true` in the payload of the [corresponding API request](buy-a-mutual-fund.md):

* [x] ReinvestDividends
* [x] ReinvestShortTermGains
* [x] ReinvestLongTermGains

### Supported Mutual Fund Operations

As of now, ETNA Trader supports all standard mutual fund operations:

#### Purchasing Mutual Funds

{% page-ref page="buy-a-mutual-fund.md" %}

#### Selling Mutual Funds

{% page-ref page="sell-a-mutual-fund.md" %}

#### Exchanging One Mutual Fund For Another

{% page-ref page="exchange-a-mutual-fund.md" %}

#### Full Liquidation of a Mutual Fund

{% page-ref page="liquidate-a-mutual-fund.md" %}

