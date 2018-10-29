# OauthRefresher
This Burp extension is used to updated bearer tokens, similar to how Burp's cooke jar works. Specifically, it pulls a authorization token out of a JSON response and includes it in future request headers.

## Example
It will extract the following token from a HTTP response (field values shown below are default values, are customisable and the expiry value can be in seconds/epoch or an arbitrary value specified in the second tab):
```
"access_token":"5dbf5b54-4644-4015-a08e-333deea4c78c",
"expires_in":"600",
```

And then include it in future request headers in the following format if an Authorization header is found:
```
Authorization: Bearer 5dbf5b54-4644-4015-a08e-333deea4c78c
```

It will then check if the token has expired if an "expires_in" field is given in the response and send an oauth token request to grab a fresh token and update your request seemlessly. If there isn't, you can select the "Expire in Arbitrary time" checkbox and you can manually set a timeout duration in seconds.

If you are signing into multiple sessions at the same time, I would disable this extension, as it wil likely cause issues for you. At the moment, it will not allow you to choose which Oauth request to use to refresh the token. That is something I will be working towards, being able to select Oauth requests from your saved list. Even better would be to save API calls and have them tagged for scopes via the Oauth requests (if it exists) and use those (soon™).

## Releases
See the [Releases](https://github.com/teekay30/UpdateToken/releases) tab for a pre-built jar.

This is based on the Extension available in the BApp store called "Token Incrementor" created by [alexlauerman](https://github.com/alexlauerman/UpdateToken)

