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

# Caching
Caching stores static web content closest to the visitor, thus significantly enhancing the performance of the website.  A globally distributed delivery environment enables web content owners to provide a seamless experience.  

## Origin and Edge Servers
An **origin** server is a computer running one or more programs that are designed to listen for and process incoming Internet requests. An origin server can take on all the responsibility of serving up the content for an Internet property such as a website.  

Static content is stored on an **edge** server that is hosted by a caching service provider.  Caching uses a variety of technologies to optimize the website experience such as Automatic static content caching, quick cache purge, and edge cache expire TTL.  

## Caching Options
Caching options include: 
- **Shared certificate**: Offers an SSL Certificate to users that is provided by the vendor. 
- **Page Rules**: Define how traffic from visitors to the website is handled. Web sites can be set up to exercise fine-grained control over how visitors interact with the site on a page-by-page basis.
- **SSL**: Supports users who would like to use latest web encryption technologies (TLS 1.2). 
- **Cache Purge**: Allows you to purge the cache content to allow for instant static content update. 
- **TTL configuration**:  Defines the length of time an edge server will cache a resource before returning to the origin server for a fresh copy.
