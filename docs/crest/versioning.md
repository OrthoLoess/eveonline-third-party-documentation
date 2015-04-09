# Accept and Content-Type Headers

In order to help app developers preserve compatibility across updates to the CREST API, whenever an endpoint receives a breaking change, a new version is created and the old version remains available.

In order to request a specific version, you should send an Accept header, containing the appropriate Content-Type for the resource. It is good practice to always send this header in production, so that your app will continue to use a version of the resource that is known to work, regardless of changes made to CREST.

The easiest way to find the latest Content-Type for the endpoint is to make a request with no Accept header. If no such header is sent, the latest version is always returned. For example, a call to the Public CREST root, with no headers attached will contain the following in the response headers:

    Content-Type: application/vnd.ccp.eve.Api-v3+json; charset=utf-8

In order to ensure that you always receive this version, you simply need to add this header to your POST (ignore the charset for versioning):

    Accept: application/vnd.ccp.eve.Api-v3+json

If you need version 2 of this resource, you can send this header instead:

    Accept: application/vnd.ccp.eve.Api-v2+json

# The X-Deprecated Header

To help you find out when a resource is updated, old versions will send an X-Deprecated header. It is up to you to decide what to do with this in your app to help alert you to update it.

# Breaking Changes

Not all API changes will trigger a new version. Specifically it has been announced that new items can be added to endpoints without changing the version. Because of this, your app should not rely on there only being certain items in the json of a response.

Any change that removes something from the result, or changes the format of data will normally be made in a new version.