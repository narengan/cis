---
copyright:
  years: 2018
lastupdated: "2018-03-02"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Managing your CIS deployment for optimal reliability

To achieve optimal reliability for your IBM Cloud CIS deployment, you can use our Page Rules to be sure that your web content wil be delivered to your customers, even if your origin server or the cache has a problem.

Here are the best Page Rule settings to give your site maximum reliability:

 * Always Online
 * Origin Cache Control
 * Forwarding URL
 
 ## Always Online
 
**Always Online** keeps a limited version of your site online if your server goes down.

With **Always Online**, your server goes down, IBM CIS will serve pages from our cache, so your visitors still see some of the pages they are trying to visit. Your visitors will see a message at the top of the page telling them that they are in offline browsing mode. Always Online returns an HTTP status 503, however, 503 is also used by many other web applications. When your server comes back online, IBM CIS will bump users back to regular browsing seamlessly.

If IBM CIS does not have the requested page in its cache, your visitor sees an error page letting them know that the website page they are requesting is offline.

### How to set up Always Online

To enable **Always Online**, follow these steps:

 * Log in to your CIS account.
 * Select the domain you wish to modify.
 * Choose the "Caching" link on the menu at the top of the page.
 * Scroll to the "Always Online" section and toggle it on or off as needed.
 
 ### Limitations of Always Online
 
 * Only content hosted on the domain that has **Always Online** enabled will be cached in the **Always Online** cache.
 
 * **Always Online** caches the first 10 links from your root HTML, then just the first links from each of those pages, and finally the first links from each of those subsequent pages. This means that only some pages on your site will be viewable when your origin server goes down.
  
 * Recently added sites won't have a large cache of their site available, which means that **Always Online** may not work if you only added the site a few days ago.
 
 * CIS won't be able to show private content or handle form submission (POSTs) if your server is down. Visitors will be shown an error on checkout pages or items requiring a login to view.
 
 * To trigger **Always Online**, your web server must be returning a standard HTTP Error code of 502 or 504 timeout. Always Online also works when we encounter issues contacting your origin (Errors 521 & 523), timeouts (522 & 524), SSL errors (525 & 526) or an unknown error (520). Always Online will not be triggered for other HTTP response codes, such as 404s, 500, 503, database connection errors, internal server error, or empty replies from server.
 
 * **Always Online** will not work if a "Cache Everything" page rule is enabled with the "Edge Cache Expire TTL" lower than the caching frequency (Free customers: 7 days, Pro customers: 3 days, and Business and Enterprise customers: 1 day), because the "Edge Cache Expire TTL" causes the **Always Online** cache to be purged in the corresponding interval.
 
 * **Always Online** will not function if you have the United States listed as a country on your Threat Control block list. If the US is listed as a block, the **Always Online** crawler will not be able to crawl your site.
 
 ## Origin Cache Control
 
Not all caching behaviors are strictly RFC-compliant. Setting **Origin Cache Control** invokes caching rules that seek to adhere closely to RFCs, primarily with respect to revalidation. For example, the CIS default behavior with `max-age=0` is not to cache at all, whereas setting **Origin Cache Control** caches, but it always revalidates.
 
 ## Forwarding URL
 
To ensure that your content is always available (HA), you can set up a forwarding URL to be used in case your site is unavailable. 
 
 **Note:** When you enable a **Forwarding URL**, all of your other settings are disabled becuase you are sending all your traffic to another URL.
