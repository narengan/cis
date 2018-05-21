---

copyright:
  years: 2018
lastupdated: "2018-05-21"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Web Application Firewall (WAF)

The following `waf` commands are available:

* Show WAF setting
* Update WAF settings
* List WAF packages
* Show a WAF package
* Update WAF OWASP package
* List WAF groups
* Show a WAF group
* Update a WAF group
* List WAF rules
* Show a WAF rule
* Update a WAF rule


## Show WAF setting

### NAME
  waf-setting - Show WAF setting.

### USAGE
  ibmcloud cis waf-setting DNS_DOMAIN_ID

### ARGUMENTS:
   DNS_DOMAIN_ID is the id of DNS domain.

### OPTIONS:
   -i, --instance  Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' will be used.

#### Output Message:

   * waf setting ID
   * waf mode



## Update WAF Setting

### NAME
  waf-setting-update - Update WAF setting.

### USAGE
  ibmcloud cis waf-setting-update DNS_DOMAIN_ID WAF_MODE

### ARGUMENTS:
   DNS_DOMAIN_ID is the id of DNS domain.
   
   WAF_MODE is the mode of WAF setting. Valid values are:  waf-enable , waf-disable.

### OPTIONS:
   -i, --instance  Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' will be used.

#### Output Message:

   * waf setting ID
   * waf mode



## List WAF packages

### NAME
  waf-packages - List all WAF packages.

### USAGE
  ibmcloud cis waf-packages DNS_DOMAIN_ID

### ARGUMENTS:
   DNS_DOMAIN_ID is the id of DNS domain.

### OPTIONS:
   -i, --instance  Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' will be used.

#### Output Message:

   * package id
   * package name
   * package mode



## Show a WAF package

### NAME
  waf-package - Get detail of a package.

### USAGE
  ibmcloud cis waf-package DNS_DOMAIN_ID WAF_PACKAGE_ID

### ARGUMENTS:
   DNS_DOMAIN_ID is the id of DNS domain.
   
   WAF_PACKAGE_ID is the id of WAF package.

### OPTIONS:
   -i, --instance  Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' will be used.

#### Output Message:

   * package id
   * package name
   * package description
   * package mode



## Update WAF OWASP package

### NAME
  waf-package-set - Set config of the OWASP package.

### USAGE
  ibmcloud cis waf-package-set DNS_DOMAIN_ID OWASP_PACKAGE_ID SENSITIVITY ACTION_MODE

### ARGUMENTS:
   DNS_DOMAIN_ID is the id of DNS domain.
   
   OWASP_PACKAGE_ID is the package id of OWASP.
   
   SENSITIVITY is the sensitivity of the package. Valid values are: high, low, off.
   
   ACTION_MODE is the action that will be taken for rules under the package. Valid values are: simulate, block, challenge.

### OPTIONS:
   -i, --instance  Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' will be used.

#### Output Message:

   * package id
   * package name
   * package description
   * package detection mode
   * domain id
   * package status
   * package sensitivity
   * package action mode


## List WAF groups

### NAME
  waf-groups - List WAF groups in a given WAF package.

### USAGE
  ibmcloud cis waf-groups DNS_DOMAIN_ID WAF_PACKAGE_ID

### ARGUMENTS:
   DNS_DOMAIN_ID is the id of DNS domain.
   
   WAF_PACKAGE_ID is the id of WAF package.

### OPTIONS:
   -i, --instance  Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' will be used.

#### Output Message:

   * group id
   * group name
   * group description
   * group mode


## Show a WAF group

### NAME
  waf-group - Get detail of a WAF group.

### USAGE
  ibmcloud cis waf-group DNS_DOMAIN_ID WAF_PACKAGE_ID WAF_GROUP_ID

### ARGUMENTS:
   DNS_DOMAIN_ID is the id of DNS domain.
   
   WAF_PACKAGE_ID is the id of WAF package.
   
   WAF_GROUP_ID is the id of WAF group.
   
### OPTIONS:
   -i, --instance  Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' will be used.

#### Output Message:

   * group name
   * group id
   * group mode
   * group description
   * rules count
   * modified rules count


## Update a WAF group

### NAME
  waf-group-mode-set - Set mode of a WAF group.

### USAGE
  ibmcloud cis waf-group-mode-set DNS_DOMAIN_ID WAF_PACKAGE_ID WAF_GROUP_ID WAF_GROUP_MODE

### ARGUMENTS:
   DNS_DOMAIN_ID is the id of DNS domain.
   
   WAF_PACKAGE_ID is the id of WAF package.
   
   WAF_GROUP_ID is the id of WAF group.
   
   WAF_GROUP_MODE is the mode of WAF group. Valid values are: on, off.

### OPTIONS:
   -i, --instance  Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' will be used.

#### Output Message:

   * group id
   * group mode


## List WAF rules

### NAME
  waf-rules - List all WAF rules of a given WAF package.

### USAGE
  ibmcloud cis waf-rules DNS_DOMAIN_ID WAF_PACKAGE_ID

### ARGUMENTS:
   DNS_DOMAIN_ID is the id of DNS domain.
   
   WAF_PACKAGE_ID is the id of WAF package.

### OPTIONS:
   -i, --instance  Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' will be used.
   
   -p, --page-no Page num
   
   -n, --number-per-page  Number of rules per page. Min value is 5 and max value is 1000.

Output Message:

   * rule id
   * rule description
   * rule current mode



## Show a WAF rule

### NAME
  waf-rule - Get detail of a WAF rule.

### USAGE
  ibmcloud cis waf-rule DNS_DOMAIN_ID WAF_PACKAGE_ID WAF_RULE_ID

### ARGUMENTS:
   DNS_DOMAIN_ID is the id of DNS domain.
   
   WAF_PACKAGE_ID is the id of WAF package.
   
   WAF_RULE_ID is the id of WAF rule.

### OPTIONS:
   -i, --instance  Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' will be used.

#### Output Message:

   * rule id
   * rule description
   * rule current mode
   * rule default mode
   * rule allowed mode
   * rule priority
   * group id of the rule belonging to
   * group name of the rule belonging to


## Update a WAF rule

### NAME
  waf-rule-mode-set - Set mode of a WAF rule.

### USAGE
  ibmcloud cis waf-rule-mode-set DNS_DOMAIN_ID WAF_PACKAGE_ID WAF_RULE_ID WAF_RULE_MODE  

### ARGUMENTS:
   DNS_DOMAIN_ID is the id of DNS domain.
   
   WAF_PACKAGE_ID is the id of WAF package.
   
   WAF_RULE_ID is the id of WAF rule.
   
   WAF_RULE_MODE is the mode of WAF rule. Valid values are: on, off, default, disable, simulate, block,  challenge.

### OPTIONS:
   -i, --instance  Instance name. If not set, the context instance specified by 'ibmcloud cis instance-set' will be used.

#### Output Message:

   * rule id
   * rule current mode
