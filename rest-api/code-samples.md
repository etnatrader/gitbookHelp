---
description: Explore examples of code that leverages ETNA API requests
---

# Code Samples

## Introduction

This following sections of ETNA Trader's REST API documentation provide an in-depth look into the structure, syntax, and the range of possible responses for each endpoint of ETNA Trader's API. But before you proceed to examine each endpoint in detail, let's first walk through a few sample scripts that demonstrate how the API works in action.

Each endpoint has its own URL and a set of parameters that must be provided in the request header, body, and query. For example, the initial authentication endpoint requires the credentials of a user in ETNA Trader as well as the application key that is retrievable from the BO Companies widget. It's critical to ensure that all required parameters are provided in the request; otherwise the request will fail.

If the request is successful, you'll receive a confirmation message as well as the 200 status code. If the request is improperly constructed or some parameters are lacking, you'll receive a status code in the range between 400 and 500.

## TRADER API

### Initial Authentication 

{% page-ref page="public-api/authentication/" %}

{% tabs %}
{% tab title="Python" %}
{% code-tabs %}
{% code-tabs-item title="Initial Authentication" %}
```python
import requests

class EtnaAPIRequest:

	baseURL = "https://pub-api-et-demo-prod.etnasoft.us/api/"
	EtAppKey = "your EtAppKey from the BO Companies widget"

	token = 'uninitialized'

	username = "your username in ETNA Trader"
	password = "your password in ETNA Trader"

	def initialAuth(self):
	    #Creating a POST request
		authenticationRequest = requests.post(self.baseURL + 'token', 
											  headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Username":self.username, "Password":self.password})

		print('Authorization status code: ' + str(authenticationRequest.status_code) + '\n')

		try:
			responseJSON = authenticationRequest.json()
			print(responseJSON)
			self.token = "Bearer " + responseJSON["Token"]
			return responseJSON
		except:
			return "No response"
			
#Performing initial Authentication
sampleRequest = EtnaAPIRequest()
sampleRequest.initialAuth()
```
{% endcode-tabs-item %}
{% endcode-tabs %}

In this example, there's a class called `EtnaAPIRequest` that has five properties:

* `baseURL` — this is the URL that hosts your API. Each solution has its own base URL for both the Trader and the Developer API.
* `EtAppKey` — this is the unique key of your solution that can be retrieved from the BO companies widget in ETNA Trader.
* `Token` — this is the authentication token that must be provided in all API requests except for the first one \(authentication\).
* `Username` and `password` — these are the credentials of a user on whose behalf all API requests will be made.

The first method — `initialAuth` — creates a POST request to the base URL appended by `token` \(each endpoint has its own unique address\). As for headers, the authentication endpoint requires you to provide the following parameters:

* `"Accept" : "application/json"`— use this parameter to accept the authorization token that will be returned in response to this request.
* `EtAppKey` — use this parameter to identify your app in all requests.
* `Username` and `password` — these are the credentials of the user on whose behalf all subsequent requests will be made.

In response to this request, you'll receive a JSON file that contains the token \(provided that all the parameters were correctly specified\):

```javascript
{'State': 'Succeeded', 'Token': 'Fake/Cl++ZKkDecvgAAAAAOgAAAAAIAACAAAAB8WguNLQWKAUhh7QbSvsHZMGhO6xlNiSFPptfJRlnD0hABAADlr/R6NVs3V+nl2HJlzM8qOLy3MvGU313ecOIsR9GBF14QsRVohtUPRyoiNpdZ9BRql9EdGstABoDNlYF4TLNJeEyF8WEaKL+gEHP4OXmbQTnpD6swG7+2Y3MWe6atpglyzFsJiDoMRuHMMOLbM3h3zy4+E3wgewghduRvBzgRa9pmp7iuCSF9RixJAO+pW+VzNXdfalulcBMdbVBaomN08TATGvrLjsDRKbzMy3j02w1qPc2dE7xo4svIxwWfMj+wpPDUDg4Low4Solyfk3qdK0W9/gYBvGGCB/Ppg6GRJYuFZf5+KHpbb43k/M8QFaXzpmlEL4HTYfC6cjDRsngmOzAwTK0WqT/7NpE+o1X610AAAAC3eKWYjv0Il+s4H0hr+Tkqc6L3+2IcT97KcTCMP7/Xrb7Pa/ybDPoZ3ZVHiU7JBUFaS4MEaZ44u7Zrsu/gbOxG'}
```

