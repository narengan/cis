---

copyright:
  years: 2018
lastupdated: "2018-02-06"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}



# Global Load Balancing (GLB)

Load Balancing automatically reduces latency by directing visitors to the infrastructure closest to them. By keeping visitors close to your infrastructure, Load Balancing provides quick delivery of content. It operates at the DNS level, and supports any protocol, from HTTP(S) through TCP- and UDP-based services. This lets you use Load Balancing with existing services, or in conjunction with other cloud providers.

## Geo Policies

Geo Policies allow you to direct visitors to datacenters located in the same region. For instance, visitors in Europe are sent to a European datacenter, U.S. visitors are sent to a North American datacenter, and so forth.

## Health checks

Load Balancing Health Checks are performed on specific URLs through periodic HTTP/HTTPS requests, and are configured with customizable intervals, timeouts, and status codes. When an origin server is marked as unhealthy, visitors are routed away from failures using fast failover routes. 
