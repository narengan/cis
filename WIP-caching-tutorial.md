---
copyright:
  years: 2018
lastupdated: "2018-03-05"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Caching and Page Rules tutorial

Page Rules give you the ability to take various actions based on the page's URL, such as creating redirects, fine tuning caching behavior, or enabling and disabling services.

A Page Rule takes effect on a given URL pattern that matches the following format:

`<scheme>://<hostname><:port>/<path>`

For example:

`https://www.example.com:80/image.png`

The `scheme` and `port` components are optional. If the scheme is omitted, it will cover both `http://` and `https://` protocols. If the `port` is not specified, the rule will match all ports. You can perform basic wildcard matches by using a `*` symbol in your rule pattern, allowing it to match a series of similar patterns.

**Important things to remember with Page Rules:**

 * Only one Page Rule will take effect on any given request
 * Page Rules are given priority in an order from top to bottom' Once a URL matches a rule, only that rule only will be applied; that is, if a Page Rule has triggered already on a request, any subsequent rules that also match the URL pattern will not take effect. 
 * As a general rule, we recommend ordering your rules from most specific to least specific.
 * Page rules can be paused, in which case they will take no action but can still be seen in the list and edited. The **Save as Draft** option creates a Page Rule that is paused initially.


## Forwarding (URL Redirection)
Redirects one URL to another using an HTTP 301/302 redirect. The contents of any section of a URL that a wildcard matches can later be referenced using $X syntax. X indicates the index of a glob in the pattern: $1 will be replaced with the first wildcard match, $2 with the second wildcard match, and so on.

For example, suppose you set the following rule:



Here, a request to "www.example.com/stuff/things" will be redirected to "http://example.com/stuff/things".

Be careful not to create a redirect in which the domain points to itself as a destination. This mistake can cause an infinite redirect error, and the affected URLs will not be able to resolve.


## Redirecting to HTTPS
If you want to redirect your visitors to use HTTPS, use the **Always Use HTTPS** setting instead:

Screenshot_from_2017-06-16_10-50-27.png


 

## Custom Caching
Sets caching behavior for any URL matching the page rule pattern, using any of our standard cache levels. The **Cache Everything** setting caches any content, even if it is not one of our normal static file types. The **Bypass** setting prevents caching on that URL.

When specifying cache level using Page Rules, you can set an edge cache TTL, which controls how long CIS will retain files in our cache. By default, this setting respects all existing headers, which uses standard HTTP caching headers to control cache age. You may set other cache lifetimes directly.

**Browser Cache TTL** controls how long resources cached by client browsers remain valid. If a browser requests a resource again and the TTL has not expired, it will receive an HTTP 304 (Not Modified) response. If you send a `max-age` header that is longer than this TTL, that value will take precedence. Customers can set TTLs ranging from 30 minutes to 1 year.

Not all default caching behaviors are strictly RFC-compliant. Setting **Origin Cache Control** by means of page rules uses a newer set of caching rules that seeks to adhere more closely to RFCs, primarily with respect to revalidation--for example, our default behavior with `max-age=0` is to not cache at all, whereas setting **Origin Cache Control** caches but always revalidates.

The following example sets a Rule to cache everything found in the "/images" folder. Cached resources will expire in 5 minutes in the user's browser, and will expire after one day in the IBM CIS datacenters:
