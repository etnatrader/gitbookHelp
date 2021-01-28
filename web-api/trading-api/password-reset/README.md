---
description: Reset the password of a trader
---

# Password Reset

### Resetting Traders' Password via API

In ETNA Trader, the process of resetting a trader's passwords consists of four steps:

1. Determining whether this trader must provide the answer to a secret question.
2. Resetting the password by providing the answer to the secret question \(if neccessary\).
3. Confirming the trader's intention to reset the password by sending a verification code to their email address.
4. Updating the old password.

The following diagram provides the step-by-step algorithm for resetting the password of a trader:

![](../../../.gitbook/assets/screenshot-2021-01-28-at-16.09.33.png)

Once you understand the password reset workflow, proceed to retrieve the trader's secret question:

{% page-ref page="2.-retrieve-the-secret-question.md" %}

