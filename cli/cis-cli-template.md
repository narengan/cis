---

---

# CIS Command Line Interface
The following commands are available from the command line interface (CLI) in CIS:
  
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


Use the overview command, shown below, as your template to create CLI documentation in `man` page format.

## Overview

### NAME
  overview - show the overview information for an instance. 

### USAGE
  bx cis overview [-i, --instance INSTANCE_ID] 

### OPTIONS
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
