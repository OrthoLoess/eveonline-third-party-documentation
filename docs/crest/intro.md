CREST is the new RESTfull API, destined to replace the older XML API. Currently there is far less data available on CREST, so the XML API is not going away for a long time. The main selling points of CREST include:

* CREST is capable of allowing write access, as well as read.
* CREST communicates directly with the game servers, rather than the backend database, so can better reflect the current state of the game.
* CREST is built with high traffic and complex loads in mind and has strong caching. Expect shorter cache timers and better performance and reliability.

# Public CREST
Public CREST is a version of the API that is available without authenticating through the SSO.

At present, most endpoints are available through public CREST, however as more are added, the majority are likely to require authentication. Specifically, write access will only be available on Authenticated CREST.

The list of endpoints available from the CREST root, as well as other references to other resources in the API include links to endpoints that require authentication. Trying to follow these links will return a 403:Forbidden HTTP response. It is important to note that this is true regardless of what authentication headers you might try to send, authentication is only available on the authed CREST server (A different root url).

# Walking
CREST is designed to be a properly RESTful API with good support for versioning and changes. As such, a well designed app will not break when things are changed on the API (most of the time!). To enable this one of the things your app should do is generate links to endpoints dynamically. The only hard coded URL will be to the root resource. Here you will find a list of all the other top level endpoints, with href elements for each.

To get the list of endpoints, you simply need to make an HTTP GET request to the appropriate root (SISI or TQ).

For more details on walking through endpoints, see the appropriate section of these docs.
