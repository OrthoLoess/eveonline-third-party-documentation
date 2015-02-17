# Implementing the SSO
The recommended flow for web applications where the client secret can be stored on a server is the Authorization Code Grant documented [here](http://tools.ietf.org/html/rfc6749#section-4.1).

For those users that don't feel like reading the standard the authentication is really just a series of HTTPS requests and redirects described in this document.

## Redirect to the SSO
When a user clicks the "login" button on a your website you need to redirect the user with HTTP 302 redirect to `https://login.eveonline.com/oauth/authorize` with the following query string parameters:

- response_type - Must be set to "code".
- redirect_uri - After authentication the user will be redirected to this URL on your website, it must match the definition on file in the SSO.P
- client_id - A string identifier for the client, provided by CCP.
- scope - The requested scopes as a space delimited string.
- state (OPTIONAL but recommended) - An opaque value used by the client to maintain state between the request and callback. The SSO includes this value when redirecting back to the 3rd party website. While not required, it is important to use this for security reasons. [http://www.thread-safe.com/2014/05/the-correct-use-of-state-parameter-in.html](http://www.thread-safe.com/2014/05/the-correct-use-of-state-parameter-in.html) explains why the state parameter is needed.

**Example URL:** [https://login.eveonline.com/oauth/authorize/?response_type=code&redirect_uri=https://3rdpartysite.com/callback&client_id=3rdpartyClientId&scope=&state=uniquestate123](https://login.eveonline.com/oauth/authorize/?response_type=code&redirect_uri=https://3rdpartysite.com/callback&client_id=3rdpartyClientId&scope=&state=uniquestate123)

The user will need to authenticate with a username/password on the SSO and select the character that your web site will be given access to. If the user has previously logged in to some other website the authentication has already been done, this is single sign-on after all, and they will just need to select a character and approve the required scopes.

The SSO will redirect the user back to the provided `callback_uri` with an authorization code and the state as query string parameters.

That will look something like this: [https://3rdpartysite.com/callback?code=gEyuYF_rf...ofM0&state=uniquestate123](https://3rdpartysite.com/callback?code=gEyuYF_rf...ofM0&state=uniquestate123)

- code - The Authorization code.
- state - The state parameter that was sent in the original request to the SSO.

## Verify the authorization code
At this point in time your website has the authorization code. The only thing the authorization code is good for is to obtain an access token.

It is also important to note that the authorization code is single use only.

The you need to make an HTTP POST to `https://login.eveonline.com/oauth/token` to exchange the authorization code with an access token, and it looks like this:

    POST https://login.eveonline.com/oauth/token HTTP/1.1
    
    Authorization: Basic bG9...ZXQ=
    Content-Type: application/x-www-form-urlencoded
    Host: login.eveonline.com
    
    grant_type=authorization_code&code=gEyuYF_rf...ofM0

- Authorization HTTP header: This is the string "Basic" plus the string {client_id}:{client_secret} Base64 encoded
    - NOTE: It is very important to make sure there are no spaces or newline characters in the string that is being Base64 encoded. If in doubt, try to Base64 encode these sample values and compare to the one below.
    - Example values:
        - client_id = 3rdparty_clientid
        - client_secret=jkfopwkmif90e0womkepowe9irkjo3p9mkfwe
        - Concatenated to become: 3rdparty_clientid:jkfopwkmif90e0womkepowe9irkjo3p9mkfwe
    - Resulting in Base64-encoded Authorization header
        - Authorization: Basic M3JkcGFydHlfY2xpZW50aWQ6amtmb3B3a21pZjkwZTB3b21rZXBvd2U5aXJram8zcDlta2Z3ZQ==
- grant_type=authorization_code: This is fixed and doesn't change
- code: The authorization code obtained in Step 1. Make sure there are no extra spaces or newline characters at the end of the HTTP body.

A successful verification request will yield a response in [JSON](http://www.json.org/) format similar to the following:

    {
        access_token: "uNEEh...a\_WpiaA2"
        token_type: "Bearer"
        expires_in: 300
        refresh_token: null
    }

The access token returned is valid for 300 seconds, or 5 minutes.