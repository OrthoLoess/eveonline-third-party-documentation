The flow available to third-party developers is the Authorization Code Grant documented [here](http://tools.ietf.org/html/rfc6749#section-4.1).

For those users that don't feel like reading the standard the authentication is really just a series of HTTPS requests and redirects described in this document.

## Registering for the SSO
Registering for the SSO is as simple as creating a new application on the Developers web site and selecting the Authentication Only option under connection type.

## Implementing the SSO
### Redirect to the SSO
When a user clicks the "login" button on a your website you need to redirect the user with HTTP 302 redirect to https://login.eveonline.com/oauth/authorize with the following query string parameters: