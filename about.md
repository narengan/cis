---
copyright:
  years: 2018
lastupdated: "2018-02-14"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# About IBM Cloud Internet Services
IBM Cloud Internet Services (CIS) provides a fast, highly performant, reliable and secure internet service for enterprise customers running their business on IBM Cloud.   

IBM Cloud CIS gets you going quickly by establishing defaults for you, which you can change easily from the API or UI interfaces. Here are some comonly changed parameters:

 * DNS settings : you can use CIS to host your DNS or you can create CNAME records.
 * Crypto settings (SSL) :  default is 'flexible' which encrypts the connection between your host and the CIS edge server, but does not encrypt the communication between the CIS edge server and origin server.
 * Firewall settings (IP reputation filter): default is 'medium' which is highly successful with few false positives, challenging about 1 in 50 million requests.
 * Speed settings: makes page loads faster, but can create some difficulty with Javascript. In particular, AutoMinify can be toggled off if Javascript pages have difficulty.
 * Cache : standard mode leads to the most bandwidth savings, but can be adjusted by each customer. Clear individual files when you are uploading new content, rather than rebuilding your entire cache, which takes much longer. You can use development mode to bypass the cache and still take advantage of security features such as the IP firewall.
 * Page Rules : lets specific page rules be applied according to each URL. Changes take effect immediately.

 ## Caching
 Caching stores static web content closest to the visitor, thus significantly enhancing the performance of the website.  A globally distributed delivery environment enables web content owners to provide a seamless experience.  

 ### Origin and Edge Servers
 An **origin** server is a computer running one or more programs that are designed to listen for and process incoming Internet requests. An origin server can take on all the responsibility of serving up the content for an Internet property such as a website. The origin server is represented as an IP address or a DNS name at which the application is exposed on the Internet. This could be a virtual or physical server, or even a local load balancer that is proxying multiple backend servers that the application runs on.

 Static content is stored on an **edge** server that is hosted by a caching service provider.  Caching uses a variety of technologies to optimize the website experience such as Automatic static content caching, quick cache purge, and edge cache expire TTL. The edge servers also implement WAF (if enabled) and DDoS mitigation functions when the proxy mode is in effect.

 ### Caching Options
 Caching options include:
 - **Shared certificate**: Offers an SSL Certificate to users that is provided by the vendor.
 - **Page Rules**: Define how traffic from visitors to the website is handled. Web sites can be set up to exercise fine-grained control over how visitors interact with the site on a page-by-page basis.
 - **SSL**: Supports users who would like to use latest web encryption technologies (TLS 1.2).
 - **Cache Purge**: Allows you to purge the cache content to allow for instant static content update.
 - **TTL configuration**:  Defines the length of time an edge server will cache a resource before returning to the origin server for a fresh copy.
 
## SSL Certificates
Encrypt communication to and from your website using Secure Socket Layer (SSL). It may take up to 24 hours after the site becomes active for new certificates to be issued.

You can find more information about SSL in our [FAQ file](faq.html).


 ## Web Application Firewall (WAF)
 IBM CIS provides Web Application Firewall (WAF), which examines web traffic looking for suspicious activity. It can automatically filter out illegitimate traffic based on rule sets that you apply to look at both GET and POST-based web requests. You can use various rule sets to determine what traffic to block, challenge, or let pass. WAF can block comment spam, cross-site scripting attacks, and SQL injections.

 You can enable or disable WAF at your discretion. We recommend that you always leave it on.

 ## DDoS Protection
 ### CIS DDoS Protection
 CIS DDoS stands between your website and attackers, regardless of the attack size or duration.

 ## Load Balancing
 CIS Load Balancing operates at the Authoritative DNS level. It incorporates advanced health checks to monitor the health of the origins, and dynamically adjusts DNS responses. Additionally, you can configure Geo policies for Global Load Balancing (GLB).

 ### Health checks
 Load Balancing Health Checks are performed on specific URLs through periodic HTTP/HTTPS requests, and are configured with customizable intervals, timeouts, and status codes. When an origin server is marked as unhealthy, visitors are routed away from failures using fast failover routes.
 
 ### Geo Policies and Global Load Balancing (GLB)
 Geo Policies allow you to control which origins a given client is directed to, based on the geo location of the client. For instance, you could configure your Geo policies such that visitors in Europe are sent to the nearest European origin for your website or application, U.S. visitors are sent to a North American origin, and so forth.


