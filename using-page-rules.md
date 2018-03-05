---
copyright:
  years: 2018
lastupdated: "2018-02-28"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Using Page Rules

A Page Rule specifies some settings and values that you can apply to a specific URL. Page Rules help you manage security and performance, based on each individual URL in your site. The following table describes the Page Rules that are available to all customers, the behaviors they produce, and any special considerations you should keep in mind before using them.

## Security

| Rule Settings | Behavior | Considerations |
|-----------|----------|----------------|
|Browser Integrity Check|Looks for common HTTP headers abused by spammers and denies access to your page. It also blocks visitors that do not have a user agent or add a non standard user agent (also commonly used by abuse bots, crawlers, or APIs). | |
|Disable Security|Disables the following features: <ul><li>Email Obfuscation</li> <li>Server Side Excludes</li> <li>WAF</li> <li>Rate Limiting</li> <li>Scrape Shield</li>|If a rule is set to disable security, and another rule is set to enable the WAF, the WAF rule takes precedence regardless of the order in which they appear.|
|Email Obfuscation|Toggles Email Obfuscation on or off. | |
|IP Geolocation Header|Includes the country code of the visitor location with all requests to your website. The information will be found in the CF-IPCountry HTTP header. | |  
|Security Level|Controls how high a client threat score must be for a client will encounter a challenge page, and can be used to set part of your site to always present visitors with the Under Attack mode challenge before they can visit your site. | |
|Server Side Excludes|Toggles SSE on or off.  | |
|SSL|Controls which of the SSL modes is used. | |
|WAF|Toggles WAF on or off. | |  
|Automatic HTTPS Rewrites|Toggles Automatic HTTPS Rewrites on or off.  | |
|Opportunistic Encryption|Toggles Opportunistic Encryption on or off.  | |
|Always Use HTTPS| |Using this disables configuring all other settings for the rule. This is because CIS forces a redirect to HTTPS for the request, which becomes a new request that is then evaluated against page rules |

## Performance
| Rule Settings | Behavior | Considerations |
|-----------|----------|----------------|
|Browser Cache TTL | ||
|Bypass Cache Cookie|Serve a cached object unless we see a cookie of a specific name, for example, serve a cached version of the homepage unless we see a SessionID cookie indicating the customer is logged in and therefore should be presented personalized content. | |
|Cache Level| | |
|Edge Cache TTL| | |

## Reliability
| Rule Settings | Behavior | Considerations |
|-----------|----------|----------------|
|Always Online|Keeps a limited version of the site online if the server goes down. |For more information view [Managing your CIS deployment for optimal reliability](managing-for-reliability.html) |
|Origin Cache Control|Determine what content is cached from the origin and how often the content is updated |For more information view [Managing your CIS deployment for optimal reliability](managing-for-reliability.html) |
|Forwarding URL |URL to be used in case the site is unavailable. | Using this disables configuring all other settings because you are forwarding the request somewhere else. For more information view [Managing your CIS deployment for optimal reliability](managing-for-reliability.html)|

## Page Rule URL patterns

A Page Rule will take effect on a given URL pattern, matching the following format:

`<scheme>://<hostname><:port>/<path>`

An example using each component would be:

`https://www.example.com:80/image.png`

The *scheme* and *port* components are optional. If the scheme is omitted, it will cover both `http://` and `https://` protocols. If the port is not specified, then the rule will match all ports. You can perform basic wildcard matches by using a ‘*’ symbol in your rule pattern, allowing it to match a series of similar patterns rather than just one.

There are two important things to remember with Page Rules:

 * Only one Page Rule will take effect on any given request
 * Page Rules are given priority in an order from top to bottom
 * Once a URL matches a rule, only that rule only will be applied; that is, if a Page Rule has already triggered on a request, any subsequent rules that also match the URL pattern will not take effect. As a general rule, we recommend ordering your rules from most specific to least specific.

Page rules can be paused, in which case they will take no action but can still be seen in the list and edited. The *Save as Draft* option will create a page rule that is paused initially.
