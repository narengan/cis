
# Caching and Page Rules tutorial

Page Rules give you the ability to take various actions based on the page's URL, such as creating redirects, fine tuning caching behavior, or enabling and disabling our various services.

A Page Rule will take effect on a given URL pattern, matching the following format:

<scheme>://<hostname><:port>/<path>

An example using each component would be:

https://www.example.com:80/image.png

The scheme and port components are both optional. If the scheme is omitted, it will cover both http:// and https:// protocols. If the port is not specified, then the rule will match all ports. You can perform basic wildcard matches by using a ‘*’ symbol in your rule pattern, allowing it to match a series of similar patterns rather than just one.

There are two important things to note with Page Rules:

 * Only one Page Rule will take effect on any given request
 * Page Rules are given priority in an order from top to bottom
 * Once a URL matches a rule, only that rule only will be applied - ie. if a Page Rule has already triggered on a request, any subsequent rules that also match the URL pattern will not take effect. As a general rule, we recommend ordering your rules from most specific to least specific.

Page rules can be paused, in which case they will take no action but can still be seen in the list and edited. The Save as Draft option will create a page rule that is paused initially.

 

Forwarding (URL Redirection)
Redirects one URL to another using an HTTP 301/302 redirect. The contents of any section of a URL that a wildcard matches can later be referenced using $X syntax. X indicates the index of a glob in the pattern: $1 will be replaced with the first wildcard match, $2 with the second wildcard match, and so on.

For example, suppose you set the following rule:



Here, a request to "www.example.com/stuff/things" will be redirected to "http://example.com/stuff/things".

Be careful not to create a redirect where the domain points to itself as a destination. This can cause an infinite redirect error, and the affected URLs will not be able to resolve.


Redirecting to HTTPS
If you want to redirect your visitors to use HTTPS, just use the Always Use HTTPS setting instead:

Screenshot_from_2017-06-16_10-50-27.png


 

Custom Caching
Sets caching behavior for any URL matching the page rule pattern, using any of our standard cache levels. The Cache everything setting will cache any content, even if it is not one of our normal static file types. The Bypass setting will prevent caching on that URL.

When specifying cache level via page rules, you can optionally set an edge cache TTL, which controls how long we will retain files in our cache. By default, this setting is to respect all existing headers, which uses standard HTTP caching headers to control cache age. You may set other cache lifetimes directly, depending on your plan.

Browser Cache TTL controls how long resources cached by client browsers remain valid. If a browser requests a resource again and the TTL has not expired, it will receive an HTTP 304 (Not Modified) response. If you send a max-age header that is longer than this TTL, that value will take precedence. Free, Pro, and Business customers can set TTLs ranging from 30 minutes to 1 year; Enterprise customers have additional options down to 30 seconds, and can choose to respect the existing max-age header.

Not all default caching behaviors are strictly RFC-compliant. Setting Origin Cache Control via page rules uses a newer set of caching rules that seeks to adhere more closely to RFCs, primarily with respect to revalidation--for example, our default behavior with max-age=0 is to not cache at all, whereas setting Origin Cache Control caches but always revalidates.

The Following example will set a Rule to cache everything found in the "/images" folder. Cached resources will expire in 5 minutes in the user's browser, and will expire after one day in Cloudflare's datacenters:
