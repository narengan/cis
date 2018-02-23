---
copyright:
  years: 2018
lastupdated: "2018-02-22"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Managing your CIS deployment for optimal performance
IBM Cloud Internet Services can provide the fastest experience for your application by optimizing your images, and storing content as near as possible to your end-users.

## Image compression with Polish
Polish can use lossy or lossless compression to achieve  compression rates of up to 30-40%. For the majority of web applications, enable Polish in the lossless, ‘Basic’ mode.

## Reduce HTML and CSS load times with Minification
Enable Minification to remove comments and formatting meant for humans, and improve your load times. Minification can be safely enabled for HTML and CSS, but make sure that all line endings in Javascript are denoted with a semicolon before enabling.

## Mirage and Rocket Loader tools
CIS can accellerate content using client-side tools such as Mirage and Rocket Loader. Test these tools carefully before enabling them for production environments.  They are enabled for specific pages or subdomains using [Page Rules](page-rules.html)
