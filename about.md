---
copyright:
  years: 2018
lastupdated: "2018-02-13"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# About IBM Cloud Internet Services
IBM Cloud Internet Services (CIS), powered by Cloudflare, provides a fast, highly performant, reliable and secure internet service for enterprise customers running their business on IBM Cloud.   

IBM Cloud CIS allows you to tune most of its features to suit your needs, including:

 * IP firewall sensitivity and range blocking
 * Cache and page rules
 * Use of SSL certificates
 
IBM Cloud CIS gets you going quickly by establishing defaults for you, which you can change easily from the API or UI interfaces. Here are some comonly changed parameters:

 * DNS settings : you can use CIS to host your DNS or you can create CNAME records.
 * Crypto settings (SSL) :  default is 'flexible' which encrypts the connection between your host and the CIS edge server, but does not encrypt the communication between the CIS edge server and origin server.
 * Firewall settings (IP reputation filter): default is 'medium' which is highly succesful with few false positives, challenging about 1 in 50 million requests.
 * Speed settings: makes page loads faster, but can create some difficulty with Javascript. In particular, AutoMinify can be toggled off if Javascript pages have difficulty.
 * Cache : standard mode leads to the most bandwidth savings, but can be adjusted by each customer. Clear individual files when you are uploading new content, rather than rebuilding your entire cache, which takes much longer. You can use development mode to bypass the cache and still take advantage of security features such as the IP firewall.
 * Page Rules : lets specific page rules be applied according to each URL. Changes take effect immediately.