You can then extract the returned token and assign it to the `token` property.
{% endtab %}

{% tab title="JavaScript" %}

{% endtab %}

{% tab title="C\#" %}

{% endtab %}
{% endtabs %}

#### CURL

```text
curl -X POST --header 'Content-Type: application/x-www-form-urlencoded' --header 'Accept: application/json' --header 'Username: yourUsername' --header 'Password: yourPassword' --header 'Authorization: Bearer yourToken' --header 'Et-App-Key: yourEttAppKey' 'https://priv-api-et-demo-prod.etnasoft.us/api/token'
```

### Placing New Orders 

{% page-ref page="public-api/orders/place-order/" %}

{% tabs %}
{% tab title="Python" %}
{% code-tabs %}
{% code-tabs-item title="Placing New Orders" %}
```python
import requests

class EtnaAPIRequest:

	baseURL = "https://pub-api-et-demo-prod.etnasoft.us/api/"
	EtAppKey = "your EtAppKey from the BO Companies widget"
	token = 'the roken retrieved in the previous endpoint'

    def placeOrder(self, order, tradingAccount):

		orderPlacementRequest = requests.post(self.baseURL + 'v1.0/accounts/' + str(tradingAccount) + '/orders',
											  headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Authorization":self.token},
											  json = order)

		print('Authorization status code: ' + str(orderPlacementRequest.status_code) + '\n')

		try:
			responseJSON = orderPlacementRequest.json()
			return responseJSON
		except:
			return "No response"

#New trailing stop limit order JSON
   newOrder = {
     "Symbol": "AAPL",
     "ExpireDate": "2019-12-20T10:07:59.181Z",
     "Type": "TrailingStopLimit",
     "Side": "Buy",
     "ExecInst": "AllOrNone",
     "TimeInforce": "GTC",
     "Quantity": 1,
     "Exchange": "XNAS",
     "TrailingLimitAmountType" : "Absolute", 
     "TrailingLimitAmount" : 4,
     "ExtendedHours": "REGPOST",
     "TrailingStopAmountType" : "Absolute", 
     "TrailingStopAmount" : 10,
   }
   
   sampleRequest = EtnaAPIRequest()
   sampleRequest.placeOrder(newOrder, 6303) #placing a new order
```
{% endcode-tabs-item %}
{% endcode-tabs %}

This method — `placeOrder()` — is quite similar: your specify the base URL appended by its unique address \(you can look it up in the documentation for order placement\). The headers are different this time and you should also provide the new order in the JSON format as the request's body. 

In response to this API request, you'll receive a JSON dictionary with detailed information about the newly placed order.
{% endtab %}

{% tab title="JavaScript" %}

{% endtab %}

{% tab title="C\#" %}

{% endtab %}
{% endtabs %}

#### CURL

```text
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: theToken' --header 'Et-App-Key: EtAppKey' -d '{ \ 
   "Symbol": "AAPL", \ 
   "ExpireDate": "2019-12-20T10:07:59.181Z", \ 
   "Type": "TrailingStopLimit", \ 
   "Side": "Buy", \ 
   "ExecInst": "AllOrNone", \ 
   "TimeInforce": "GTC", \ 
   "Quantity": 1, \ 
   "Exchange": "XNAS", \ 
   "TrailingLimitAmountType" : "Absolute",  \ 
   "TrailingLimitAmount" : 4, \ 
   "ExtendedHours": "REGPOST", \ 
   "TrailingStopAmountType" : "Absolute",  \ 
   "TrailingStopAmount" : 10, \ 
 }' 'https://priv-api-et-demo-prod.etnasoft.us/api/v1.0/accounts/6303/orders'
```

### Get a User's Information

{% page-ref page="public-api/managing-users/get-users-info/" %}

