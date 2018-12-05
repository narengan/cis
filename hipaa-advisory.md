---
copyright:
  years: 1994, 2017
lastupdated: "2018-10-10"
---
{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# HIPAA Advisory

## Use of Caching (CDN) for regulated data (for example, PHI, ITAR) is **prohibited**. All regulated data flows that use CIS must be set to **not cache**. 

There are multiple ways to disable content cacheing by the CIS CDN. 
- The origin server can set the **no-cache** in **Cache-Control** header for the regulated content
- Use the CIS Page Rules to disable caching for any content on a specified path even if the origin does not send a **no-cache** **Cache-Control** header. 
