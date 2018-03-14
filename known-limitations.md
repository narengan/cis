---
copyright:
  years: 2018
lastupdated: "2018-03-12"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Known Limitations

 * Our recommendation is to use Chrome.

 * In Firefox and Safari, the *uploaded*, *modified*, and *expires* dates for a certificate cannot be displayed.

 * Editing the URL match for a page rule causes that rule to be placed at the lowest priority.
 
 * Without a configured domain one can still navigate to Reliability > Global Load Balancers and create load balancer pools and health checks. However, upon clicking 'Create load balancer', configuring the load balancer, and clicking 'Provision 1 Resource', the request will be rejected since a domain is needed. This is done so the user can understand the purpose of the pools and monitors in the load balancer creation flow.
