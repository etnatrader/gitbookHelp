# Creating New Trading Accounts

### Create a New Trading Account

{% hint style="warning" %}
Creating new trading accounts is permitted only through the [extended API.](../)
{% endhint %}

{% page-ref page="../internal-accounts/create-a-new-trading-account/" %}

{% tabs %}
{% tab title="Python" %}
{% code-tabs %}
{% code-tabs-item title="Creating a new trading account in ETNA Trader" %}
```python
import requests

class EtnaAPIRequest:

	baseURL = "https://priv-api-et-demo-prod.etnasoft.us/api/"
	EtAppKey = "Et App Key from the BO Companies widget"

	token = 'uninitialized'

	username = "your username"
	password = "your password"

	def simpleAuth(self):
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
sampleRequest.simpleAuth()

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

