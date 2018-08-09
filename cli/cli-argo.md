---

copyright:
  years: 2018
lastupdated: "2018-08-08"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Argo

The following `argo` commands are available:

* Show
* Update

## Show Argo Setting

**NAME**

  `argo-setting` - Show Argo setting.

**USAGE**

  `ibmcloud cis argo DNS_DOMAIN_ID (--smart-routing | --tiered-caching) [-i, --instance INSTANCE_NAME]`

**ARGUMENTS**

   `DNS_DOMAIN_ID` is the ID of DNS domain.
   
   `--smart-routing` is one feature of Argo.
  
  `--tiered-caching` is one feature of Argo.
   
**OPTIONS**

   `-i, --instance`  Instance name. If not set, the context instance specified by `ibmcloud cis instance-set` is used.

**Output Message**

* argo feature ID
* argo feature value
* argo feature modified time


## Update Argo Setting

**NAME**

  `argo-setting-update` - Update Argo setting.

**USAGE**

  `ibmcloud cis argo-update DNS_DOMAIN_ID  (--smart-routing (on | off) | --tiered-caching (on | off)) [-i, --instance INSTANCE_NAME]`

**ARGUMENTS**

   `DNS_DOMAIN_ID` is the ID of DNS domain.
   
   `--smart-routing` is one feature of Argo.
  
   `--tiered-caching` is one feature of Argo.

**OPTIONS**
   
   `-i, --instance`  Instance name. If not set, the context instance specified by `ibmcloud cis instance-set` is used.

**Output Message**

* argo feature id
* argo feature value
* argo feature modified time
