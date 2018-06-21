---
copyright:
  years: 2018
lastupdated: "2018-06-21"
---
# How to use CIS Security Events

Reviewing Security Events gives you insight into your traffic and any potential malicious activity against your website. It also helps you to optimize your WAF configuration.

## CIS Security Events Table
The Security Events Table shows you detailed information about requests blocked by the WAF. Each entry shows one blocked request. 
* **Triggered rule** indicates which rule blocked the request. Any of the following actions is available:
  * **Block** : A hard block
  * **Challenge**: A CAPTCHA page that humans can bypass 
  * **Simulate**: A request that is allowed through normally, but is logged 
* **IP Address** shows source IP of the web request.
* **Location** shows the country associated with the source of the web request.
* **Host** shows the hostname of the server that has been accessed.
* **Date** shows the day the event occurred.
 

## CIS Security Events Details
Click the arrow on an event to expand the details for the security event.
The left section shows the event details, along with the Ray-Id. The right section shows request details such as Header, URI, Protocol, the type of firewall that blocked the request, and User Agent.

If the triggered rule for an event has an ID of `981176`, this means the block was caused by OWASP. When any rules in the OWASP ruleset is matched, the “threat score” of the request increases. The Sensitivity setting (`Low` or `High`) for your zone translates to a threshold. If the cumulative score of all the matched OWASP rules exceeds that threshold, `981176` is triggered and blocks the request.

This means that all requests blocked by OWASP show on your Security Events as blocked by `981176`. Expand the event details and view the Event Triggers section to see the individual OWASP rules that were matched to increase the request’s threat score.

## What do I do if valid traffic is blocked?
Expand each event to see event details. The **Event Triggers** section displays all the individual OWASP rules that were matched for OWASP rule-triggered events. Decide whether this traffic looks normal for your website, or if it got appropriately blocked. If you decide that this block is a false positive, you can go back to your WAF configuration and disable individual OWASP rules until this request no longer exceeds your sensitivity threshold.
