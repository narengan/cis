---
copyright:
  years: 2018
lastupdated: "2018-01-18"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# FAQ

## What is SSL?
SSL is a standard security protocol for establishing encrypted links between a web server and a browser in an online communication. An SSL certificate is necessary to create an SSL connection with a website, and comprises of the domain name, the name of the company, and additional data such as company address, city, state, and country. It also shows the expiration date of the SSL certificate, and details of the issuing Certificate Authority (CA).

## How Does SSL Work?
Whenever a browser initiates a connection with an SSL secured website, it first retrieves the site's SSL Certificate to check if it's still valid. It  verifies that the CA is one that the browser trusts, and that the certificate is being used by the website for which it has been issued. If any of these checks fail, you'll get a warning indicating that the website is not secured by a valid SSL certificate.

When as SSL certificate is installed on a web server, it enables a secure connection between the web server and the browser that connects to it. The website's URL is prefixed with "https" instead of "http" and a padlock is shown on the address bar. If the website uses an extended validation (EV) certificate, the browser may also show a green address bar.

## Why do I see a privacy warning?
The SSL certificates issued by IBM Cloud CIS cover the root domain (example.com) and one level of subdomain (*.example.com). If you’re trying to reach a second-level subdomain (*.*.example.com) you will see a privacy warning in your browser, because these host names are not added to the SAN.

Also, please allow up to 15 minutes for one of our partner Certificates Authorities (CAs) to issue a new certificate. You’ll see a privacy warning in your browser if your new certificate has not yet been issued.

## What is DDoS?
A distributed denial-of-service (DDoS) attack is an attempt to make an online service unavailable by overwhelming it with traffic from multiple sources. In a DDoS attack, multiple compromised computer systems attack a target such as a server, website, or other network resource, and which affects users of the targeted resource.

The flood of incoming messages, connection requests, or malformed packets to the target system forces it to slow down or even crash and shut down, thereby denying service to legitimate users or systems. DDoS attacks have been carried out by diverse threat actors, ranging from individual criminal hackers to organized crime rings and government agencies.

## What do I do if I’m under a DDoS attack?

**Step 1:** Turn on “Defense mode" [Here's how](needs a link).

**Step 2:** Set your DNS records for maximum security.

**Step 3:** Do not rate-limit or throttle requests from IBM CIS, we need the bandwidth to assist you with your situation.

**Step 4:** Block specific countries and visitors if necessary.





