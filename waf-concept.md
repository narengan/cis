---
copyright:
  years: 2018
lastupdated: "2018-03-15"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# What is a Web Application Firewall (WAF)?
A WAF or Web Application Firewall helps protect web applications by filtering and monitoring HTTP traffic between a web application and the Internet. It typically protects web applications from attacks such as cross-site forgery, cross-site-scripting (XSS), file inclusion, and SQL injection, among others. A WAF is a protocol layer 7 defense (in the [OSI model ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://en.wikipedia.org/wiki/OSI_model)), and is not designed to defend against all types of attacks. This attack mitigation method is usually part of a suite of tools, which together create a holistic defense against a range of attack vectors.

Deploying a WAF in front of a web application places a shield between the web application and the internet. While a proxy server protects a client machine’s identity by using an intermediary, a WAF is a type of reverse-proxy that protects the server from exposure by having clients pass through the WAF before reaching the server.

A WAF operates through a set of rules often called policies. These policies aim to protect against vulnerabilities in the application by filtering out malicious traffic. The value of a WAF comes from the speed and ease with which policy modification can be implemented, allowing for a faster response to varying attack vectors. During a [DDoS attack ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://en.wikipedia.org/wiki/Denial-of-service_attack), rate limiting can be quickly implemented by modifying WAF policies.
