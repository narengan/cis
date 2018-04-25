---
copyright:
  years: 2018
lastupdated: "2018-04-23"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# OWASP Rule Set for WAF

The OWASP Rule Set is generic attack detection rules. The OWASP rules protect against many common attack categories, including SQL Injection, Cross Site Scripting, Locale File Inclusion, etc. These rules are provided and not curated by IBM(CIS). OWASP is an industry standard and provides a good security baseline
https://github.com/SpiderLabs/owasp-modsecurity-crs
https://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project


## Managing OWASP
Unlike the CIS rules set, OWASP allows you to set a "Sensitivity". 
When a request comes in, It may trigger a set of OWASP rules. These rules have high to low severity score associated with them. The final score is calculated base on all the rules triggered. After the final score is calculated, its compared to the sensitivity threshhold selected in the begining and then the request is either blocked or allowed

Sensitivity	Score to trigger
Low	60 and higher
Medium	40 and higher
High	25 and higher

Generally suggest setting OWASP to low. Otherwise set it to high, check the logs on CIS and fine tune the OWASP rule set to work for your application

https://support.cloudflare.com/hc/en-us/articles/360002866492-Managing-the-OWASP-rule-set-in-the-WAF - more info

OWASP rules can only be turned "On" or "Off" unlike CIS Rulesets rules can be set to "Disable", "Simulate", "Challenge", or "Block".

https://support.cloudflare.com/hc/en-us/articles/115000223771 - more info

## How to deal with False Positives?

A false positive is when something is evaluated as true/positive when it's actually a negative, i.e. the diagnosis was wrong. In the context of our WAF this means a request getting blocked because it was mistakenly evaluated as malicious.

To deal with false positives and make sure they're avoided in the future, you need to know how to spot them, and how to correct them. To spot them, you would need to review the logs of requests that got blocked and then evaluate whether it makes sense that these requests were blocked within the context of the expected and normal traffic of your website.

https://support.cloudflare.com/hc/en-us/articles/115000223771 - more info




