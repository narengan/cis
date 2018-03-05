---
copyright:
  years: 2018
lastupdated: "2018-03-02"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Managing your CIS deployment for optimal reliability

To achieve optimal reliability for your IBM Cloud CIS deployment, you can set up a helpful DNS configuration and you can set up Global Load Balancers. For additional reliability, you can use our Page Rules to be sure that your web content will be delivered to your customers, even if your origin server or the cache has a problem. This document gives details about some best practices for making your CIS deployment optimally reliable.

Generally, our recommended best practices are these:

 * Set up your DNS to take advantage of IBM CIS proxy servers and other features
 * Use one or more Global Load Balancers to distribute your site traffic evenly
 * Set up appropriate Page Rules to manage your caching and other options

Each of these items provides certain functionality you can use to create a more reliable CIS deployment.

Notice that the CIS interface is organized into sections for *security*, *reliability*, and *perfomance*. The main navigation menu is shown in the following figure, with the Global Load Balancers and DNS menu items are revealed:

![Left navigation DNS ](images/cis-left-navigation.png)


## Setting up DNS
 
 To get started setting up your DNS configuration, select **DNS** from the navigation menu, as shown previously.
 
 For detailed information about settng up and managing your DNS for reliability, please [refer to this document]().


## Setting up Global Load Balancers


To get started setting up your Global Load Balancers, select **Global Load Balancers** from the navigation menu.

 For detailed information about settng up and managing your Global Load Balancers, please [refer to this document]().

## Using Page Rules to increase reliability

Here are some recommended Page Rule settings to give your site maximum reliability:

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

 * To trigger **Always Online**, your web server must be returning a standard HTTP Error code of 502 or 504 timeout. Always Online also works when we encounter issues contacting your origin (Errors 521 & 523), timeouts (522 & 524), SSL errors (525 & 526) or an unknown error (520). **Always Online** will not be triggered for other HTTP response codes, such as 404s, 500, 503, database connection errors, internal server error, or empty replies from server.

 * **Always Online** will not work if a "Cache Everything" page rule is enabled with the "Edge Cache Expire TTL" lower than the caching frequency (Free customers: 7 days, Pro customers: 3 days, and Business and Enterprise customers: 1 day), because the "Edge Cache Expire TTL" causes the **Always Online** cache to be purged in the corresponding interval.

 * **Always Online** will not function if you have the United States listed as a country on your Threat Control block list. If the US is listed as a block, the **Always Online** crawler will not be able to crawl your site.

## Origin Cache Control

You can use the *Origin Cache Control* Page Rule settings to determine what content is cached from your origin and how often the content is updated, which has an effect on reliability and on performance. By default, if no settings are changed and no headers that prevent caching are sent from your origin server, IBM CIS caches all static content with certain extensions. These types of content include images, CSS, and JavaScript. This caching is primarily for performance reasons.

To set up **Origin Cache Control** you would use Page Rules to turn on specific headers that give the desired behavior with respect to each resource of your content. To understand how to use **Origin Caache Conrol**, some more general explanation of Page Rules and overall caching behavior for CIS is required to provide context, which you'll see in the next several sections. Three methods exist that you can use to control caching in general, and **Origin Cache Control** is the second one.

Setting **Origin Cache Control** invokes caching rules that seek to adhere closely to internet best practices and RFCs, primarily with respect to revalidation. For example, the CIS default behavior with `max-age=0` is not to cache at all, whereas setting **Origin Cache Control** caches, but it always revalidates.

### How to set up Origin Cache Control

 * Log into your IBM CIS account.
 * From the dropdown menu on the top left, select your domain.
 * Select the **Page Rules** app.
 * Apply the Page Rules Origin Cache Control settings that best meet your requirements, as described in the following sections.

### Page Rule precedence

Two specific Page Rules take precedence for caching overall:

 * If a Page Rule is set to "Bypass Cache", the resources that match that Page Rule are not cached. CIS still acts as a proxy, and our other performance features remain active. However, your content won't be served from our cache, it will be fetched from your origin server directly.

 * If a Page Rule is set to "Cache Everything", resources that match the Page Rule are cached. Using this Page Rule setting is the only way to tell us to cache resources beyond what we consider static, including HTML.

 * If no Page Rule is set, we will use the Standard caching mode, which is based the extension of the resource. We will cache static resources only (as mentioned previously).

