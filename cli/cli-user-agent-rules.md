---

copyright:
  years: 2018
lastupdated: "2018-08-08"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# User Agent Rules

The following `useragent` commands are available:

* Create
* Update
* List
* Detail
* Delete

## Create User Agent Rule

**NAME**

  `useragent-rule-create` - Create a new user-agent blocking rule for a given zone under a service instance.

**USAGE**

   `ibmcloud cis useragent-rule-create DNS_DOMAIN_ID  (-s, --json-str JSON_STR | -j, --json-file JSON_FILE) [-i, --instance INSTANCE_NAME] [-o, --output OUTPUT_FILE]`

**ARGUMENTS**

   `DNS_DOMAIN_ID`  is the ID of DNS domain.

**OPTIONS**

   `-s, --json-str`  The JSON data describing a user-agent blocking rule.

The required fields in JSON data are `mode`, `configuration`.

 * `mode`: The type of action to perform. Valid values: `block`, `challenge`, `js_challenge`.
 * `configuration`: Target/Value pair to use for this rule. The value is the exact UserAgent to match.
    * `target`: The value for the selected target. Valid value is `ua`.
     * `value`: The exact UserAgent string to match with this rule.

The optional fields are `paused`, `description`.

  * `paused`: Whether this user-agent rule is currently disabled.
  * `description`: Some useful information about this rule to help identify the purpose of it.


**Sample JSON data**

```
                   {
                       "mode": "block",
                       "description": "This rule is added because of event X that occurred on date xyz",
                       "configuration": {
                           "target": "ua",
                           "value": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_5) AppleWebKit/603.2.4 (KHTML, like Gecko) Version/10.1.1 Safari/603.2.4"
                       }
                   }
```   
   
   `-j, --json-file`  A file contains input JSON data.
   
   `-i, --instance`   Instance name. If not set, the context instance specified by `ibmcloud cis instance-set` is used.
   
   `-o, --output`     Output the result in JSON format to a file. If not set, outputs the result to terminal.


**Output Table Columns**

 * ID
 * paused
 * mode
 * description
 * configuration
 * target
 * value 


## Update User Agent rule

**NAME**

   `useragent-rule-update` - Update an existing user-agent blocking rule for a given zone under a given service instance.

**USAGE**

   `ibmcloud cis useragent-rule-update DNS_DOMAIN_ID  UA_RULE_ID  (-s, --json-str JSON_STR | -j, --json-file JSON_FILE) [-i, --instance INSTANCE_NAME] [-o, --output OUTPUT_FILE]`

**ARGUMENTS**

   `DNS_DOMAIN_ID`  is the ID of DNS domain.
   
   `UA_RULE_ID`  is the ID of user-agent rule.

**OPTIONS**

   `-s, --json-str`  The JSON data describing a firewall access rule.

   `-s, --json-str`  The JSON data describing a user-agent blocking rule.

The required fields in JSON data are mode, configuration.

   * `mode`: The type of action to perform. Valid values: `block`, `challenge`, `js_challenge`.
      * `configuration`: Target/Value pair to use for this rule. The value is the exact UserAgent to match.
        * `target`: The value for the selected target. Valid value is: `ua`.
        * `value`: The exact UserAgent string to match with this rule.

The optional fields are `paused`, `description`,
        * `paused`: Whether this user-agent rule is currently disabled.
        * `description`: Some useful information about this rule to help identify the purpose of it.


** Sample JSON data:**

```
                   {
                       "mode": "block",
                       "description": "This rule is added because of event X that occurred on date xyz",
                       "configuration": {
                           "target": "ua",
                           "value": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_5) AppleWebKit/603.2.4 (KHTML, like Gecko) Version/10.1.1 Safari/603.2.4"
                       }
                   }
```

   `-j, --json-file`  A file contains input JSON data.
   
   `-i, --instance`   Instance name. If not set, the context instance specified by `ibmcloud cis instance-set` is used.
   
   `-o, --output`     Output the result in JSON format to a file. If not set, outputs the result to terminal.



**Output Table Columns**

 * ID
 * paused
 * mode
 * description
 * configuration
 * target
 *  value 





## List User Agent rules

**NAME**

   `useragent-rules` - List all user-agent blocking rules.

**USAGE**

   `ibmcloud cis useragent-rules  DNS_DOMAIN_ID [-p, --page NUM] [-n, --per_page NUM ] [-i, --instance INSTANCE_NAME] [-o, --output OUTPUT_FILE]`

**ARGUMENTS**

   `DNS_DOMAIN_ID`  is the ID of DNS domain.

**OPTIONS**

  `-p, --page`      Page number of paginated results.
  
  `-n, --per_page`  Maximum number of user-agent rules per page.
  
  `-i, --instance`  Instance name. If not set, the context instance specified by `ibmcloud cis instance-set` is used.
  
  `-o, --output`    Output the result in JSON format to a file. If not set, outputs the result to terminal.

**Output Table Columns**

 * ID
 * paused
 * mode
 * configuration.target
 * configuration.value 



## Detail User Agent rule

**NAME**

   `useragent-rule` - Get the details of a user-agent blocking rule for a given zone under a given service instance.

**USAGE**
   
   `ibmcloud cis useragent-rule DNS_DOMAIN_ID UA_RULE_ID  [-i, --instance INSTANCE_NAME] [-o, --output OUTPUT_FILE]`

**ARGUMENTS**

   `DNS_DOMAIN_ID`  is the ID of DNS domain.
   
   `UA_RULE_ID`  is the ID of user-agent rule.

**OPTIONS**
   
   `-i, --instance`  Instance name. If not set, the context instance specified by `ibmcloud cis instance-set` is used.
   
   `-o, --output`   Output the result in JSON format to a file. If not set, outputs the result to terminal.



**Output Table Columns**

 * ID
 * paused
 * mode
 * description
 * configuration
 * target
 * value 

## Delete User Agent rule

**NAME**

   `useragent-rule-delete` - Delete a user-agent rule by ID.

**USAGE**

   `ibmcloud cis useragent-rule-delete DNS_DOMAIN_ID UA_RULE_ID  [-i, --instance INSTANCE_NAME]` 

**ARGUMENTS**

   `DNS_DOMAIN_ID`  is the ID of DNS domain.
   
   `UA_RULE_ID`  is the ID of user-agent rule.

**OPTIONS**

   `-i, --instance`  Instance name. If not set, the context instance specified by `ibmcloud cis instance-set` is used.


