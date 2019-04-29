# Creating New Users

### Creating a New User

{% page-ref page="../internal-users/create-a-new-user/" %}

{% tabs %}
{% tab title="Python" %}
{% code-tabs %}
{% code-tabs-item title="Creating a new user in ETNA Trader" %}
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
sampleRequet.simpleAuth()

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

