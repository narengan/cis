---
copyright:
  years: 2018
lastupdated: "2018-02-23"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Page Rules
The following table covers the page rules that are available to all customers, the behaviors they produce, and any special considerations you should keep in mind before using them.

| Page Rule | Behavior | Considerations |
|-----------|----------|----------------|
|Always Online| | |
|Always Use HTTPS| |Using this disables configuring all other settings for the rule. This is because CIS forces a redirect to HTTPS for the request, which becomes a new request that is then evaluated against page rules |
|Browser Cache TTL | ||
|Browser Integrity Check|Looks for common HTTP headers abused by spammers and denies access to your page. It also blocks visitors that do not have a user agent or add a non standard user agent (also commonly used by abuse bots, crawlers, or APIs). | |
|Bypass Cache Cookie|Serve a cached object unless we see a cookie of a specific name, for example, serve a cached version of the homepage unless we see a SessionID cookie indicating the customer is logged in and therefore should be presented personalized content. | |
|Cache Deception Armor| | |
|Cache Level| | |
|Disable Apps| | |
|Disable Performance| Disables the following features: <ul><li>Minification</li> <li>Rocket Loader</li> <li>Mirage</li> <li>Polish</li>| |
|Disable Security|Disables the following features: <ul><li>Email Obfuscation</li> <li>Server Side Excludes</li> <li>WAF</li> <li>Rate Limiting</li> <li>Scrape Shield</li>|If a rule is set to disable security, and another rule is set to enable the WAF, the WAF rule takes precedence regardless of the order in which they appear.|
|Email TTL| | |
|Email Obfuscation| | |
|Forwarding URL | | Using this will disable configuring all other settings because you are forwarding the request somewhere else.|
|Automatic HTTPS Rewrites| | |
|IP Geolocation Header| | |
|Polish|Offers compression rates up to 30-40% with either lossy or lossless compression.  | Polish should always be enabled in the lossless, ‘Basic’ mode, and even lossy for the majority of web applications.|
|Mirage|A mobile specific image optimization solution that “right-sizes” images based on the screen resolution, lazy loads images below the fold, bundles images and asynchronously loads them after page load to reduce the time until a mobile user can interact with a page. | |
|Opportunistic Encryption| | |
|Origin Cache Control| | |
|Rocket Loader|Grabs all javascript and forces it to be loaded asynchronously after the page load.| |
|Security Level| | |
|Server Side Excludes| | |
|SSL| | |
|WAF| | |
|Minification| |This requires a specific payload, see the example that follows. |
  
**Example:**

``` 
{

      "targets": [

        {

          "target": "url",

          "constraint": {

            "operator": "matches",

            "value": "https://wordpress.bossco.de/minification.html"

          }

        }

      ],

      "actions": [

        {

          "id": "minify",

          "value": {

            "html": "on",

            "css": "off",

            "js": "off"

          }

        }

      ],

      "priority": 1,

      "status": "active"

    }
    
```
    

## Enterprise Only Options
The rules in the following table are for Enterprise customers only.

| Page Rule | Behavior | Considerations |
|-----------|----------|----------------|
|Cache On Cookie| | |
|Host Header Override | | |
|Resolve Override | | |
|Custom Cache Key| | |
|Query String Sort | | |
|Origin Error Page Pass Through| | |
|True Client IP Header| | |
|Max Upload Size||CIS limits the maximum amount of data a visitor can upload per request. The limit is determined by the plan level. Enterprise: 500MB (default)|
|Response Buffering| | |
