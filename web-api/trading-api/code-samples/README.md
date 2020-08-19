---
description: Explore examples of code that leverages ETNA API requests
---

# Code Samples

## Introduction

The previous articles of ETNA Trader's REST API documentation provide an in-depth look into the structure, syntax, and the range of possible responses for each endpoint of the trader's API. But before you proceed to examine each endpoint in detail, let's first walk through a few sample scripts that demonstrate how the API works in action.

Each endpoint has its own URL and a set of parameters that must be provided in the request header, body, and query. For example, the initial authentication endpoint requires the credentials of a user in ETNA Trader as well as the application key that is retrievable from the BO Companies widget. It's critical to ensure that all required parameters are provided in the request; otherwise the request will fail.

If the request is successful, you'll receive a confirmation message as well as the 200 status code. If the request is improperly constructed or some parameters are lacking, you'll receive a status code in the range between 400 and 500.