### Origin cache-control headers

The second way to alter what IBM CIS will cache is through caching headers sent from the origin. CIS will respect these settings, but you can override them by specifying an "Edge Cache TTL". Here are the headers we consider when deciding what resources to cache from your origin:

 * If the Cache-Control header is set to `private`, `no-store`, `no-cache`,  or `max-age=0`, or if there is a cookie in the response, then CIS will not cache the resource. Note that all sensitive material should not be cached, so you might consider using one of these headers in that case.

 * If the Cache-Control header is set to `public` and the `max-age` is greater than 0, or if the `Expires` headers are set any time in the future, we will cache the resource.

**Note:** As per RFC rules, `Cache-Control: max-age` trumps `Expires` headers. If we see both and they do not agree, `max-age` wins.

### Using the 's-maxage' header

The third way to control caching behavior and browser caching behavior together is by using the `s-maxage` Cache-Control header.

Normally we respect the `max-age` directive:

`Cache-Control: max-age=1000`

But if you would like to specify a cache timeout that's different from the browser, we can use `s-maxage`. Here's an example that tells IBM CIS to cache the object for 200 seconds and the browser to cache the object for 60 seconds.

`Cache-Control: s-maxage=200, max-age=60`

Basically `s-maxage` is intended to be followed ONLY by reverse proxies (so the browser should ignore it) whilst on the other hand we (IBM CIS) give priority to `s-maxage` if it is present. We will respect whichever value is higher: the browser cache setting or the `max-age` header.

### Summary on cache control headers and Page Rules for reliability

To sum up, here are some main areas to consider for reliability with regard to caching:

 * Check your origin's caching headers to make sure there are no overriding headers for cacheable resources (`Cache-Control` and `Expires`).

 * CIS always caches static content by default, with the following TTL depending on the return code:

```
200 301    120m;
302 303    20m;
403        5m; for reliability
404        5m;
any        0s;
```

 * To cache more, create a Page Rule set to cache everything on the desired URL (if your webserver returns a 404 when requesting this URL, we will cache this result for 5mn only).

 * To avoid caching on a URL, create a Page Rule to bypass the cache.


 ## Forwarding URL

To ensure that your content is always available (HA), you can set up a forwarding URL to be used in case your site is unavailable.

 **Note:** When you enable a **Forwarding URL**, all of your other settings are disabled becuase you are sending all your traffic to another URL.

### How to set up a forwarding URL

 * Log into your IBM CIS account.
 * From the dropdown menu on the top left, select your domain.
 * Select the **Page Rules** app.
 * Add a new page rule, and select enable Forwarding.
 * Enter the destination URL and select the forwarding type.

### Forwarding examples:

Imagine you want to make it easy for anyone coming to reach a URL such as:

    *www.example.com/+

    *example.com/+

This pattern will match:

    http://example.com/+
    http://www.example.com/+
    https://www.example.com/+
    https://blog.example.com/+
    https://www.blog.example.com/+
    Etc...

It will not match:

    http://www.example.com/blog/+  [extra directory before the +]
    http://www.example.com+  [no trailing slash]


Once you've created the pattern that matches what you want, click the **Forwarding** toggle to expose a field in which you can enter the forwarding address. For example:

    https://plus.google.com/yourid

Enter that URL in the **Forwarding** field and click the **Add Rule** button. Within a few seconds any requests that match the pattern will be forwarded to the new URL with a 302 Redirect.

### Advanced forwarding options:

If you use a basic redirect, such as forwarding the root domain to www.yourdomain.com, you lose anything else in the URL. For example, you could set up the pattern:

    example.com

And have it forward to:

    http://www.example.com

But then if someone entered:

    example.com/some-particular-page.html

Then they'd be redirected to:

    www.example.com

instead of

    www.example.com/some-particular-page.html

The solution is to use variables. Each wildcard corresponds to a variable that can be referenced in the forwarding address. The variables are represented by a `$` followed by a number. To refer to the first wildcard you'd use `$1`, to refer to the second wildcard you'd use `$2`, and so on. To fix the forwarding from the root to `www` in the previous example, you could use the same pattern:

    example.com/*

You'd then set up the following URL for traffic to forward to:

    http://www.example.com/$1

In this case, if someone went to:

    example.com/some-particular-page.html

They'd be redirected to:

    http://www.example.com/some-particular-page.html
