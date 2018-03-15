---
copyright:
  years: 2018
lastupdated: "2018-03-14"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Known Limitations

 * Our recommendation is to use Chrome.

 * In Firefox and Safari, the *uploaded*, *modified*, and *expires* dates for a certificate cannot be displayed.

 * Editing the URL match for a page rule causes that rule to be placed at the lowest priority.
 
 * Without a configured domain, you can navigate to **Reliability > Global Load Balancers** to create your load balancer pools and health checks. However, if you select **Create load balancer**, configure the load balancer, and click **Provision 1 Resource**, the request will be rejected because a domain is required. This functional limitation helps the user understand the purpose of pools and monitors in the load balancer creation flow.

 * Our system will not gather your domain records at this time.
 
* The Early Access program is limited to one instance per account. Once you create a resource instance and add a domain to it, you will not be allowed to add new resource instances for CIS. This restriction is enforced even if you delete a trial domain and attempt to add a domain again to the same resource instance. You will encounter an error if you attempt to do so.

* We support only subdomain delegation via NS records from another provider at this time. CNAME delegation is not supported.
