---

---

# CIS Command Line Interface
The following families of commands are available from the command line interface (CLI) in CIS. At these links, you'll find the full set of commands within each set, including `Create`, `Delete`, `Update`, and so forth.
  
    * [Resource Instance](cli/cli-resource-instance.html)
    * [Domain](cli/cli-domain.html)
    * [DNS Record](cli/cli-dns-record.html)
    * [GLB](cli/cli-glb.html)
    * [Cache](cli/cli-cache.html)
    * [SSL](cli/cli-ssl.html)
    * [WAF](cli/cli-waf.html)
    * [Pagerule](cli/cli-pagerule.html)
    * [Metrics](cli/cli-metrics.html)
    * [Overview](cli/cli-overview.html)


## Template

The CIS CLI documentation is shown in modified `man` page format. You can use the `man` page format, shown below, as your example if you need to create additional CLI documentation. Or you can use any of the existing CLI command documentation as an example.

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
  overview - show the overview information for an instance. 

#### USAGE
  bx cis overview [-i, --instance INSTANCE_ID] 

#### OPTIONS
 **-i, --instance INSTANCE_ID**  (Optional) Set the instance ID. If not set, will use the instance specified by the "bx cis instance-set" command.

**Output messages**:

    * service mode:
    * service details:

            domain:
            id:
            plan:

    * security:

             waf:
             tls mode:
            certificates:

    * pagerules:

              active rules:
              browser expiration:
              caching level:

    * reliability:

              dns records:
              dns security:
              active load balancer:
