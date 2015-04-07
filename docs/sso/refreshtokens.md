If any valid scope was requested in the initial redirect to the SSO, a refresh token will be returned by the token endpoint, along with the access token. While the access token will expire after a set interval - currently 20 minutes, the refresh token can be stored and used indefinitely. (Users can revoke access for individual apps on the support site)

To get a new access token you make a POST request to "https://login.eveonline.com/oauth/token" with the following params:

    grant_type='refresh_token'&refresh_token=USERS_REFRESH_TOKEN
    
You also need to include the same Authentication header (base64 encoded) as you used for the first call to the token endpoint. Example:

    Authorization: Basic [Base64 encoded client_id:client_secret]

The json response should contain a new access token for that user, along with the time until it expires.