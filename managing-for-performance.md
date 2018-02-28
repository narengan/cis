---
copyright:
  years: 2018
lastupdated: "2018-02-27”

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Managing your CIS deployment for best performance

IBM Cloud Internet Services can provide the fastest experience for your customers because it optimizes your images, and it stores your web content as near as possible to your end-users. Your content is loaded from proxied edge servers (which reduces latency).

With IBM Cloud CIS, you can enhance your site's performance further by using best practices to speed up the loading of your web content. Here are some specific best practices for enhancing the performance of your web content within CIS.

**Recommended and best practices**

 * Activate Web Content Optimization (WCO) features wherever possible
 * Cache as much of your static and semi-static web content as possible
 * For event-driven content, purge your cache using the API
 * For business and enterprise: use Railgun to accelerate dynamic content loading

## Best practice 1: Activate WCO features as much as possible

  * Use image compression
  * Enable Minification for HTMl and CSS files
  * Use client-side tools such as Mirage and Rocket Loader, where possible

### Image compression with Polish
Polish can use lossy or lossless compression to achieve  compression rates of up to 30-40%. For the majority of web applications, enable Polish in the lossless, ‘Basic’ mode.

### Reduce HTML and CSS load times with Minification
Enable Minification to remove comments and formatting meant for humans, and improve your load times. Minification can be safely enabled for HTML and CSS, but make sure that all line endings in Javascript are denoted with a semicolon before enabling.

### Mirage and Rocket Loader tools
CIS can accellerate content using client-side tools such as Mirage and Rocket Loader. Test these tools carefully before enabling them for production environments.  They are enabled for specific pages or subdomains using Page Rules.

## Best practice 2: Cache as much static and semi-static content as possible

  * Enable **Cache Everything** for static HTML web pages
  * Use conservative **Time to Live (TTL)** for your content that changes occasionally

### Utilize conservative TTLs (Time-to-Lives) for content that changes occasionally
If content rarely changes, you can set a conservative TTL to utilize our cache as much as possible. A good way to tell if your TTLs may need to be adjusted is by watching your Status Codes in our Analytics App for an abundance of 304 requests. If you have a high percetange of re-validation requests, you could likely increase the TTLs of your content without negatively impacting your customers. This will use our cache more effectively and increase performance since you’’ll revalidate less often.

### How do I tell if items are being cached?
CIS adds the response header `CF-Cache-Status` if attempting to cache the object. If successful, the value of this header indicates:

* **MISS:** Not yet in the cache or the TTL expired (i.e. cache-control max age of 0).
* **HIT:** Asset delivered from cache.
* **EXPIRED:** Delivered from cache, but the next request will require revalidation.
* **REVALIDATED:** Delivered from cache. The TTL was expired, but a `If-Modified-Since` request to the origin indicated the asset has not changed so the version in cache is considered valid again.


## Best practice 3: For event-driven content, use the API to purge your cache

For example, Everytime a new post is added to your blog, you could easily purge the CIS cache using an API command. It is very common to see event-driven content, and we make it easy to ensure no stale content is reaching your users. The necessary commands are listed below to purge the cache immediately across our entire global network either via our Caching Application or via the API.

  * Purge the cache for individual files
  * Purge the cache by using a Cache-Tag
  * Purge the cache globally
  * Purge the cache by Page Rule

### Purge the cache for individual files
Purging individual objects is a great way to maintain your cache-hit ratio while still ensuring certain objects are re-validated in our cache. 

[API Documentation](https://api.cloudflare.com)

### Purge the cache by Cache-Tag
Cache-Tags allow you to define buckets of content that you wish to purge. This is an excellent way to combine objects that are commonly changed together. So an HTML blog post, for example, and all of its image content could be tagged together. Mobile-only content could also be bundled using cache-tags to purge everything when you push a new update to your mobile domain.

### Purge the cache globally
You also have the option to force our entire cache to revalidate. This allows you to reset all of the objects stored in our cache to ensure every request will return to the origin.

### Purge the cache by Page Rule
Page Rules allow you to effectively purge the entire cache by a basic regular expression. These let you utilize a pre-defined Page Rule and re-validate all hits against that Page Rule.

### Use advanced caching features for Enterprise customers

**Bypass Cache Cookie -** The ability, configured in a page rule, to serve a cached object unless we see a cookie of a specific name, e.g., serve a cached version of the homepage unless we see a SessionID cookie indicating the customer is logged in and therefore should be presented personalized content.

**Cache on Cookie -** Presents a cached page when only when we see a specific cookie, e.g., only serves a cached page once a device type cookie has been set by the origin server.

**Custom Cache Keys -** Generally, objects in CIS’s cache are referenced by only their URI, e.g., `https:// www.example.com/logo.png`. We offer the ability to create custom cache keys so that a different object is served for the same URI based on any arbitrary request header or cookie, e.g., `https://www.example.com/logo.png` with a device type cookie set to desktop would be a different object in our cache than `https://www.example.com/logo.png` with device type cookie set to tablet.

## Best practice 4: Accelerate your dynamic content with Railgun
Web applications often render personalized, dynamic content which means that this content must be proxied through to the origin server. Railgun is an optional feature available to Business & Enterprise accounts that accelerates requests for this type of personalized content. Railgun is fundamentally a de-duplicating proxy. The railgun listener is installed within the customer’s origin infrastructure so that before a response is sent from the origin infrastructure, a binary diff is performed with the last resource at the same URI. For example, when Bob attempts to access his shopping cart page, the application server renders it, but before it leaves the origin datacenter, the railgun listener compares Bob’s page with Alice’s page, and only sends the difference.

[Documentation](https://www.CIS.com/docs/railgun/)

### Railgun Best Practices
The following are best practices for using Railgun.

**Consider high-availability (HA) configuration** - As CIS will fall back to HTTP in the event railgun fails, a high availability solution is generally not required. If high availability is a preferred solution, all railgun instances should be placed behind a layer 3 load-balancer and registered with the same activation code. If configured in an active/active configuration, Railguns should share memcache to improved the cache hit rate. If configured in an active/passive configuration, Railguns can have independent memcaches.

**Railgun should be outside of a load-balancer if possible** - The railgun listener (stand-alone or cluster) should logically sit outside of the load balancer allowing requests for all application servers to flow through the same railgun instance increasing the cache hit ratio. Keep Railgun near the origin. The railgun listener should be less than 5 milliseconds from your application server.

**Railgun can easily be created within AWS** - We’ve provided a link to some excellent [documenation](https://www.edge-cloud.net/2016/02/17/CIS-railgun-on-aws/) from our friends at AWS.