{% tabs %}
{% tab title="Python" %}
```python
import requests

class EtnaAPIRequest:

	baseURL = "https://pub-api-et-demo-prod.etnasoft.us/api/"
	EtAppKey = "your EtAppKey from the BO Companies widget"
	token = 'the roken retrieved from the first endpoint'

	def getUsersInfo(self, userID):
	
			getUsersInfoRequest = requests.get(self.baseURL + 'v1.0/users/' + str(userID) + '/info', 
											   headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Authorization":self.token},
											   )
			print('Authorization status code: ' + str(getUsersInfoRequest.status_code) + '\n')
	
			try:
				responseJSON = getUsersInfoRequest.json()
				print (responseJSON)
				return responseJSON
			except:
				return "No response"

sampleRequest = EtnaAPIRequest()
#Retrieving information about the user 7420
sampleRequest.getUsersInfo(7420)
```

This method — `getUsersInfo()` — enables you to retrieve detailed information about a specific user in ETNA Trader. The ID of the enquired user must be specified in the base URL. In response to this request, you'll receive a JSON file with the user's information. 
{% endtab %}

{% tab title="JavaScript" %}

{% endtab %}

{% tab title="C\#" %}

{% endtab %}
{% endtabs %}

#### CURL

```text
curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer yourToken+wefx0MhIL' --header 'Et-App-Key: yourKey' 'https://priv-api-et-demo-prod.etnasoft.us/api/v1.0/users/7420/info'
```

### Getting a User's Positions

{% page-ref page="public-api/positions/get-users-positions/" %}

{% tabs %}
{% tab title="Python" %}
```python
import requests

class EtnaAPIRequest:

	baseURL = "https://pub-api-et-demo-prod.etnasoft.us/api/"
	EtAppKey = "your EtAppKey from the BO Companies widget"
	token = 'the roken retrieved from the first endpoint'

	def getUsersPositions(self, accountID):

		queryParameters = {
			"accoundId" : 6303,
			"pageNumber" : 0,
			"pageSize" : 10,
			"sortField" : "Id",
			"desc" : True
		}

		getUsersPositions = requests.get(self.baseURL + 'v1.0/accounts/' + str(accountID) + '/positions', 
										 headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Authorization":self.token},
										 params = queryParameters
										 )
		try:
			responseJSON = getUsersPositions.json()
			print (responseJSON)
			return responseJSON
		except:
			return "No response"


#Performing initial Authentication
sampleRequest = EtnaAPIRequest()
sampleRequest.initialAuth()

#retrieveing positions in account 6303
sampleRequest.getUsersPositions(6303)

```

This method — `getUsersPositions()` — enables you to retrieve the list positions opened on a specific account in ETNA Trader. The ID of the enquired account must be specified in the base URL. In response to this request, you'll receive a JSON file with the list of currently open positions. 
{% endtab %}

{% tab title="JavaScript" %}

{% endtab %}

{% tab title="C\#" %}

{% endtab %}
{% endtabs %}

```text
curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAUGqZLsz5mkidCvrdAY1TRgAAAAACAAAAAAAQZgAAAAEAACAAAAD7npupkHQns7X8egXdUEd9DN58PmhOqYh/LEz5FGZuCgAAAAAOgAAAAAIAACAAAACU/Q1qGPWZGNu/nWFJzuyltREDxZSNKw6V1fO++++/JVZxWO///yourToken' --header 'Et-App-Key: yourKey' 'https://pub-api-et-demo-prod.etnasoft.us/api/v1.0/accounts/6303/positions?pageNumber=0&pageSize=10&sortField=Id&desc=true'
```

### Get Candles and Indicators for a Security

{% page-ref page="public-api/historical-data/get-candles-and-indicators-for-charts/" %}

{% tabs %}
{% tab title="Python" %}
```python
import requests

class EtnaAPIRequest:

	baseURL = "https://pub-api-et-demo-prod.etnasoft.us/api/"
	EtAppKey = "your EtAppKey from the BO Companies widget"
	token = 'the roken retrieved from the first endpoint'
    
    def getCandlesAndIndicators(self, securityInfoBody):

		getCandlesAndIndicatorsRequest = requests.put(self.baseURL + 'v1.0/history/symbols/',
													  headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Authorization":self.token},
													  json = securityInfoBody
													  )

		try:
			responseJSON = getCandlesAndIndicatorsRequest.json()
			print (responseJSON)
			return responseJSON
		except:
			return "No response"
			
#Performing initial Authentication
sampleRequest = EtnaAPIRequest()
sampleRequest.initialAuth()

#declaring chart model
chartDataModel = {
"Security":
	{"Symbol":"AAPL",
	"Exchange":"XNAS",
	"Currency":"USD"},	
"SecurityHistorySettings":
	{"StartDate":1542776400,
	"EndDate":1550764844,
	"CandlesCount":-1,
	"Period":"4h",
	"Interval":-7,
	"IncludeNonMarketData":False},
"IndicatorsHistorySettings":[
	{"Signature":"MACD|4h|false|12|26|9",
	"Interval":-7,
	"StartDate":1542776400,
	"EndDate":1550764844,
	"CandlesCount":-1,
	"Offset":0,
	"Indicator":{
		"id":4,
		"indicatorId":1,
		"type":"movingAverageConvergenceDivergenceIndicator",
		"position":"lower",
		"external":True,
		"settings":{
			"id":4,
			"type":"movingAverageConvergenceDivergenceIndicator",
			"shortThickness":2,
			"longThickness":2,
			"shortBrush":"32c814",
			"longBrush":"dc1414",
			"signalBrush":"ff9900",
			"shortPeriod":12,
			"longPeriod":26,
			"signalPeriod":9,
			"showLastValue":True,
			"showCurrentPoint":True,
			"showLevelBands":False}}}]
}

#retrieving candles and indicators for the Apple stock
sampleRequest.getCandlesAndIndicators(chartDataModel)
```

This method — `getCandlesAndIndicators()` — enables you to retrieve chart data \(candles and indicators\) for a specific security. In response to this request, you'll receive a JSON file with the pricing data that can be used to draw charts. 
{% endtab %}

{% tab title="JavaScript" %}

{% endtab %}

{% tab title="C\#" %}

{% endtab %}
{% endtabs %}

#### CURL

```text
curl -X PUT --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer yourToken' --header 'Et-App-Key: yourKey' -d '{"Security": \ 
 	{"Symbol":"AAPL", \ 
 	"Exchange":"XNAS", \ 
 	"Currency":"USD"}, \ 
 	 \ 
 "SecurityHistorySettings": \ 
 	{"StartDate":1542776400, \ 
 	"EndDate":1550764844, \ 
 	"CandlesCount":-1, \ 
 	"Period":"4h", \ 
 	"Interval":-7, \ 
 	"IncludeNonMarketData":false}, \ 
  \ 
 "IndicatorsHistorySettings":[ \ 
 	{"Signature":"MACD|4h|false|12|26|9", \ 
 	"Interval":-7, \ 
 	"StartDate":1542776400, \ 
 	"EndDate":1550764844, \ 
 	"CandlesCount":-1, \ 
 	"Offset":0, \ 
 	"Indicator":{ \ 
 		"id":4, \ 
 		"indicatorId":1, \ 
 		"type":"movingAverageConvergenceDivergenceIndicator", \ 
 		"position":"lower", \ 
 		"external":true, \ 
 		"settings":{ \ 
 			"id":4, \ 
 			"type":"movingAverageConvergenceDivergenceIndicator", \ 
 			"shortThickness":2, \ 
 			"longThickness":2, \ 
 			"shortBrush":"32c814", \ 
 			"longBrush":"dc1414", \ 
 			"signalBrush":"ff9900", \ 
 			"shortPeriod":12, \ 
 			"longPeriod":26, \ 
 			"signalPeriod":9, \ 
 			"showLastValue":true, \ 
 			"showCurrentPoint":true, \ 
 			"showLevelBands":false}}}] \ 
 }' 'https://pub-api-et-demo-prod.etnasoft.us/api/v1.0/history/symbols'
```

## EXTENDED API

### Create a New Trading Account

{% hint style="warning" %}
Creating new trading accounts is permitted only through the [extended API.](private-api/)
{% endhint %}

{% page-ref page="private-api/internal-accounts/create-a-new-trading-account/" %}

