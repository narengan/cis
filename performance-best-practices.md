---
copyright:
  years: 2018
lastupdated: "2018-02-27”

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}


# Best practices for performance

With IBM Cloud CIS, your site's performance is enhanced by speeding up the loading of your web content, as well as because your content is being loaded from proxied edge servers. Here are some specific best practices for enhancing the performance of your web content within CIS.

**Recommended and best practices**

 * Activate Web Content Optimization (WCO) features wherever possible
 * Cache as much of your static and semi-static web content as possible
 * For event-driven content, purge your cache using the API
 * For business and enterprise: use Railgun to accelerate dynamic content loading

## Best practice 1: Activate WCO features as much as possible

  * Use image compression
  * Enable Minification for HTMl and CSS files
  * Use client-side tools such as Mirage and Rocket Loader, where possible

## Best practice 2: Cache as much static and semi-static content as possible

  * Enable *8cache Everything** for static HTML web pages
  * Use conservative **Time to Live (TTL)** for your content that changes occasionally


## Best practice 3: For event-driven content, use the API to purge your cache

  * Purge the cache for individual files
  * Purge the cache by using a Cache-Tag
  * Purge the cache globally
  * Purge the cache by Page Rule

**Advanced caching features for Enterprise customers**

 * Bypass cache cookie: 
 * Cache on cookie
 * Custom cache keys

## Best practice 4: Use tools that accelerate your dynamic content loading

**Best practices when using Railgun**

 * Consider high-availability (HA) configuration
 * Keep Railgun outside the Load Balancer, if possible
 * Deploy Railgun near your origin server to reduce latency
