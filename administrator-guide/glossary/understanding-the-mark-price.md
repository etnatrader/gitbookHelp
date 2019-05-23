---
description: Learn how the mark price is calculated in ETNA Trader
---

# Mark Price

### Introduction

In ETNA Trader, various components use the so-called **Mark price** as the standard reference for the current market price of a specific security. For example, the [Fat Finger rules](../../knowledge-base/how-to-guides/back-office/configuring-fat-finger-rules.md) validate orders based on various conditions, including the discrepancy between the stop/limit price and the **mark price**. Similarly, many other components of the platform use the mark price to get the current price of a security; therefore, it's important to understand how it's calculated

Let's explore how the mark price is calculated in ETNA Trader.

### Understanding the Mark Price

The mark price in ETNA Trader is calculated separately for stocks and options.

#### Stocks

<table>
  <thead>
    <tr>
      <th style="text-align:left">Trading Session</th>
      <th style="text-align:left">Mark Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">Trading Hours</td>
      <td style="text-align:left">
        <p>If Bid &lt; LastPrice &lt; Ask:</p>
        <ul>
          <li></li>
        </ul>
        <p>If Last &gt;= Ask:</p>
        <ul>
          <li></li>
        </ul>
        <p>If Last &lt;= Bid:</p>
        <ul>
          <li></li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">After-Market Hours</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Pre-Market Hours</td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left">Non-trading Hours</td>
      <td style="text-align:left"></td>
    </tr>
  </tbody>
</table>As you can notice, the mark price is calculated differently depending on the current trading session. Also, during the regular trading hours, the mark price varies based on the difference between the last price and the bid/ask price.

#### Options

<table>
  <thead>
    <tr>
      <th style="text-align:left">Trading Session</th>
      <th style="text-align:left">Mark Price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">All trading sessions</td>
      <td style="text-align:left">
        <p></p>
        <ul>
          <li></li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>For options, the mark price is calculated identically during all trading sessions.