{% tabs %}
{% tab title="Python" %}
{% code-tabs %}
{% code-tabs-item title="Creating a new trading account in ETNA Trader" %}
```python
import requests

class EtnaAPIRequest:

	baseURL = "https://priv-api-et-demo-prod.etnasoft.us/api/"
	EtAppKey = "your EtAppKey from the BO Companies widget"
	token = 'the roken retrieved from the first endpoint'
	
	def createNewTradingAccount(self, account):

		createNewTradingAccountRequest = requests.post(self.baseURL + 'v1.0/accounts', 
										   			   headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Authorization":self.token},
										   			   json = account
										               )
		try:
			responseJSON = createNewTradingAccountRequest.json()
			print (responseJSON)
			return responseJSON
		except:
			return "No response"

sampleRequest = EtnaAPIRequest()

#Creating a new trading account
newTradingAccount = {
  "SubscriptionPlanId": 0,
  "ClearingAccount": "string",
  "CreatedDate": "2019-03-11T10:37:02.671Z",
  "ModifiedDate": "2019-03-11T10:37:02.671Z",
  "Enabled": True,
  "IsChanged": True,
  "Cash": 0,
  "Currency": "string",
  "Status": "UnSpecified",
  "CommissionPlan": "string",
  "RepCode": "string",
  "MarginInterestRate": 0,
  "CashInterestRate": 0,
  "CloseEquity": 0,
  "OpenExcess": 0,
  "OptionLevel": 0,
  "MarginType": "Empty",
  "Permissions": "Empty",
  "BaseCash": 0,
  "Sweep": 0,
  "OwnerType": "IndividualCustomer",
  "DayTradingBuyingPower": 0,
  "DayTrades": 0,
  "SmaBalance": 0,
  "HouseCall": 0,
  "MaintenanceCall": 0,
  "EquityCall": 0,
  "InitialCall": 0,
  "DayTradeCall": 0,
  "TradeDayBalance": 0,
  "MoneyMarket": 0,
  "Cip": 0,
  "IsAverageAccount": True,
  "MarginEquity": 0,
  "ClearingFirm": "string",
  "ExcessEquity": 0
}
sampleRequest.createNewTradingAccount(newTradingAccount)
```
{% endcode-tabs-item %}
{% endcode-tabs %}

This method — `createNewTradingAccount()` — enables you to create a new trading account in ETNA Trader. Information about the new trading account must be provided in the JSON format as the request's body. In response to this request, you'll receive a JSON file with the newly created account's information \(including its ID\). 
{% endtab %}

{% tab title="JavaScript" %}

{% endtab %}

{% tab title="C\#" %}

{% endtab %}
{% endtabs %}

#### CURL

```text
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer yourToken' --header 'Et-App-Key: yourEtAppKey' -d 'newTradingAccount = { \ 
   "SubscriptionPlanId": 0, \ 
   "ClearingAccount": "string", \ 
   "CreatedDate": "2019-03-11T10:37:02.671Z", \ 
   "ModifiedDate": "2019-03-11T10:37:02.671Z", \ 
   "Enabled": True, \ 
   "IsChanged": True, \ 
   "Cash": 0, \ 
   "Currency": "string", \ 
   "Status": "UnSpecified", \ 
   "CommissionPlan": "string", \ 
   "RepCode": "string", \ 
   "MarginInterestRate": 0, \ 
   "CashInterestRate": 0, \ 
   "CloseEquity": 0, \ 
   "OpenExcess": 0, \ 
   "OptionLevel": 0, \ 
   "MarginType": "Empty", \ 
   "Permissions": "Empty", \ 
   "BaseCash": 0, \ 
   "Sweep": 0, \ 
   "OwnerType": "IndividualCustomer", \ 
   "DayTradingBuyingPower": 0, \ 
   "DayTrades": 0, \ 
   "SmaBalance": 0, \ 
   "HouseCall": 0, \ 
   "MaintenanceCall": 0, \ 
   "EquityCall": 0, \ 
   "InitialCall": 0, \ 
   "DayTradeCall": 0, \ 
   "TradeDayBalance": 0, \ 
   "MoneyMarket": 0, \ 
   "Cip": 0, \ 
   "IsAverageAccount": True, \ 
   "MarginEquity": 0, \ 
   "ClearingFirm": "string", \ 
   "ExcessEquity": 0 \ 
 }' 'https://priv-api-et-demo-prod.etnasoft.us/api/v1.0/accounts'
```

### Creating a New User

