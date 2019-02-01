# Types of Conditions

### Conditions

In ETNA Trader, each risk rule can have multiple conditions, and an order must simultaneously satisfy all conditions of an active rule before it is detected by the system and then sent for review. There are a total of 29 different conditions that can be specified in each rule.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-16.50.44.png)

#### **1. Account**

Use this condition to apply the order review mechanism only to specific trading accounts. You can specify multiple accounts, and this rule will be applied to all of them. Alternatively, you can specify to which accounts this rule should not be applied by selecting the **NotIn** option.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-17.14.25%20%281%29.png)

#### **2. Average Daily Volume**

Use this condition to apply the order review mechanism only to to those trading accounts whose average daily volume exceeds or is less than the specified amount. Gt refers to "greater" while Lt refers to "less than".

![](../../../.gitbook/assets/screenshot-2019-01-31-at-17.50.28.png)

#### 3. Clearing Firm

Use this condition to apply the order review mechanism only to those trading accounts who belong to a particular clearing firm that is indicated in the the text field. Alternatively, you can enforce this rule for all accounts except for the specified by selecting **NotIn** in the drop-down menu.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-17.51.28%20%282%29.png)

#### 4. Day Loss

Use this condition to apply the order review mechanism only to those trading accounts whose current day loss is greater than or equal to the specified amount.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-18.04.28.png)

#### 5. **Days to Expiration**

Use this condition to apply the order review mechanism to the options whose expiration date is exactly the specified number of days from now.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-18.07.13.png)

#### 6. Exchange Destination ???

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.59.19.png)

#### 7. Exchange Working Hours

Use this condition to apply the order review mechanism to all orders placed during specific trading hours. For example, you can use this rule to review all orders placed during the pre- and post-market hours.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-18.12.51%20%281%29.png)

#### 8. Execution Instructions 

Use this condition to apply the order review mechanism to all orders that must either be executed entirely or not at all. 

{% hint style="info" %}
Options **DoNotIncrease** and **DoNotReduce** are currently unavailable.
{% endhint %}

![](../../../.gitbook/assets/screenshot-2019-01-31-at-18.22.54.png)

#### 9. Execution Venue

Use this condition to apply the order review mechanism to all orders that should be placed on the selected exchanges \(the list of options may vary depending on which exchanges are available to your company\).

![](../../../.gitbook/assets/screenshot-2019-01-31-at-19.02.45.png)

#### 10. Extended Hours

Use this condition to apply the order review mechanism to all orders that are placed during extended market hours.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-19.24.05.png)

#### 11. Extended Hours Exchange Working Hours ???

Use this condition to apply the order review mechanism to all orders that are placed ???

![](../../../.gitbook/assets/screenshot-2019-01-31-at-19.27.20.png)

#### 12. Is Halted Security

Use this condition to apply the order review mechanism to all orders in which the underlying security is suspended from trading by the relevant exchange.  

![](../../../.gitbook/assets/screenshot-2019-01-31-at-19.28.29.png)

#### 13. Is contingent ??? 

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.29.44.png)

#### 14. Legs Quantity

Use this condition to apply the order review mechanism to all multi-leg option orders. A multi-leg order is a type of order used to buy or sell options with more than one strike price, expiration date, or sensitivity to the underlying security's price. In the text field you should specify the number of legs of an order that should be flagged and sent for review.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.30.15.png)

#### 15. Margin Requirement Cash ??? 

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.30.50.png)

#### 16. Opening/Closing Order

Use this condition to apply the order review mechanism to all orders that are either opening a new position or closing an existing position.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.33.57.png)

#### 17. Option Expiration Type

Use this condition to apply the order review mechanism to all option orders with a particular expiration type. Alternatively, you could apply the order review mechanism to all expiration types except for the selected ones by selecting the **NotIn** option.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.34.52.png)

#### 18. Order Duration 

Use this condition to apply the order review mechanism to all orders with a particular duration. There are three duration types to choose from:

1. **Day**. This rule will only be applied to orders that expire at the end of the current trading session. 
2. **GoodTillCancel**. This rule will only be applied to orders that are active until cancelled.
3. **GoodTillDate**. This rule will only be applied to orders that expire at a particular date.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.36.33.png)

#### 19. Order Fields

Use this condition to apply the order review mechanism to all orders where particular fields have been modified. This rule might be useful in preventing placement of orders with fields that are not supported on particular exchanges.

Some of these fields are not available in the web terminal and can only be used when invoking our external API.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.37.37.png)

#### 20. Order Side

Use this condition to apply the order review mechanism to all orders with a particular trade side. There are four options to choose from:

1. **Buy**. These are the types of orders that concern buying securities.
2. **Sell**. These are the types of orders that concern selling securities.
3. **SellShort**. These are the types of orders in which a trader is selling the broker's shares in an attempt to buy them back cheaper, and return those shares with interest back to the broker while pocketing the profit from the security price depreciation.
4. **BuyToCover**. These are the types of orders in which a trader is buying back the shares they had previously sold short \(to return the shares back to the broker\).

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.38.25.png)

#### 21. Order Total 

Use this condition to apply the order review mechanism to all orders whose total price \(number of shares multiplied by the limit price\) exceeds or is less than the specified amount. For example, if you set the order total  to $100'000, whenever one of your users places an order with a higher total price, that order will be flagged and sent for review.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.39.05.png)

#### 22. Order Type

Use this condition to apply the order review mechanism to all orders of a specific type. There are six options to choose from:

1. **Market**. These are the types of orders in which securities are purchased at market price.
2. **Limit**. These are the types of orders in which securities are purchased at a specified price \(or better\).
3. **Stop**. These are the types of orders in which securities are automatically purchased or sold when their price moves past a certain point.
4. **StopLimit**. These are the types of orders in which securities should be purchased or sold once the security's price has reached the target, at which point the order is converted into a stop order.
5. **Pegged**. These are the types of orders in which securities are purchased at the bid or ask price offset by a certain amount. 

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.40.00.png)

#### 23. Overall Quantity

Use this condition to apply the order review mechanism to all orders in which the total number of shares exceeds or is less than the specified value. 

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.43.30.png)

#### 24. Price

Use this condition to apply the order review mechanism to all orders in which the target price is equal to, not equal to, exceeds, exceeds or equal to, is less than, is less than or equal to the specified value.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.44.47.png)

#### 25. Quantity

Use this condition to apply the order review mechanism to all orders in which the number of shares exceeds or is less than the specified value.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.45.16.png)

#### 26. Security

Use this condition to apply the order review mechanism to all orders in which the underlying security is specified in this condition. For example, you can use this rule to review all trades of the stocks that you deem extremely volatile.

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.46.04.png)

#### 27. Security Exchange

Use this condition to apply the order review mechanism to all orders that are placed on the specified stock exchanges. 

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.47.01.png)

#### 28. Security Exchange Working Hours ???

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.47.37.png)

#### 29. Security Type

Use this condition to apply the order review mechanism to all orders that concern specific security types. Alternatively, you can review all securities by default except for the selected ones by selecting the **NotIn** option in the second drop-down menu

![](../../../.gitbook/assets/screenshot-2019-01-31-at-20.48.26.png)

Once all the conditions are configured, you can close the rules creation window and they will automatically be applied to all new trades whose characteristics satisfy the conditions in these rules.

