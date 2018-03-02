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

To enable **Always Online**, follow these steps:

 * Log in to your CIS account.
 * Select the domain you wish to modify.
 * Choose the "Caching" link on the menu at the top of the page.
 * Scroll to the "Always Online" section and toggle it on or off as needed.
 
 ## Origin Cache Control
 
   * placeholder
 
 ## Forwarding URL
 
To ensure that your content is always available (HA), you can set up a forwarding URL to be used in case your site is unavailable. 
 
 **Note:** When you enable a **Forwarding URL**, all of your other settings are disabled becuase you are sending all your traffic to another URL.