{% hint style="warning" %}
Creating new users is permitted only through the [extended API.](private-api/)
{% endhint %}

{% page-ref page="private-api/internal-users/create-a-new-user/" %}

{% tabs %}
{% tab title="Python" %}
{% code-tabs %}
{% code-tabs-item title="Creating a new user in ETNA Trader" %}
```python
import requests

class EtnaAPIRequest:

	baseURL = "https://priv-api-et-demo-prod.etnasoft.us/api/"
	EtAppKey = "your EtAppKey from the BO Companies widget"
	token = 'the roken retrieved from the first endpoint'

	def createNewUser(self, user):

		createNewUserRequest = requests.post(self.baseURL + 'v1.0/users', 
										   	 headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Authorization":self.token},
										   	 json = user,
										   	 params = {"sendInvitationEmail":False} #query
										     )
		try:
			responseJSON = createNewUserRequest.json()
			print (responseJSON)
			return responseJSON
		except:
			return "No response"

sampleRequest = EtnaAPIRequest()

newUser = {
  "FirstName": "string",
  "Middle": "string", 
  "LastName": "string",
  "EmailAddress": "test@domain.com", 
  "Login": "string", 
  "Salutation": "NoSalutation", 
  "Suffix": "NoSuffix", 
  "Enabled": True, 
  "TimeZoneInfoId": "string", 
  "ExpirationDate": "2019-03-10T14:11:54.494Z",
  "PhoneNumber": "string",
  "EntitlementsPhoneNumber": "string"
}
#Creating a new user
sampleRequest.createNewUser(newUser)
```
{% endcode-tabs-item %}
{% endcode-tabs %}

This method — `createNewUser()` — enables you to create a new user in ETNA Trader. Information about the new user must be provided in the JSON format as the request's body. In response to this request, you'll receive a JSON file with the newly created user's information \(including its ID\). 
{% endtab %}

{% tab title="JavaScript" %}

{% endtab %}

{% tab title="C\#" %}

{% endtab %}
{% endtabs %}

#### CURL

```text
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' --header 'Authorization: Bearer token/Cl+sBAAAAUGqZLsz5mkidCvrdAY1TRgAAAAACAAAAAAAQZgAAAAEAACAAAACayaU6KE1fF4D6MmFqe2n8XKelFGHhaau7ysPRew4/+wAAAAAOgAAAAAIAACAAAAC2g20aiTv3Vwmn5AlsMvoIQNVqvEOKgDbPwp3cwH4nZBABAAC8xIylg7shBUaQfJR7RmhV0n21swY30s4v0VQFEru4BKs4+9dwmW1Sstz5qCk5CB4nPukGrTG3V7R3/KKQgHcOGLjQyES84XhWHdn1oXY0qgvCVJZHmb+SnIJJGP9NuMdU3mzG8+ZV4GcWZFgLP596xZKWN7uxanou8Sw2QxzSiy5Wnva/jrqQsYfL6TskU9lGTFz5ph2UQwjp7g96HTjLkVR7+DmCMFLgq0AjcEujcrp4maBqXzXGRHgREZCkZq9EaVNoKIfF+K+EYOu4pOaVxEI3yBmIrkMxUJT6JjH+DygVHHYX/4N3yd6nogqDz4NOCMwb8sHg7NU3GDdpC3wmDq+fDlvIBIGeTi8Yi7k/UEAAAACAR3PN/9rQzbxcWAsgYtLIbJvu8seDekmis0TGf3cbkPo+the+0MhIL' --header 'Et-App-Key: theKey' -d '{ \ 
   "FirstName": "string", \ 
   "Middle": "string",  \ 
   "LastName": "string", \ 
   "EmailAddress": "test%40domain.com",  \ 
   "Login": "string",  \ 
   "Salutation": "NoSalutation",  \ 
   "Suffix": "NoSuffix",  \ 
   "Enabled": true,  \ 
   "TimeZoneInfoId": "string",  \ 
   "ExpirationDate": "2019-03-10T14:11:54.494Z", \ 
   "PhoneNumber": "string", \ 
   "EntitlementsPhoneNumber": "string" \ 
 }' 'https://priv-api-et-demo-prod.etnasoft.us/api/v1.0/users?sendInvitationEmail=false'
```

