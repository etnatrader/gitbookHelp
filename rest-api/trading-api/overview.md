---
description: Get started with ETNA Trader's REST API
---

# Overview

### Introduction

Trader API mimics the functionality of user widgets. Namely, you can invoke the API to perform regular trading operations like placing orders, getting quotes, configuring price alerts, and so forth. You can use this API to create custom JavaScript-based widgets or develop your own UI that invokes our API to settle transactions. Note that the trader API provides a limited number of methods compared to the private API that offers far more functionality.

The trader API is structured by categories, each representing a different set of functionality. The first section — Authentication — covers the process of generating authentication tokens that must be provided in the header of all other requests. All subsequent sections cover different aspects of ETNA Trader, ranging from order placement to submitting user feedback.

Each API request is described on two pages; the first page introduces you to the API request and explains how to properly use the request parameters and the typical mistakes to avoid; the second page is strictly technical, outlining all of the header and body parameters along with their types, the range of request status codes, as well as all possible responses.

