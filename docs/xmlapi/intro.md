# XML API
The EVE XML API is an HTTP **read only** API to the EVE Universe. The API has both publicly accessible information and private character/corporation information. Using the API does not require any kind of registration, simply point your HTTP requests to the correct locations, or use one of the many third-party libraries, and away you go.

## Accessing The API
As the XML API is an HTTP API you can access it by simply pointing your browser at the correct endpoints. An example of this would be: ```https://api.eveonline.com/eve/CharacterInfo.xml.aspx?characterID={character_id_here}```

The above will take you to the public character information for the specific character ID.

If you would like to access private information you will need an API key and can then do it like so: ```https://api.eveonline.com/corp/IndustryJobsHistory.xml.aspx?keyID={api_key_id_here}&vCode={api_verification_code_here}```

* Base URL: [https://api.eveonline.com/](https://api.eveonline.com/)
* API Keys: [https://community.eveonline.com/support/api-key](https://community.eveonline.com/support/api-key)

It is highly recommended that you consider using an existing [library](https://wiki.eveonline.com/en/wiki/XML_API_Libraries) to make accessing the API easier.

You can also find some examples for getting started with the API over [here](https://wiki.eveonline.com/en/wiki/XML_API_Getting_Started).

## Other Information
### Rate Limits
- General Rate Limit: 30 requests per second
- Error Rate Limit - Max Exceptions: 300
- Error Rate Limit - Exception Interval: 3 minutes
- Error Rate Limit - Block For: 15 minutes

The error rate limit means that if your application generates more than 300 exceptions within 3 minutes you will automatically be banned from the API for 15 minutes.

If for some reason you require more than 30 requests per second on the API please feel free to contact us and we can discuss giving you a higher limit. For the most part very few people should need that, 30 requests per second is a fairly large number. The white listing is not an excuse for you as a developer being lazy or ignoring the cache timers.

### User-Agent
Consuming the XML API does not require you as a developer to register or pass any unique identification with each request. While this is makes getting into and developing with the API very easy, it means aside from the IP address CCP has very little way in identifying who the requests are coming from.

We ask that if you are going to consume the API that you pass a custom [User-Agent](http://en.wikipedia.org/wiki/User_agent) header along with your requests. The User-Agent should primarily include information on how we can contact you, but it is also a good idea to include your application name and version.

If at all possible if something goes wrong with you application and we are considering banning it from the API, we will attempt to contact you first before banning. There are of course other reasons for us to contact you, but that is the primary one.

A good User-Agent header makes CCP very happy.

### Test Server
The Singularity test server has the XML API running and is in most cases updated before Tranquility. We do highly encourage third-party developers to test new API features on Singularity and provide feedback.

* Base URL: [https://api.testeveonline.com/](https://api.testeveonline.com/)
* API Keys: [https://community.testeveonline.com/support/api-key](https://community.testeveonline.com/support/api-key)

New features being deployed to Singularity will often be announced in the dev blogs of the developer web site and/or the [technology lab](https://forums.eveonline.com/default.aspx?g=topics&f=263) forums section.