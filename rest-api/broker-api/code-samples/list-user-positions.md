# List User Positions

### Getting a User's Positions in Each Trading Account

{% page-ref page="../positions/get-users-positions/" %}

{% tabs %}
{% tab title="Python" %}
```python
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

	def getUsersAccounts(self, userID):
		getUsersAccountsRequest = requests.get(self.baseURL + 'v1.0/users/' + str(userID) + '/accounts', 
										 	   headers = {"Accept" : "application/json", "Et-App-Key" : self.EtAppKey, "Authorization":self.token})
		try:
			responseJSON = getUsersAccountsRequest.json()
			# print (responseJSON)
			return responseJSON
		except:
			return "No response"
		

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
			# print (responseJSON)
			return responseJSON
		except:
			return "No response"
			
#Performing initial Authentication
sampleRequest = EtnaAPIRequest()
sampleRequest.simpleAuth()

#retrieving the user's trading accounts
accounts = sampleRequest.getUsersAccounts(7125)

#looping through each trading account and retrieving its positions
for accountJson in accounts:
	accountID = accountJson['Id']
	positions = sampleRequest.getUsersPositions(accountID)
	print('Account: ' + str(accountID))
	print('Positions: ')
	print(positions)

```

This method — `getUsersPositions()` — enables you to retrieve the list positions opened on a specific account in ETNA Trader. The ID of the enquired account must be specified in the base URL. In response to this request, you'll receive a JSON file with the list of currently open positions. 
{% endtab %}
{% endtabs %}

```text
curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAUGqZLsz5mkidCvrdAY1TRgAAAAACAAAAAAAQZgAAAAEAACAAAAD7npupkHQns7X8egXdUEd9DN58PmhOqYh/LEz5FGZuCgAAAAAOgAAAAAIAACAAAACU/Q1qGPWZGNu/nWFJzuyltREDxZSNKw6V1fO++++/JVZxWO///yourToken' --header 'Et-App-Key: yourKey' --header 'Content-Length: 0' 'https://priv-api-et-demo-prod.etnasoft.us/api/v1.0/accounts/6303/positions?pageNumber=0&pageSize=10&sortField=Id&desc=true'
```

