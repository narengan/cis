---

---

# CLI Overview
Use the following template to create CLI documentation in `man` page format.

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
