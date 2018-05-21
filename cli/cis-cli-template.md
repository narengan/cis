---

copyright:
  years: 2018
lastupdated: "2018-05-08"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# CIS Command Line Interface
The following families of commands are available from the command line interface (CLI) in CIS. At these links, you'll find the full set of commands within each set, including `Create`, `Delete`, `Update`, and so forth.
  
  * [Resource Instance](cli/cli-resource-instance.html)
  * [Domain](cli/cli-domain.html)
  * [DNS Record](cli/cli-dns-record.html)
  * [GLB](cli/cli-glb.html)
  * [Cache](cli/cli-cache.html)
  * [TLS](cli/cli-tls.html)
  * [WAF](cli/cli-waf.html)
  * [Pagerule](cli/cli-pagerule.html)
  * [Metrics](cli/cli-metrics.html)
  * [Overview](#overview)


## Template

The CIS CLI documentation is shown in modified `man` page format. You can use the `man` page format, shown below, as your example if you need to create additional CLI documentation. Or you can use any of the other existing CLI command documentation as an example.

```
man(1)                                                                  man(1)

NAME
      man - format and display the on-line manual pages

SYNOPSIS
      man  [-acdfFhkKtwW]  [--path]  [-m system] [-p string] [-C config_file]
      [-M pathlist] [-P pager] [-B browser] [-H htmlpager] [-S  section_list]
      [section] name ...

DESCRIPTION
      man formats and displays the on-line manual pages.  If you specify sec-
      tion, man only looks in that section of the manual.  name  is  normally
      the  name of the manual page, which is typically the name of a command,
      function, or file.  However, if name contains  a  slash  (/)  then  man
      interprets  it  as a file specification, so that you can do man ./foo.5
      or even man /cd/foo/bar.1.gz.

      See below for a description of where man  looks  for  the  manual  page
      files.

OPTIONS
      -C  config_file
```

## Example

The `overview` command also is one of the CLI commands available to you. It just happens to make a good example as well, so we included it here.


### Overview

#### NAME
  overview - Show the overview information for an instance. 

#### USAGE
  ibmcloud cis overview [-i, --instance INSTANCE_NAME] 

#### OPTIONS
 **-i, --instance INSTANCE_NAME**  (Optional) Instance name. If not set, the context instance specified by 'ibmcloud cis   instance-set' will be used.

**Output messages**:

  * Service Mode
    * Service Details
    *  Domain Name
       * Status
       * ID
       * Service Plan

  * Security
    * Web Application Firewall
    * TLS Mode
    * Dedicated Certificates
    * Custom Certificates

  * Performance 
    * Page Rules
    * Browser Expiration
    * Caching Level

  * Reliability:
    * DNS Records
    * DNS Security
    * Load Balancers
              
**Service Mode** is displayed only when the domain is paused or in defense mode.
