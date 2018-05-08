---
copyright:
  years: 2018
lastupdated: "2018-05-08"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# OWASP Ruleset for WAF

The OWASP Ruleset contains generic attack detection rules. The OWASP rules protect against many common attack categories, including SQL Injection, Cross Site Scripting, and Locale File Inclusion, among others. IBM CIS provides but does not curate these rules. OWASP is an industry standard and provides a good security baseline. See the following links for more information:
[OWASP on Github](https://github.com/SpiderLabs/owasp-modsecurity-crs)
[OWASP.org](https://www.owasp.org/index.php/Category:OWASP_ModSecurity_Core_Rule_Set_Project)

## Managing OWASP

Unlike the [CIS ruleset](waf-cis-ruleset.html), OWASP allows you to set Sensitivity. 
A request may trigger a set of OWASP rules that have a high to low severity score associated with them. The final score is calculated based on all the rules triggered. After calculating the final score, CIS compares it to the sensitivity threshhold selected in the begining, and then either blocks or allows the request.

|Sensitivity	score| Trigger threshold|
|------|---------------|
|Low   |	60 and higher|
|Medium|	40 and higher|
|High	 |  25 and higher|

We suggest that you set OWASP to low. If you set it to high, check the logs on CIS, and fine tune the OWASP ruleset to work for your application.

Keep in mind that OWASP rules can only be toggled on or off, unlike CIS Rulesets rules which can be set to "Disable", "Simulate", "Challenge", or "Block".

## How to deal with False Positives?

False positives occur when something evaluates as true or positive when it's actually a negative. In the context of our WAF, this means a request gets blocked because it was mistakenly evaluated as malicious.

To deal with false positives and make sure to avoid them in the future, you need to know how to spot them and correct them. Review the logs of blocked requests, and then evaluate whether these requests were reasonably blocked within the context of the expected and normal traffic of your website.
