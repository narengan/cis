---

copyright:
  years: 2018
lastupdated: "2018-05-08"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Pagerule

The following `pagerule` commmands are available:

* Create
* Update
* Delete
* Show

## Create Page Rule

### NAME
page-rule-create - Create a page rule under a given DNS domain.

### USAGE
bx cis page-rule-create <DNS_DOMAIN_ID> [-i, --instance INSTANCE_NAME] [-s, --json-str JSON_STR] [-j, --json-file JSON_FILE] [-o, --output OUTPUT_FILE]

### OPTIONS
   **-i, --instance INSTANCE_NAME**  (Optional) Instance name. If not set, will use the instance specified by the "bx cis instance-set" command.
   **-s, --json-str JSON_STR**  (Optional) The JSON data used to create a page rule. The required fields in JSON data are "targets" and "actions", and optional fields are "priority" and "status" fields, where, 

    * **targets**:  the target URL pattern to evaluate on a request. 
    * **actions**: An array of actions to perform if the targets of this rule match the request. Available actions are:

**disable_security, always_use_https, ssl, browser_cache_ttl, security_level, cache_level, edge_cache_ttl, bypass_cache_on_cookie, browser_check, server_side_exclude, always_online, email_obfuscation, automatic_https_rewrites, opportunistic_encryption, ip_geolocation, explicit_cache_control, cache_deception_armor, waf,** and **forwarding_url**.

    * **priority**: (Optional) A number that indicates the preference for a page rule over another. Default is 1.

    * **status**: (Optional) Status of the page rule. The valid values are "active" and "disabled", default is "disabled".

   **-j, --json-file JSON_FILE**  (Optional) The JSON file used to create a page rule. 
   **-o, --output OUTPUT_FILE**  (Optional) Output the result as JSON style to a file. If not set, will output the result to terminal.

### EXAMPLES

    * bx cis page-rule-create b7b847226e772bd44c5c3a1a27cad3b1 -j pagerule.json

where, pagerule.json is a file with the following example Json data. 
{
    "targets": [
        {
            "target": "url",
            "constraint": {
                "operator": "matches",
                "value": "*example.com/images/*"
            }
        }
    ],
    "actions": [
        {
            "id": "always_use_https"
        },
        {
            "id": "always_online",
            "value": "on"
        },
        {
            "id": "ssl",
            "value": "flexible"
        },
        {
            "id": "browser_cache_ttl",
            "value": 14400
        },
        {
            "id": "security_level",
            "value": "medium"
        },
        {
            "id": "cache_level",
            "value": "basic"
        },
        {
            "id": "edge_cache_ttl",
            "value": 7200
        },
        {
            "id": "bypass_cache_on_cookie",
            "value": "wp-.*|wordpress.*|comment_.*"
        }
    ]
}

    * bx cis page-rule-create b7b847226e772bd44c5c3a1a27cad3b1 -s '{"targets": [{"target":"url", "constraint": {"operator": "matches", "value":"*example.com/images/*"}}], "actions": [ {"id": "always_use_https"}, {"id": "always_online", "value": "on"}, {"id": "ssl", "value": "flexible"}, {"id": "browser_cache_ttl", "value": 14400}, {"id": "security_level", "value": "medium"}, {"id": "cache_level", "value": "basic"}, {"id": "edge_cache_ttl", "value": 7200}, {"id": "bypass_cache_on_cookie", "value": "wp-.*|wordpress.*|comment_.*"} ] }'



#### Output Message:

    * page rule id
    * target
    * priority
    * status
    * actions table (columns as below):
    * action ID
    * action value



## Update a Page Rule

### NAME:
   page-rule-update - Update a given page rule.

### USAGE:
   bx cis page-rule-update <DNS_DOMAIN_ID> <PAGE_RULE_ID> [-i, --instance INSTANCE_NAME] [-s, --json-str JSON_STR] [-j, --json-file JSON_FILE] [-o, --output OUTPUT_FILE]

### OPTIONS:
  **-i, --instance INSTANCE_NAME** (Optional) Instance name. If not set, will use the instance set by "bx cis set-instance" by default.
  **-s, --json-str JSON_STR ** (Optional) The JSON data used to create a page rule. The required fields in JSON data are "targets" and "actions", and optional fields are "priority" and "status" fields, where, 

    * **targets**:  the target URL pattern to evaluate on a request. The URL can be set to match a series of similar patterns by using wildcard "*", e.g. "*example.com/images/*" matches both HTTP/HTTPS requests under domain example.com that start with URI with /images/.
    * **actions**: An array of actions to perform if the targets of this rule match the request. Available actions are:

