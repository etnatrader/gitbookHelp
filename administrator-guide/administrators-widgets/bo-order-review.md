# Order Reviews

### Introduction

By default, all placed orders in ETNA Trader are automatically executed without prior approval from the user's administrator. Consequently, users can place market, limit, and stop-loss orders without any limitations which might lead to unintended consequences like amateur traders selling options or trading on margin. For this reason ETNA traders offers comprehensive order review functionality that enables administrators to configure meticulous rules for each user.

### Understanding Order Review

There are two components to order reviews:

1. Risk rule designer in the ETNA Trader's administrator portal.
2. Order Review Panel in the ETNA Trader's web terminal.

The risk rule designer is located at **admin.yourWebTerminal.com**, and it allows you to create order review rules for all of your users. For example, you can create a rule that will force all orders places on the London Stock Exchange to first be reviewed by administrators. Also, you can automatically reject all orders placed during pre- or post-market hours — the range of possible conditions is quite extensive.

Once the rules are set in place, the administrators in your company will have to review all orders whose characteristics satisfy the conditions in one of those rules. Until the suspended order is reviewed, users will see the following message after placing the order: 

![](../../.gitbook/assets/screenshot-2019-01-30-at-18.09.56.png)

The notifications for such orders will contain the following text:

![](../../.gitbook/assets/screenshot-2019-01-30-at-18.09.30.png)

### Configuring Risk Rules

The first step in configuring the order review is to go to the ETNA Trader's administrator portal \(**admin.yourWebTerminal.com**\) and sign in using your special credentials \(they're different from the user or administrator credentials\).

{% hint style="warning" %}
ETNA Trader's administrator portal requires your computer to have Microsoft SilverLight installed, and it can only be accessed through Internet Explorer.
{% endhint %}



