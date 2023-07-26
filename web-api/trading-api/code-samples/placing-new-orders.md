# Placing New Orders

### Placing New Orders  & Checking Their Status

{% content-ref url="../orders/place-order/" %}
[place-order](../orders/place-order/)
{% endcontent-ref %}

{% tabs %}
{% tab title="Python" %}
{% code title="Placing New Orders" %}
```python
import requests

class EtnaAPIRequest:

	baseURL = "https://pub-api-trader-demo-prod.etnasoft.us/api/"
	EtAppKey = "Et App Key from the BO Companies widget"

	token = 'uninitialized'

	username = "Your username"
	password = "Your password"

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
		
	def placeOrder(self, order, tradingAccount):

		orderPlacementRequest = requests.post(self.baseURL + 'v1.0/accounts/' + str(tradingAccount) + '/orders',
											  headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Authorization":self.token},
											  json = order)

		print('Authorization status code: ' + str(orderPlacementRequest.status_code) + '\n')

		try:
			responseJSON = orderPlacementRequest.json()
			# print (responseJSON)
			return responseJSON['Id']
		except:
			return "No response"

	def getOrderStatus(self, accountID, orderID):
		getOrderStatusRequest = requests.get(self.baseURL + 'v1.0/accounts/' + str(accountID) + '/orders/' + str(orderID),
											 headers = {"Accept" : "application/json", 
									  			 		"Et-App-Key" : self.EtAppKey, 
									  			 		"Authorization":self.token})
		try:
			responseJSON = getOrderStatusRequest.json()
			print(responseJSON)
			return responseJSON['Status']
		except:
			return "No response"
			
#Performing initial Authentication
sampleRequest = EtnaAPIRequest()
sampleRequest.simpleAuth()


order = {
  "Symbol": "AAPL",
  "Type": "Market",
  "Side": "Buy",
  "Quantity": 100
}

#placing a new order; the trading account mi
orderID = sampleRequest.placeOrder(order, 6303) 

#Retrieving the status of the new order
responseMessage = sampleRequest.getOrderStatus(6303, orderID)
print(responseMessage)
```
{% endcode %}

In this example we perform authentication, place a new order, and then check the new order's status to see if it's active, under review, rejected, etc.

{% hint style="info" %}
If the authorization token provided in the request header was generated using an administrator's credentials, the order can be placed on behalf of any user in the company.
{% endhint %}
{% endtab %}
{% endtabs %}

#### Sample CURL for Order Placement

```
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
 }' 'https://pub-api-trader-demo-prod.etnasoft.us/api/v1.0/accounts/6303/orders'
```
