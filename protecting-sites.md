---
copyright:
  years: 2018
lastupdated: "2018-08-09"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Protecting your site

IBM Cloud Internet Services offers several tools for controlling your traffic so that you protect your domains, URLs, and directories against volumes of traffic, certain groups of requesters, and particular requesting IPs. This section details the tools available.


## IP Rules
The IP Rules allow you to control access for specific IP addresses, IP ranges, specific countries, specific ASNs, and certain CIDR blocks. Available actions on incoming requests are:
  * Whitelist 
  * Block 
  * Challenge (Captcha) 
  * JavaScript Challenge (IUAM challenge)

For example, if you notice that a particular IP is causing malicious requests, you can block that user by IP address.

## Domain Lockdown
Domain Lockdown allows you whitelist specific IP addresses and IP ranges such that all other IPs are blacklisted. Domain Lockdown supports:

  * Specific sub-domains. For example, you can allow IP `1.2.3.4` access to the domain `foo.example.com` and allow IP `5.6.7.8` access to domain `bar.example.com`, without necessarily allowing the reverse.
  * Specific URLs. For example, you can allow IP `1.2.3.4` access to directory `example.com/foo/*` and allow IP `5.6.7.8`  access to directory `example.com/bar/*`, but not necessarily allow the reverse.
This capability is useful when you need more granularity in your access rules because, with the IP Rules, you can either apply the block to all sub-domains of the current domain, or all domains on your account, and you cannot specify URIs.

 
## User-Agent Blocking Rules
User-Agent Blocking rules allow you to take action on any User-Agent string you select. This capability works like Domain Lockdown as described previously, except the block examines the incoming User-Agent string rather than the IP. You can choose how to handle a matching request with the same list of actions as you have estabilshed in the IP Rules (Block, Challenge, and JS Challenge). Note that User-Agent blocking applies to your entire zone. You cannot specify sub-domains in the same manner you can Domain Lockdowns.

This tool is useful for blocking any User-Agent strings that you deem suspicious.

 
