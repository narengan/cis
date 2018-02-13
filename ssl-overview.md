---

copyright:
  years: 2018
lastupdated: "2018-01-24"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# SSL Certificates

Encrypt communication to and from your website using Secure Socket Layer (SSL). It may take up to 24 hours after the site becomes active for new certificates to be issued.

## What is SSL?

SSL is a standard security protocol for establishing encrypted links between a web server and a browser in an online communication. An SSL certificate is necessary to create an SSL connection with a website, and comprises of the domain name, the name of the company, and additional data such as company address, city, state, and country. It also shows the expiration date of the SSL certificate, and details of the issuing Certificate Authority (CA).

## How Does it Work?

Whenever a browser initiates a connection with an SSL secured website, it first retrieves the site's SSL Certificate to check if it's still valid. It  verifies that the CA is one that the browser trusts, and that the certificate is being used by the website for which it has been issued. If any of these checks fail, you'll get a warning indicating that the website is not secured by a valid SSL certificate. 

When as SSL certificate is installed on a web server, it enables a secure connection between the web server and the browser that connects to it. The website's URL is prefixed with "https" instead of "http" and a padlock is shown on the address bar. If the website uses an extended validation (EV) certificate, the browser may also show a green address bar.
