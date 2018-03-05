---
copyright:
  years: 2018
lastupdated: "2018-02-27"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Managing your IBM CIS for optimal Security

The Cloud Internet Services (CIS) security settings include safe defaults designed to avoid false positives and negative influence on your traffic. However, these safe default settings do not provide the best security posture for every customer. Take the following steps to be sure that your CIS account is configured in a safe and secure way:

**Recommendations and best practices:**

* Secure origin IP addresses by proxying and increasing obfuscation
* Configure your Security Level selectively
* Activate your Web Application Firewall (WAF) safely

## Best practice 1: Secure Your Origin IP Addresses

When a subdomain is proxied using IBM CIS, all traffic is protected because we actively respond with IP addresses specific to IBM CIS (for example, all of your clients connect to CIS proxies first, and your origin IP addresses are obscured).

### Use CIS proxies for all DNS Records for HTTP(S) traffic from your origin

To improve the security of your origin IP address, all HTTP(S) traffic should be proxied.

**See the difference yourself - Query a non-proxied and a proxied record:**

```
$ dig greycloud.theburritobot.com +short
1.2.3.4 (The origin IP address)

$ dig orangecloud.theburritobot.com +short
104.16.22.6 , 104.16.23.6 (CIS IP addresses)
```

### Obscure non-proxied origin records with non-standard names
Any records that cannot be proxied through IBM CIS, and that still use your origin IP, such as FTP, can be secured by creating additional obfuscation. In particular, if you require a record for your origin that cannot be proxied by IBM CIS, use a non-standard name. For example, instead of `ftp.example.com` use `[random word or-random characters].example.com.` This obfuscation makes dictionary scans of your DNS records less likely to expose your origin IP addreses.

### Use separate IP ranges for HTTP and non-HTTP traffic if possible
Some customers use separate IP ranges for HTTP and non-HTTP traffic, thereby allowing them to proxy all records pointing to their HTTP IP range, and to obscure all non-HTTP traffic with a different IP subnet.

## Best practice 2: Configure your Security Level selectively
Your **Security Level** establishes the sensitivity of our **IP Reputation Database**. IBM CIS sees over 1 billion unique IP addresses every month, from more than 4 million websites, which allows our system to quickly and automatically identify malicious actors and prevent them from reaching your web assets. To prevent negative interactions or false positives, configure your **Security Level** by domain to heighten security where necessary, and to decrease it where appropriate.

### Increase the Security Level for Sensitive Areas to 'High'
You can increase this setting by adding a **Page Rule** for administration pages or login pages, to reduce brute-force attempts:

1. Select the domain you'd like to modify.
2. Create a **Page Rule** with the URL pattern of your API (for example, `www.example.com/wp-login`). 
3. Identify the **Securty Level** setting.
4. Mark the setting as **High**.
5. Select **Save and Deploy**.

### Decrease the Security Level for non-sensitive paths or APIs to reduce false positives
This setting can be decreased for general pages and API traffic: 

1. Select domain you'd like to modify. 
2. Create a **Page Rule** with the URL pattern of your API (for example, `www.example.com/api/*`).
3. Identify the **Security Level** setting.
4. Turn Security Level to **Low**, **O** , or **Essentially O**.
5. Select **Save and Deploy**.

### What do Security Level settings mean?
Our Security Level settings are aligned with threat scores that certain IP addresses acquire from malicious behavior on our network. A threat score above 10 is considered high.

* **HIGH** -- Threat scores greater than 0 will be challenged.
* **MEDIUM** -- Treat scores greater than 14 will be challenged.
* **LOW** -- Threat scores greater than 24 will be challenged.
* **ESSENTIALLY OFF** -- Threat scores greater than 49 will be challenged.
* **OFF** - Enterprise customers can remove this security feature entirely.

## Best practice 3: Activate your Web Application Firewall (WAF) safely
Your WAF is available in the **Security** section. We will walk through these settings in reverse order to ensure that your WAF is configured as safely as possible before turning it on for your entire domain. These initial settings can reduce false positives by populating the Traffic Application with WAF events for further tuning. WAF is updated automatically to handle new vulnerabilities as they are identified.

WAF protects against the following attacks:
* SQL injection attack
* Cross-site scripting
* Cross-site forgery

WAF also contains the **CIS Rule Set**, which includes rules to stop attacks most commonly seen on our network, and the **OWASP Top 10** vulnerabilities. 

WAF also will perform a browser integrity check. The browser integrity check looks for HTTP headers that are commonly abused by spammers. It denies traffic with those headers access to your page. It also blocks visitors that do not have user agent or who add a non-standard user-agent (this tactic is commonly used by abuse bots, crawlers, or APIs).

## Best practice 4: Configure your TLS settings
CIS provides some options for encrypting your traffic. As a reverse proxy we close TLS conections at our datacenters and open a new TLS connection to your origin server(s).

There are four modes of operation for TLS:
* **Off** -- TLS is disabled in this mode, this is not recommended.
* **Client-to-edge** -- Encrypts traffic from CIS to your clients, but not from CIS to your origin server(s).
* **End-to-end flexible** -- Encrypts all traffic, however, a self-signed certificate can be used to secure traffic between CIS and your origin server(s).
* **End-to-end CA signed** -- Encrypts all traffic, however, a CA signed certificate must be used.

CIS also allows use of custom certificates or you can use a wildcard certificate provisioned for you by CIS.

### Upload a custom certificate
You can upload your custom certificate by clicking **Add Certificate** button and entering your certificate, private key, and bundle method. If you upload your own certificate, you gain immediate compatibility with encrypted traffic, and you maintain control over your certificate (e.g., Extended Validation (EV) certificate). Remember that you will be responsible for managing your certificate.

### Utilize a provisioned certificate
CIS has partnered with several Certificate Authorities (CAs) to provide domain wildcard certificates for our customers. Manual verification could be required for setting up these certificates your support team can hep you perform these additional steps.
