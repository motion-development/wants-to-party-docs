# Wants to Party Oauth2
Wants to party provides a aouth system for all user to login with wants to party on any site and give them permission to do things. 

## Getting Started
First you need to make a new application at the [developer portal](/developers). After you have done that save the client ID and secret in a secure place.

## Making a ouath link
All application need to use the same link and change the url arguments to fit with the application. Here is a list of all the required arguments:

- `client_id` (required) - The ID of the application you just made.
- `scopes` (required) - A list of [scopes](/developers/docs/oauth/scopes)
- `redirect_uri` (reqiured) - A redirect uri where the user goes to after authorizing (Must be set in developer portal)
- `response_type` (required) - Must be set to `code`
- `state` (Optional) - A argument that gets returned after the user authorized. Used for sessions

Example link:
```
https://wants-to.party/oauth/authorize?client_id=n3gwnb-ur8bki-uhf5l-1sjxo8&scopes=user.read&redirect_uri=https://mysite.com/callback&response_type=code&state=1234567890
```



