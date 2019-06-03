# Introduction

### Overview

ETNA Trader is a cross-platform trading suite that enables brokers to provide all-encompassing trading functionality to their customers. Even though ETNA Trader provides both the web and the mobile interfaces for executing trades and analyzing markets, some brokers opt to implement their own custom interfaces that suit their requirements. For this purpose, ETNA Trader offers a trader as well as extedned REST API that can be invoked to perform various trading operations like creating users, getting quotes, and placing orders. 

In this scenario ETNA Trader serves as the backend platform for your own custom-made web terminal or mobile app. Your task is to develop the mobile and web UI that invoke our API to perform all of the trading operations. On our side, we will execute your customers' orders on the required exchange, settle all transactions with the clearing firm, and take care of all of behind-the-scenes technicalities.

Another frequent use-case of our API is to augment the existing functionality of ETNA Trader by designing custom widgets. In this scenario you create your own custom JavaScript-based widgets that can load various information about the user's positions, place new orders, and perform just about any other action. For example, you can create a widget that displays the user's most frequently traded securities; or a widget that displays the list of users' positions with the highest profit or highest loss.

### Trading API

This is the trader's API that invokes actions typically performed by trader's widgets: placing orders, getting quotes, configuring price alerts, and so forth. This API can be called from anywhere simply using your app's API key and a user's credentials. 

{% page-ref page="trading-api/" %}

