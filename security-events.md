---
copyright:
  years: 2018
lastupdated: "2018-06-21"
---
# How to use the CIS Security Events

Reviewing Security Events can give you unique insight into your traffic and any potential malicious activity against your website. It can also enable you to optimize your WAF configuration

## CIS Security Events Table
The Security Events Table shows you detailed information about requests blocked by the WAF. Each entry shows one blocked request. 
 Triggered rule indicates what rule blocked the request
Action taken can be one of :
 ** "Block" : A hard block
 ** "Challenge" : A CAPTCHA page that humans can bypass, 
 ** "Simulate" : A request that is allowed through normally, but is nevertheless logged
 IP Address shows source IP of the web request
 Location shows country associated with the source of the web request
 Host shows the hostname of your server which has been accessed
 Date shows the timestamp of the event occurrence.

 

## CIS Security Events Details
Clicking on the arrow on an event expands the event details and shows details for the security event.
The left  section shows the event details, along with the Ray-Id. The right section shows request details like Header, URI, Protocol, the type of firewall that blocked the request and User Agent.
If the triggered rule for an event has id 981176, this means the block was caused by OWASP. The OWASP ruleset includes many rules, and when any of them is matched, the “threat score” of the request increases. The Sensitivity setting (Low or High) for your zone translates to a threshold. If the cumulative score of all the matched OWASP rules exceeds that threshold, 981176 is triggered and blocks the request.

In effect this means that all requests that get blocked by OWASP will show on your Security Events as blocked by 981176. If you expand the event details and see the Event Triggers section,  you will see the individual OWASP rules that were matched to increase the request’s threat score.


