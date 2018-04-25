copyright:
  years: 2018
lastupdated: "2018-04-25"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}



# CIS Rule Set for WAF

<< Clicking on Rule Details will reveal the rulesets that this package consists of. You will find 10 rulesets called Drupal, Flash, Joomla, Magento, Miscellaneous, PHP, Plone, Specials, WHMCS, and Wordpress. 

Specials contains a number of rules that we have found to be compatible with and appropriate for virtually all applications and websites on the internet. This ruleset is the core of the security that our WAF offers, with rules that target common attacks like SQLi, XSS, LFI, etc. Based on that, we recommend that you always leave Specials enabled.

Other than Specials, you should only enable the rulesets that correspond to your technology stack, i.e. if you use Wordpress but none of the other technologies then you should only enable the Specials and Wordpress rulesets. Enabling rulesets that are not relevant to your tech stack will likely cause issues.

By clicking on any of the specific Rulesets, you will be able to see further details about each of the rules that ruleset consists of.

CIS Rule set lets you perform 4 actions on each rule
1. Disable
2. Simulate: Logs the event and does not block or challenge the visitor (you can still decide to set to a block or challenge after reviewing your logs).
3. Block: Block will simply block the request entirely, with no option to bypass it for that request.
4. Challenge: Will display a challenge (CAPTCHA) page that must be completed before the request in question is allowed access.

that the names of the rules don't reveal exactly how they work - they are mostly a general summary of their function. This is on purpose: for security purposes we don't reveal the code (or other exact information) we use to filter traffic. If this knowledge were easily accessible, it would allow malicious actors to reverse engineer it and bypass our defences.>> copied from website https://support.cloudflare.com/hc/en-us/articles/115000223771 . 