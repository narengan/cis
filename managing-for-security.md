---
copyright:
  years: 2018
lastupdated: "2018-02-22"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Managing your IBM CIS for optimal Security

By default, CIS’s security settings are set to safe defaults that aim to avoid false positives and negative influences on your traffic. However, this is not necessarily the best security posture for every Enterprise customer. The following steps will ensure CIS is configured in a secure and safe manner.

**Recommendations:**

* Secure origin IP addresses by proxying and increasing obfuscation 
* Configure your Security Level selectively
* Activate your Web Application Firewall safely

## Secure Origin IP Addresses

### Orange-Cloud all DNS Records for HTTP(S) traffic from your origin

When a subdomain is orange-clouded within our DNS application, CIS will actively proxy that traffic by responding with CIS IP addresses. These addresses cause the client to connect to CIS first and obscure the origin IP address. To improve the security of your origin IP address, all HTTP(s) traffic should be orange-clouded.

See the difference yourself - Query a Grey-Clouded and Orange-Clouded record:

```
$ dig greycloud.theburritobot.com @woz.ns.cloud are.com +short
1.2.3.4 (The origin IP address)

$ dig orangecloud.theburritobot.com @woz.ns.cloud are.com +short
104.16.22.6 , 104.16.23.6 (CIS IP addresses)
```

### Obscure Grey-Clouded origin records with non-standard names
Any records that cannot be proxied through CIS but still utilize your origin IP — such as FTP — can still be secured with additional obfuscation. If you require a record to your origin that cannot be proxied by CIS, use a non-standard name for this record. For example, instead of `ftp.example.com` use `[random word or-random characters].example.com` — this will make dictionary scans of your DNS less likely to expose your origin IP addreses.

### Separate IP ranges for HTTP and non-HTTP traffic if possible
Some customers will use separate IP ranges for HTTP and non-HTTP traffic, allowing them to orange-cloud all records pointing to their HTTP IP range and obscuring all non-HTTP traffic with a different IP subnet.

## Configure your Security Level selectively
Your Security Level sets the sensitivity to our IP Reputation Database. CIS sees over 1 billion unique IPs every month from more than 4 million websites. This allows CIS to quickly and automatically determine malicious actors and prevent them from reaching your webassets. You can easily configure your Security Level by URI to heighten security where necessary and decrease it where appropriate to prevent any negative interactions or false positives.

### Increase the Security Level for Sensitive Areas to High
This setting can be increased for administration pages or login pages to reduce brute-force attempts by adding a Page Rule.

1. Ensure the proper domain is selected in the upper left corner.
2. Create a Page Rule with the URL pattern of your API (for example, `www.example.com/wp-login`). 
3. Select the **Securty Level** setting.
4. Mark the setting as **High**.
5. Press **Save and Deploy**.

### Decrease the Security Level for non-sensitive paths or APIs to reduce false positives
This setting can be decreased for general pages and API traffic: 

1. Ensure the proper domain is selected in the upper left corner. 
2. Create a Page Rule with the URL pattern of your API (for example, `www.example.com/api/*`).
3. Select the **Security Level** setting.
4. Turn Security Level to **Low**, **O** , or **Essentially O**.
5. Press **Save and Deploy**.

### Alternatively, globally utilize the Medium Security Level setting
The Medium security setting has a very low false positive rate ( 1 in 50 million) and is recommended as a starting point for all customers. The global setting is available in the Firewall Application.

1. Ensure the proper domain is selected in the upper left corner.
2. Select the **FireWall** application.
3. Click the **Options** within the **Security Level** module. 
4. Select **Medium**.

### What do Security Level settings mean?
Security Level settings are aligned with threat scores that IP addresses acquire with malicious behavior on our network. A threat score above 10 is considered high and 50 is really bad.

* **HIGH** -- Threat scores greater than 0 will be challenged.
* **MEDIUM** -- Treat scores greater than 14 will be challenged.
* **LOW** -- Threat scores greater than 24 will be challenged.
* **ESSENTIALLY OFF** -- Threat scores greater than 49 will be challenged.
* **OFF** - Enterprise customers can remove this security feature entirely.

## Activate your Web Application Firewall (WAF) safely
Your WAF is available in the Firewall Application in the Web Application
Firewell section. We will walk through these settings in reverse order to ensure
that the WAF is configured as safely as possible before turning it on for
your entire domain. The goal of these initial settings is to reduce false positives and to populate the Traffic Application with WAF events for further tuning.

### First, set the OWASP ModSecurity sensitivity to High with an action of Simulate
The OWASP package is based on an anomaly score to help reduce false positives while still catching attacks. The goal of these settings is to tune your OWASP
settings by logging any false positives.

A Simulate action simply logs an event within our Traffic application.

### Second, activate CIS Specials and any platform-specific groups you use
The CIS Rulesets are focused on novel, zero-day and application specific exploits. They are more specific and do not lend themselves to false positives. 

Selecting CIS Specials and any application-specific groups allow you to take an adequate security posture with very few false positives. For example, if you use a Drupal application, that group should be activated while Joomla and Magento groups are turned OFF.

| Group  | Description | Mode |
| ------------- | ------------- | ------------- |
| CIS Specials  | CIS Specials contains a number of rules that have been created to deal with specific attack types.  | ON |
| CIS Drupal  | This ruleset should only be enabled if the Drupal CMS is used for this domain. It contains additional rules that compliment the technology-specific protections provided by similar rules in the OWASP ruleset. | ON |
| CIS Flash  | This ruleset should only be enabled if Adobe Flash content is used for this domain. It contains additional rules that compliment the technology-specific protections provided by similar rules in the OWASP ruleset. | OFF |
| CIS Joomla  | This ruleset should only be enabled if the Joomla CMS is used for this domain. It contains additional rules that compliment the technology-specific protections provided by similar rules in the OWASP ruleset. | OFF |
| CIS Magento  | This ruleset should only be enabled if the Magento CMS is used for this domain. It contains additional rules that compliment the technology-specific protections provided by similar rules in the OWASP ruleset. | OFF |

### Finally, turn your Web Application Firewall On with the Global Setting
Now that your Package-level settings are configured safely, you can now turn on the global, domain-wide WAF. Specific Paths, such as API endpoints, can turn the WAF off completely using a Page Rule. This can ensure you are protected while not interfering with legimate requests.