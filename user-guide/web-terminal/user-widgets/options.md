# Options

### Exploring the Option Chain Widget

![](../../../.gitbook/assets/screenshot-2019-04-24-at-18.39.43.png)

### Greeks

Various sophisticated hedging strategies are used to neutralize or decrease the effects of risk when taking a position in an option.

![](../../../.gitbook/assets/screenshot-2019-04-24-at-18.42.50.png)

### Calls and Puts

There are two types of options: calls and puts. Furthermore, there are four types of participants in options markets depending on the position they take: 

1. Buyers of calls;
2. Sellers of calls; 
3. Buyers of puts; 
4. Sellers of puts.

![](../../../.gitbook/assets/screenshot-2019-04-24-at-18.45.50.png)

### Intrinsic value and Time

One of the columns of the _Option Chain_ widget is entitled **Mark** and it contains the current mark price of the option. Please note that this column is available only for Call and Put options.

 As you hover over the column with the option's strike price, the following pop-up will be prompted:

![](../../../.gitbook/assets/options.png)

The pop-up contains two parameters: 

1. **Intrinsic**

\*\*\*\*$$Intrinsic = StockMark - Strike$$ ****

The `Intrinsic` parameter is calculated as the difference between the underlying security's mark price and the option's strike price.

   ****2. **Time**

\*\*\*\*$$Time = Option Mark - Intrinsic$$ ****

The `Time` parameter is calculated as the difference between the option's mark price and the **Intrinsic** parameter.