**disable_security, always_use_https, ssl, browser_cache_ttl, security_level, cache_level, edge_cache_ttl, bypass_cache_on_cookie, browser_check, server_side_exclude, always_online, email_obfuscation, automatic_https_rewrites, opportunistic_encryption, ip_geolocation, explicit_cache_control, cache_deception_armor, waf,** and **forwarding_url**.

    * **priority**: (Optional) A number that indicates the preference for a page rule over another. Default is 1.

    * **status**: (Optional) Status of the page rule. The valid values are "active" and "disabled", default is "disabled".

   **-j, --json-file JSON_FILE**  (Optional) The JSON file used to create a page rule.
   **-o, --output OUTPUT_FILE**  (Optional) Output the result formatted to a JSON file. If not set, will output the result to terminal.

### EXAMPLES

1.     bx cis page-rule-create b7b847226e772bd44c5c3a1a27cad3b1 -j page_rule.json

where, page_rule.json may have the following example Json data. 
{
    "targets": [
        {
            "target": "url",
            "constraint": {
                "operator": "matches",
                "value": "*example.com/images/*"
            }
        }
    ],
    "actions": [
        {
            "id": "always_use_https"
        },
        {
            "id": "always_online",
            "value": "on"
        },
        {
            "id": "ssl",
            "value": "flexible"
        },
        {
            "id": "browser_cache_ttl",
            "value": 14400
        },
        {
            "id": "security_level",
            "value": "medium"
        },
        {
            "id": "cache_level",
            "value": "basic"
        },
        {
            "id": "edge_cache_ttl",
            "value": 7200
        },
        {
            "id": "bypass_cache_on_cookie",
            "value": "wp-.*|wordpress.*|comment_.*"
        }
    ]
}

1.     bx cis page-rule-update b7b847226e772bd44c5c3a1a27cad3b1 -s '{"targets": [{"target":"url", "constraint": {"operator": "matches", "value":"*example.com/images/*"}}], "actions": [ {"id": "always_use_https"}, {"id": "always_online", "value": "on"}, {"id": "ssl", "value": "flexible"}, {"id": "browser_cache_ttl", "value": 14400}, {"id": "security_level", "value": "medium"}, {"id": "cache_level", "value": "basic"}, {"id": "edge_cache_ttl", "value": 7200}, {"id": "bypass_cache_on_cookie", "value": "wp-.*|wordpress.*|comment_.*"} ] }'



#### Output Message:

    * page rule id
    * target
    * priority
    * status
    * actions table (columns as below):
        * action ID
        * action value



## Delete a Page Rule

### NAME
   page-rule-delete - Delete a given page rule.

### USAGE
   bx cis page-rule-delete <DNS_DOMAIN_ID> <PAGE_RULE_ID> [-i, --instance INSTANCE_NAME]

### OPTIONS
**-i, --instance INSTANCE_NAME** (Optional) Instance name. If not set, will use the instance set by "bx cis instance-set" command.

#### Output Message:
    * result of deleting the page rule


## List Page Rules

### NAME
   page-rules - List page rules of a given zone.

### USAGE
   bx cis page-rules <DNS_DOMAIN_ID> [-i, --instance INSTANCE_NAME] [-o, --output OUTPUT_FILE]

### OPTIONS
   **-i, --instance INSTANCE_NAME**  (Optional) Instance name. If not set, will use the instance set by the "bx cis set-instance" command.
   **-o, --output OUTPUT_FILE**  (Optional) Output the result formatted to a JSON file. If not set, will output the result to terminal.

#### Output Table Columns:

    * page rule id
    * target
    * priority
    * status


## Show a Page Rule

### NAME:
   page-rule - Get details of a given page rule.

### USAGE:
   bx cis page-rule <DNS_DOMAIN_ID> <PAGE_RULE_ID> [-i, --instance INSTANCE_NAME] [-o, --output OUTPUT_FILE]

### OPTIONS:
   **-i, --instance INSTANCE_NAME**  (Optional) Instance name. If not set, will use the instance set by "bx cis instance-set" command.
   **-o, --output OUTPUT_FILE**  (Optional) Output the result formatted to a JSON file. If not set, will output the result to terminal.

#### Output Message:

    * page rule id
    * target
    * priority
    * status
    * actions table (columns as below):
      1. action ID
      1. action value


