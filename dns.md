---

copyright:
  years: 2018
lastupdated: "2018-02-26"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}

# Domain Name System (DNS) Concepts

This document contains some concepts and definitions related to the internet's domain name system (DNS) and how it affects your IBM CIS deployment

## DNS.

The Domain Name System (DNS) underpins the web we use every day. It works transparently in the background, converting human-readable website names into computer-readable, numerical IP addresses that follow the [internet's RFC 1918 guidelines for IPv4 and RFC 4193 for IPv6](https://en.wikipedia.org/wiki/Private_network). In short, DNS servers match domain names, such as 'ibm.com', to their associated IP addresses, which most people do not need to know.

The DNS system looks up this IP address and host name information on a network of linked DNS servers across the internet, similarly to how people might look for someplace using a phone book or a map.

## Secure DNS

**DNSSec** is a technology to digitally 'sign' DNS data so you can be assured it is valid. To eliminate vulnerability from the internet, DNSSec must be deployed at each step in the lookup, from root zone to final domain name (for example, www.icann.org).

![Secure DNS](images/dns/secure-dns.png)

## Name Servers
A **name server** implements services that provide responses to queries against a directory service. It translates meaningful, text-based web or host identifiers into IP addresses.

**Name server delegation** takes place when a name server for a domain receives a request for a subdomain's records and responds with the name server's reference to the delegate server. This capability allows you to decentralize the management of a large domain (such as `ibm.com`).

A **custom domain name server** allows you to utilize the DNS provider's servers with the customized reference name of your own domain. For example, you can define your name server to be `ns1.cloud.ibm.com` instead of `ns1.acme.com`.
