# Get User Information

## Get a User's Information

{% page-ref page="../managing-users/get-users-info/" %}

{% tabs %}
{% tab title="Python" %}
```python
import requests

class EtnaAPIRequest:

    baseURL = "https://pub-api-et-demo-prod.etnasoft.us/api/"
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

#Performing initial authentication
sampleRequest = EtnaAPIRequest()
sampleRequest.simpleAuth()

#Retrieving information about the user 7420
sampleRequest.getUsersInfo(7420)
```

This method — `getUsersInfo()` — enables you to retrieve detailed information about a specific user in ETNA Trader. The ID of the enquired user must be specified in the base URL. In response to this request, you'll receive a JSON file with the user's information.
{% endtab %}
{% endtabs %}

### CURL

```text
curl -X GET --header 'Accept: application/json' --header 'Authorization: Bearer yourToken+wefx0MhIL' --header 'Et-App-Key: yourKey' --header 'Content-Length: 0' 'https://pub-api-et-demo-prod.etnasoft.us/api/v1.0/users/7420/info'
```

