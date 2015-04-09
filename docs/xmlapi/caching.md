# Introduction
It is impossible to overstate how important it is to correctly cache certain endpoints on the XML API. To use a cautionary example:

> If you pull the asset list for a character and don't cache it, you will not be able to get that data again for 6 hours.

Fortunately this behaviour is only found on a few endpoints, specifically those using the long cache style.

# Cache Styles
The API has two major styles of caching in use. Long and Short. They are picked based on whether or not the API is able to store the data internally. Some things are just too large to effectively store in memory, so there are some pages that will not cache the data. The XML data files accessible via the API all have a currentTime and cachedUntil element. The currentTime is the current time where the server is located. The cachedUntil element indicates at what time (based on local time where the server is located) you are required to wait before you try accessing that XML file again. It is not guaranteed that the data for that XML file will be updated since the cachedUntil time and the time the data is updated internally are not in sync.

### Long Cache Style
The long cache style is used on pages that have long intervals and are not cached in memory on CCP's servers. Examples of this include the asset list, market transactions, and journal entries. If you request the data from one of these pages, you only get one shot at it until the cache timer expires.

It is recommended in your API library that you store these pages locally when you request them. Then, if you need to reload the data, you can do it from your local cache without having to wait until the timer expires.

Typical timer lengths are 1-23 hours with this caching style.

### Short Cache Style
As opposed to the long cache style, pages that use the short cache style method allow you to revisit them in between cache hits. The data you get will be pulled from the cache, i.e., not updated from the database. These methods are suitable for use in such applications as widgets/gadgets/whatevers that don't have local cache.

It is still highly encouraged for you to obey the timer. You will not get new data until it actually expires. Asking for the same data you've already been given is somewhat silly, and so should be avoided if at all possible.

### Modified Short Cache Style
The same in almost every respect to the short cache style, this particular caching style changes the cachedUntil timer semantics slightly. Instead of telling you when the data will be updated, you will always be told the cache interval. In effect, this is used to spread out requests on global pages that are hit often.

For example, this style is used on the map data pages to help prevent stampeding (everybody requesting the same resource at the same time). As long as you obey the cachedUntil timer, all will be well.

# Cached Until Values
Please very much to the best of your ability obey the cachedUntil values. This is generally best accomplished with some kind of local caching mechanism.