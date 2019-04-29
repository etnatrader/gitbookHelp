---
description: Get started with ETNA Trader's extended REST API
---

# Overview

### Introduction <a id="introduction"></a>

ETNA Trader's Broker API mimics the functionality of administrator widgets. Namely, you can invoke the API to perform regular administrative operations like like managing payments, creating allocation requests, etc.

{% hint style="info" %}
Broker API provides a more comprehensive selection of methods compared to the [trader's API](../trading-api/).
{% endhint %}

The extended API is structured by categories, each representing a different set of functionality. The first section — **Authentication** — covers the process of generating authentication tokens that must be provided in the header of all other requests. All subsequent sections cover different aspects of ETNA Trader, ranging from order placement to submitting user feedback.

Each API request is described on two pages; the first page introduces you to the API request and explains how to properly use the request parameters and the typical mistakes to avoid; the second page is strictly technical, outlining all of the header and body parameters along with their types, the range of request status codes, as well as all possible responses.

![](../../.gitbook/assets/screenshot-2019-04-29-at-15.29.22.png)

