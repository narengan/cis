---
  
copyright:
   years: 2018
lastupdated: "2018-02-27"
 
---


# Best practices for integrating CIS with your origin servers

IBM Cloud CIS is positioned at the edge of your network. You’ll need to take a few steps to guarantee a smooth integration with your CIS services. You can do these steps either before or after you change your DNS and activate our proxy service. These recommendations allow CIS to connect to your origin servers properly. They’ll help you prevent any issues with API or HTTPS traffic, and help your logs capture the correct IP addresses of your customers, rather than the protective CIS IP addresses.

Here’s what you’ll need to set up:

 * Step 1: Restore the originating IPs of your customers
 * Step 2: Incorporate CIS IP addresses
 * Step 3: Integrate API traffic with appropriate security settings
 * Step 4: Configure your SSL with a custom certificate and a Full (Strict) setting

**Step 1: Know how to restore the originating IPs of your customers**

As a reverse proxy, we provide the origination IP in these headers:

  * CF-Connecting-IP
  *  X-Forwarded-For
  * True-Client-IP (optional)

You can restore user IP addresses using a variety of tools, for infrastructures such as Apache, Windows IIS, and NGINX.

**Step 2: Incorporate CIS IP addresses to make integration smoother**

Here are the two steps to take:

  * Remove any rate limiting of CIS IP addresses
  * Set up your ACLs to allow only CIS IP addresses and other trusted parties

You can find the updated list of IP ranges for IBM CIS [at this location](need this link).

**Step 3: Review your security settings to make sure they don’t interfere with API traffic**

IBM CIS usually accelerates API traffic by removing connection overhead. However, the default security stance can interfere with many API calls. We recommend that you take a few actions to prevent interference with your API traffic once proxying is active.

 * Turn security features off selectively, using the **Page Rules** features.

  * Alternatively, you can turn off **Browser Integrity Check** globally.

*What does the Browser Integrity Check do?*

*The browser integrity check looks for HTTP headers that are commonly abused by spammers. It denies traffic with those headers access to your page. It also blocks visitors that do not have a user agent, or who add a non-standard user agent (this tactic is commonly used by abuse bots, crawlers. or APIs).*

**Step 4: Configure your SSL settings**

 * Upload a custom SSL certificate
 * Alternatively, utilize a certificate provisioned by CIS
 * Explore a keyless SSL configuration
 * Change your SSL setting to **Full** (Strict)

