# Wants to Party Oauth2
Wants to party provides a aouth system for all user to login with wants to party on any site and give them permission to do things. 

<br>


## Getting Started
First you need to make a new application at the [developer portal](/developers). After you have done that save the client ID and secret in a secure place.

<br>

## Making a Oauth link
All application need to use the same link and change the url arguments to fit with the application. Here is a list of all the required arguments:

- `client_id` (required) - The ID of the application you just made.
- `scopes` (required) - A list of [scopes](/developers/docs/oauth/scopes)
- `redirect_uri` (reqiured) - A redirect uri where the user goes to after authorizing (Must be set in developer portal)
- `response_type` (required) - Must be set to `code`
- `state` (Optional) - A argument that gets returned after the user authorized. Used for sessions 

<Br>
  
  
#### Example link:
```
https://wants-to.party/oauth/authorize?client_id=n3gwnb-ur8bki-uhf5l-1sjxo8&scopes=user.read&redirect_uri=https://mysite.com/callback&response_type=code&state=1234567890
```
#### Example response:
```
https://mysite.com/callback?code=ns60PYmuV6T4sSykpTsRdR1X8&state=1234567890
```

  <br>
  
  ## Get Access token
  To get an access token you will need to redeem the code for it under the `/api/token` endpoint. You will need to authorize yourself with the application secret as a `Bearer` token.
  
  #### Required json data:
  - `code` - The code you recieved in the url, or a refresh token
  - `grand_type` - Must be `authorization_code` if redeeming code or `refresh_token` if redeeming for a refresh token
  - `client_id` - The client ID for the application making the request
  
#### Example request in python
  ```py
import requests
  
headers={"Authorization": "Bearer CLIENT_SECRET"}
response=requests.post("https://wants-to.party/api/oauth/token", json={
    "code": "CODE_FROM_URL", 
    "grand_type": "authorization_code",
    "client_id": "CLIENT_ID"
}, headers=headers)
access_token=response.json().get("access_token")
  ```
  
  ### Refresh token
  If you need to refresh your access token you can use the above endpoint but with an access token instead of a code. Change the grand type and your are good.
  
  
  <br>
  
  ## What is next?
  Depending on the scopes you picked you may do different things. Get started by taking a look at the [user](/developers/docs/user) endpoints.
  


