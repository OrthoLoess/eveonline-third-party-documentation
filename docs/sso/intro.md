# What is the SSO
Simply put, SSOs are a way for users to log into one web site using their username and password from another web site. For example, if go to [https://www.goodreads.com/](https://www.goodreads.com/) and try to sign in they will ask you if you want to sign in with Facebook, Twitter, Google, or even Amazon. For Goodreads this is great because it means they don't have to worry about trying to manage your username and password information. It also has the nice advantage of making it a lot easier for you as a user to sign into their site as you don't need to register or keep track of multiple extra account names and passwords.

For EVE Online, the SSO means that you can sign into a web site that has integrated the EVE SSO and confirm you are a specific character. While signing into a site you will be asked which character you wish to authenticate with and the web site that let you sign in with the EVE SSO will get confirmation from CCP that you own that character. The original web site will only ever get your character, they never see your account name or password. The original web site will not know what account that character is on or have any way, from us at least, of linking that character to any other character on the same account.

# Registering for the SSO
To use the SSO in your app, you must first register it at [the developers' site](https://developers.eveonline.com/). When you create a new application here it will give you a client ID and secret key, which are used in the authentication flow.

You are required to supply a callback URL and this is the only location the login server will redirect back to after the user has authorised the login (see the authentication flow for details).

You will also be asked to select what authentication scopes your application will ask for. At present, the only one is publicData, which gives access to market orders.

# Errors
Please note:

If too many HTTP requests are done to an SSO endpoint within a set time interval the SSO will return a HTTP 409 response (being vague on the number of requests and time on purpose as we will be tuning these values).

#Test Server
All instances of https://login.eveonline.com can be swapped for https://sisilogin.testeveonline.com when trying to use Sisi.

#Login Images
When creating a button to direct users to login to your site or application with the EVE SSO please use one of the following images for the button. This helps create consistency for EVE players and when they view your site or application will more easily be able to quickly identify that it supports the EVE SSO.

![EVE SSO Login Buttons Large White](https://images.contentful.com/idjq7aai9ylm/4PTzeiAshqiM8osU2giO0Y/5cc4cb60bac52422da2e45db87b6819c/EVE_SSO_Login_Buttons_Large_White.png?w=270&h=45) ![EVE SSO Login Buttons Large Black](https://images.contentful.com/idjq7aai9ylm/4fSjj56uD6CYwYyus4KmES/4f6385c91e6de56274d99496e6adebab/EVE_SSO_Login_Buttons_Large_Black.png?w=270&h=45)
![EVE SSO Login Buttons Small White](https://images.contentful.com/idjq7aai9ylm/18BxKSXCymyqY4QKo8KwKe/c2bdded6118472dd587c8107f24104d7/EVE_SSO_Login_Buttons_Small_White.png?w=195&h=30) ![EVE SSO Login Buttons Small Black](https://images.contentful.com/idjq7aai9ylm/12vrPsIMBQi28QwCGOAqGk/33234da7672c6b0cdca394fc8e0b1c2b/EVE_SSO_Login_Buttons_Small_Black.png?w=195&h=30)