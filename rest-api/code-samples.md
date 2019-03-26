---
description: Explore examples of code that leverages ETNA API requests
---

# Code Samples

### Introduction

This following sections of ETNA Trader's REST API documentation provide an in-depth look into the structure, syntax, and the range of possible responses for each endpoint of ETNA Trader's API. But before you proceed to examine each endpoint in detail, let's first walk through a few sample Python methods that demonstrate how the API works in action.

Each endpoint has its own URL and a set of parameters that must be provided in the request header, body, and query. For example, the initial authentication endpoint requires the credentials of a user in ETNA Trader as well as the application key that is retrievable from the BO Companies widget. It's critical to ensure that all required parameters are provided in the request; otherwise the request will fail.

If the request is successful, you'll receive a confirmation message as well as the 200 status code. If the request is improperly constructed or some parameters are lacking, you'll receive a status code in the range between 400 and 500.

### Initial Authentication & Order Placement

Let's explore how initial authentication and order placement might be implemented in a solution. In this example, there's a class called `EtnaAPIRequest` that has five properties:

* `baseURL` — this is the URL that hosts your API. Each solution has its own base URL for both the Trader and the Developer API.
* `EtAppKey` — this is the unique key of your solution that can be retrieved from the BO companies widget in ETNA Trader.
* `Token` — this is the authentication token that must be provided in all API requests except for the first one \(authentication\).
* `Username` and `password` — these are the credentials of a user on whose behalf all API requests will be made.

{% hint style="info" %}
The provided examples leverage the [Requests library](http://docs.python-requests.org/en/master/) to keep the code concise.
{% endhint %}

The first method — `initialAuth` — creates a POST request to the base URL appended by `token` \(each endpoint has its own unique address\). As for headers, the authentication endpoint requires you to provide the following parameters:

* `"Accept" : "application/json"`— use this parameter to accept the authorization token that will be returned in response to this request.
* `EtAppKey` — use this parameter to identify your app in all requests.
* `Username` and `password` — these are the credentials of the user on whose behalf all subsequent requests will be made.

In response to this request, you'll receive a JSON file that contains the token \(provided that all the parameters were correctly specified\):

```javascript
{'State': 'Succeeded', 'Token': 'Fake/Cl++ZKkDecvgAAAAAOgAAAAAIAACAAAAB8WguNLQWKAUhh7QbSvsHZMGhO6xlNiSFPptfJRlnD0hABAADlr/R6NVs3V+nl2HJlzM8qOLy3MvGU313ecOIsR9GBF14QsRVohtUPRyoiNpdZ9BRql9EdGstABoDNlYF4TLNJeEyF8WEaKL+gEHP4OXmbQTnpD6swG7+2Y3MWe6atpglyzFsJiDoMRuHMMOLbM3h3zy4+E3wgewghduRvBzgRa9pmp7iuCSF9RixJAO+pW+VzNXdfalulcBMdbVBaomN08TATGvrLjsDRKbzMy3j02w1qPc2dE7xo4svIxwWfMj+wpPDUDg4Low4Solyfk3qdK0W9/gYBvGGCB/Ppg6GRJYuFZf5+KHpbb43k/M8QFaXzpmlEL4HTYfC6cjDRsngmOzAwTK0WqT/7NpE+o1X610AAAAC3eKWYjv0Il+s4H0hr+Tkqc6L3+2IcT97KcTCMP7/Xrb7Pa/ybDPoZ3ZVHiU7JBUFaS4MEaZ44u7Zrsu/gbOxG'}
```

You can then extract the returned token and assign it to the `token` property.

The second method — `placeOrder()` — is quite similar: your specify the base URL appended by its unique address \(you can look it up in the documentation for order placement\). The headers are different this time and you should also provide the new order in the JSON format as the request's body. 

In response to this API request, you'll receive a JSON dictionary with detailed information about the newly placed order.

{% code-tabs %}
{% code-tabs-item title="ETNA API Requests sample" %}
```python
import requests

class EtnaAPIRequest:

	baseURL = "https://pub-api-et-demo-prod.etnasoft.us/api/"
	EtAppKey = "yourEtAppKey"

	token = 'uninitialized'

	username = "your username"
	password = "your password"
	
	def initialAuth(self):
		authenticationRequest = requests.post(self.baseURL + 'token', headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Username":self.username, "Password":self.password})
		print('Authorization status code: ' + str(authenticationRequest.status_code) + '\n')

		try:
			responseJSON = authenticationRequest.json()
			self.token = "Bearer " + responseJSON["Token"]
			return responseJSON
		except:
			return "No response"

	def placeOrder(self, order, tradingAccount):

		orderPlacementRequest = requests.post(self.baseURL + 'v1.0/accounts/' + str(tradingAccount) + '/orders',
											  headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Authorization":self.token},
											  json = order)

		print('Authorization status code: ' + str(orderPlacementRequest.status_code) + '\n')
		try:
			responseJSON = orderPlacementRequest.json()
			print (responseJSON)
			return responseJSON
		except:
			return "No response"


#Performing initial Authentication
sampleRequest = EtnaAPIRequest()
sampleRequest.initialAuth()

stopLimirOrder = {
  "Symbol": "AAPL",
  "ExpireDate": "2019-12-20T10:07:59.181Z",
  "Type": "StopLimit",
  "Side": "Buy",
  "ExecInst": "DoNotIncrease",
  "TimeInforce": "GTC",
  "Quantity": 100,
  "Price": 201,
  "StopPrice" : 200,
  "Exchange": "XNAS",
  "ExtendedHours": "REGPOST",
}

sampleRequest.placeOrder(stopLimirOrder, 6303)
```
{% endcode-tabs-item %}
{% endcode-tabs %}

