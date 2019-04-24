---
description: Learn how to analyze faulty orders
---

# Inability to Place a New Order

### Introduction

ETNA Trader sometimes rejects a new order because it was determined to be invalid by some internal order validator. There are numerous validators on the platform, ranging from fat finger validators to initial margin rate validators. Each order must go through all order validators before being sent to the execution venue. If an order fails even one validator, it will be rejected by the system, and the trader will see the following error message:

* Web terminal:

![](../../.gitbook/assets/screenshot-2019-04-18-at-20.46.54.png)

* Mobile app:

![](../../.gitbook/assets/img_0065_iphonexspacegrey_portrait.png)

### Order Validators in ETNA Trader

The following table lists the most common order validators and their descriptions. 

#### Verification Order Errors <a id="CodesAndValues-VerificationOrderErrors.1"></a>

| Error Message | Description |
| :--- | :--- |
| AccountDisabled | This trading account is prohibited for trading. Please contact ETNA Trader's support team at [support@etnasoft.com](mailto:support@etnasoft.com). |
| AccountDoesNotBelongToUser | You cannot trade from this account, as it does not belong to you. |
| AccountIsNotApproved | This account is not approved for trading. Please contact ETNA Trader's support team at [support@etnasoft.com](mailto:support@etnasoft.com). |
| AccountMarginRuleViolation | Margin rules prohibit this transaction. Please contact our trade desk. |
| AonOrderQuantity | You cannot place All-or-none orders with the number of securities lower than 2. |
| AssetTradingNotConfiguredForAccount | You cannot trade this type of asset on this trading account. |
| BuyStopOrderStopPriceLessAsk | Buy-side stop orders must have a stop price greater than the Ask price. |
| ContingentOrderExecution | Placement condition is invalid |
| DayTraderPatternRestriction | Your day trade limit has been exceeded. |
| DayTradingBuyingPowerExceeded | Your trading account does not have sufficient day trading buying power. |
| ExpirationDateUndefined | Expiration date for this option is not defined. |
| FatFingersOptionsSizeExceedsMaximum | The number of contracts in the orders exceeds the maximum number of contracts allowed. Learn more [here](../how-to-guides/back-office/configuring-fat-finger-rules.md). |
| FatFingersStockSizeExceedsMaximum | The number of securities in the order exceeds the maximum number of shares allowed. Learn more [here](../how-to-guides/back-office/configuring-fat-finger-rules.md). |
| FatFingersTradeBands | The difference between order's price and the mark price is higher than allowed. Learn more [here](../how-to-guides/back-office/configuring-fat-finger-rules.md). |
| FatFingersValueExceedsMaximum | Order value exceeds the maximum amount permitted. |
| FuturesDeniedForMlegOrders | Multi-leg option strategy can't have a leg with a futures contract. |
| Gt | Greater than |
| IncorrectOrderQuantity | The number of securities should be between 1 and 10,000,000. |
| IncorrectTimeInForce | Time In Force \(Day or GTC\) is not defined. |
| IndexOptionsOneExparyDate | Multi Leg Orders with Index options must have all legs within 1 expiration date. Time spreads are not allowed on Index Options. |
| InitialMargin | You do not have enough buying power for this trade. |
| InvalidOrderExpiration | Expiration date must be greater than the current date. |
| LimitPriceUndefined | Limit price is not defined. |
| LongOptionTradingDeniedForAccount | Account is restricted for option trading. |
| LongPositionCrossZero | You cannot sell more shares than your effective long position \(effective long position = long position less open sell orders\) using one order ticket. Industry regulations require that two order tickets be submitted: one to sell your effective long position and one to open your desired short position. |
| Lt | Lower than |
| MaintenanceMargin | You do not have enough buying power for this trade. |
| MarketOrderIsGtc | You cannot place market orders with GTC, only day orders are allowed. |
| OcoExpirationTypeNotTheSame | Expiration type of OCO orders must be the same. |
| OcoOrderWithOppositeLegs | You cannot place OCO order with orders for the same security and with opposite trade directions. |
| OcoPriceDifferenceIsLessThanDelta | The OCO order's legs' price difference should be lower. |
| OmsInternalError | The order service could not process the order \(unknown error\). |
| OmsUnavailable | Sorry, the order service is not available, please try again later. |
| OptionLevelRestriction | The required minimum equity balance is not met or you may not have permissions to place this trade. Please contact the Trade Desk for further assistance. |
| OptionTypeUndefined | Type of option \(call or put\) is not defined. |
| OrderContingentChangeNotAllowed | Change of order's contingent is not allowed. |
| OrderIsNotAllowedForAccount | This operations is not allowed for this account. Trading operations allowed: closing orders only. |
| OrderPriceIsInvalid | The specified price is invalid.  |
| OrderQuantity | You cannot place orders with quantity less than 1. |
| OrderWithDifferentSide | You cannot have pending orders with different sides for selected symbol where one is a MARKET order. You must close another pending order in order to place a SHORT order, or try a limit order instead. |
| OtoFirstLesIsMarketNotAllowed | First market order in OTO is not allowed. |
| OtoOcoForex\_NonForexAreNotAllowed | OTO/OCO orders with combination of Forex and non-Forex securities are not allowed |
| OtoOcoMarketNotAllowed | OCO market orders are not allowed. |
| OtoOcoTrailingNotAllowed | OTO/OCO trailing orders are not allowed. |
| PennyPilotDivisionPrice | The price must be divisible by {number}. |
| PositionLocked | Position is locked. |
| PriceOutOfMarket | The limit order's price is invalid relative to the current market price. |
| PricePrecisionIsOutOfRange | Price increment cannot be smaller than $0.01 if Price is equal to or greater than $1.00 per share and smaller than $0.0001 if Price is less than $1.00 per share. |
| QuantityConsistency | Maximum quantity precision is {number}. |
| QuotePriceIsInvalid | Quotes for this security are unavailable. Please try placing your order again later. |
| SecurityUndefined | The security with the specified symbol does not exist. |
| SellShortOrderLastPriceBelow5 | Sell Short order cannot be placed for stock priced below $5. |
| SellStopOrderStopPriceGreaterBid | Sell Stop order must have a Stop price less than the Bid price. |
| ShortOptionTradingDeniedForAccount | Account is prohibited from opening short positions in options. |
| ShortOrderIsGtc | You cannot place short stock orders with GTC, only day orders are allowed. |
| ShortPositionCrossZero | You cannot buy \(to cover\) more shares than your effective short position \(effective short position = short position plus open buy orders\) using one order ticket. Industry regulations require that two order tickets be submitted: one to cover your effective short position and one to buy your desired long position. |
| ShortStockTradingDeniedForAccount | Account is prohibited from opening short positions in stocks. |
| ShortTradingDeniedForSecurity | This symbol is not available for shorting. Please contact our trade desk. |
| SnapQuoteIsInvalid | Failed to get snap quotes. |
| SpreadTradingDeniedForAccount | Account is restricted for spread trading. |
| StopPriceUndefined | Stop price is not defined. |
| StrikePriceUndefined | Strike price for option leg is not defined. |
| TickSizePilotDivisionLimitPrice | The limit price is not a multiple of {number} US-Finra Tick Size Pilot Program. |
| TickSizePilotDivisionStopPrice | The stop price is not a multiple of {number} US-Finra Tick Size Pilot Program. |
| TooSmallEquityForDayTrading | Pattern Day Trader Rule violation: Equity balance fell below $25,000. |
| TotalInitialMargin | You do not have enough buying power for this trade. |
| TradeNonStandartOptions | You cannot place an order with non standard options. |
| TradeOptionAfter1pmAtExpirationDay | Orders for options that expire today are limited to closing transactions only after 1 p.m. EST |
| TradeOTC | You cannot place order on OTCBB or Pinks Securities. |
| TradingDeniedForAccount | Account is restricted for trading. |
| TradingDeniedForSecurity | This asset class is restricted for trading. |
| TradingIsNotAllowedForAccount | Trading using this account is not allowed. |
| UnexpectedBuyOrder | Buy order cannot be placed for short position or if there are pending Sell Short orders. |
| UnexpectedBuyOrderOption | Buy To Open order cannot be placed for short position if there are pending Sell To Open orders. |
| UnexpectedBuyToCoverOrder | Buy To Cover order cannot be placed for long or flat positions. |
| UnexpectedBuyToCoverOrderOption | Buy To Close order cannot be placed for long or flat positions. |
| UnexpectedSellOrder | Sell order cannot be placed for short or flat positions. |
| UnexpectedSellOrderOption | Sell To Close order cannot be placed for short and flat positions. |
| UnexpectedSellShortOrder | Sell Short order cannot be placed for long positions or if there are pending Buy orders. |
| UnexpectedSellShortOrderOption | Sell To Open order cannot be placed for long positions if there are pending Buy To Open orders. |
| UnsupportedOrderSide | Specified order side is not supported. |
| UserDisabled | Account is prohibited from trading. Please contact our support team. |
| WashTradeAttempt | You cannot place orders on the same security and with the same price but in different directions. |

### 

