---
copyright:
  years: 2018
lastupdated: "2018-12-03"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:DomainName: data-hd-keyref="DomainName"}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:generic: data-hd-programlang="generic"}


# IAM and CIS

IBM Cloud Internet Services (CIS) leverages IAM to perform authorization and Authentication.

If you do not wish to add anyone to your CIS instance, you may disregard this page.
{:note}

Restrict access to CIS by three types, based on the navigation tree: 
* reliability - e.g DNS, GLB
* security - e.g Certificate, firewall rules and rate limiting
* performance - Page rules, caching and routing

This section walks through how to provide fine-grained access control of your instance.

## Roles

Use the following three roles to leverage IAM
* Reader - Ability to get information of instance/domain
* Writer - Ability to make changes to existing configuration
* Manager - Ability to create/delete/edit domain/configuration

## Access groups and users

A policy can be assigned to a User directly or to an Access Group.
We recommend assigning it to an access group to minimize the number of policies created and to reduce the effort of managing these policies.

## Best Practices

1. Instead of modifying a policy, delete the existing policy and then create a new one

## Scenarios
This section walks through the different examples of access policies created through CIS 

### Domain level with `config` type

#### Access to single domain with `security config` on an Access Group
##### Writer Role:

Bob has a CIS instance - cis-test-instance, and has two domains, bob.com and bob-ibm.com.
Bob wants to provide all security engineers (sec-group) in the company access to Writer role only the *security configuration* of *bob.com*.

These steps show how to create an IAM policy to make this scenario possible.

After Bob logs into cis-test-instance:
1. Click on **Account > Access** tab in the nav bar
2. Select the **access group** - **sec-group** you want to provide access
3. Select **bob.com**
4. Select **Writer** role
5. Select the **Security config** option
6. Click **create policy**

On the Manage Tab:
The following policies are created for **sec-group** :
```
Reader	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, domainId: 4b23ec772965f672f96f05670e36827e	
Viewer	Resource	Only service instance cis-test-instance of CIS 	
Writer	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, cfgType: security, domainId: 4b23ec772965f672f96f05670e36827e

Service Instance 
    name: cis-test-instance  
    id: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9 
Domain 
    name: bob.com
    id: 4b23ec772965f672f96f05670e36827e 
```


Now sec-group has access to see only bob.com, and can modify values pertaining to security. 

##### Update from Writer to Manager Role for an Access group:

If Bob wants to update the role of sec-group from Writer to Manager:
First, Bob needs to delete the existing policy 
1. Go tot he Manage IAM tab > Access groups > sec-group > access policies
2. Delete the following Policy 
```
Writer	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, cfgType: security, domainId: 4b23ec772965f672f96f05670e36827e
```

Lastly, Bob has to create the new policy 
1. Click on **Account > Access** tab in the nav bar
2. Select the **access group** - **sec-group** you want to provide access
3. Select **bob.com**
4. Select **Manager** role
5. Select the **Security config** option
6. Click **create policy**

```
Reader	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, domainId: 4b23ec772965f672f96f05670e36827e	
Viewer	Resource	Only service instance cis-test-instance of CIS 	
Manager	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, cfgType: security, domainId: 4b23ec772965f672f96f05670e36827e

```


##### Update the configuration to include Performance along with Security

If Bob wants to give Manager sec-group access to performance configuration on bob.com along with security.
1. Click on **Account > Access** tab in the nav bar
2. Select the **access group** - **sec-group** you want to provide access
3. Select **bob.com**
4. Select **Manager** role
5. Select the **Performance config** option
6. Click **create policy**

```
Reader	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, domainId: 4b23ec772965f672f96f05670e36827e	
Viewer	Resource	Only service instance cis-test-instance of CIS 	
Manager	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, cfgType: security, domainId: 4b23ec772965f672f96f05670e36827e
Manager	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, cfgType: performance, domainId: 4b23ec772965f672f96f05670e36827e

```


#### Access to all domains with `security config`

If you want to provide security actions for bob.com and bob-ibm.com from the previous example, you must create a new policy by repeating the steps for each domain. The only difference is selecting the respective domain for each policy.

1. Click on **Account > Access** tab in the nav bar
2. Select the **access group** - **sec-group** you want to provide access
3. Select **bob.com**
4. Select **Manager** role
5. Select the **Security config** option
6. Click **create policy**

```
Reader	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, domainId: 4b23ec772965f672f96f05670e36827e	
Viewer	Resource	Only service instance cis-test-instance of CIS 	
Manager	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, cfgType: security, domainId: 4b23ec772965f672f96f05670e36827e

```

1. Click on **Account > Access** tab in the nav bar
2. Select the **access group** - **sec-group** you want to provide access
3. Select **bob-ibm.com**
4. Select **Manager** role
5. Select the **Security config** option
6. Click **create policy**

```
Reader	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, domainId: 7ad7341865246f5df482ad9f76aafb5a	
Viewer	Resource	Only service instance cis-test-instance of CIS 	
Manager	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, cfgType: security, domainId: 7ad7341865246f5df482ad9f76aafb5a

```



#### Access to single domain with `security config` and `reliability config`

Bob has a CIS instance cis-test-instance, and has 2 domains, bob.com and bob-ibm.com.
Bob wants to provide Tony access to Writer role only the *security and reliability actions* of *bob-ibm.com*.

After Bob logs into cis-test-instance, they:
1. Click on **Account > Access** tab in the nav bar
1. Select the **Tony** you want to provide access
1. Select **bob-ibm.com**
1. Select **Writer** Role
1. Select the checkbox for **Security and reliability** option 
1. Click **create policy**

This creates two policies on the backend for each config type.

### Domain level without config 

Bob wants to grant read/write/mange at a domain level to Tony

#### Write/manage
After Bob logs into cis-test-instance, they:
1. Click on **Account > Access** tab in the nav bar
1. Select the **Tony** you want to provide access
1. Select **bob.com**
1. Select **Writer** Role
1. Click **create policy**

```
Writer	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, domainId: 7ad7341865246f5df482ad9f76aafb5a	
Viewer	Resource	Only service instance cis-test-instance of CIS 	
```

#### Reader
After Bob logs into cis-test-instance, they:
1. Click on **Account > Access** tab in the nav bar
1. Select the **Tony** you want to provide access
1. Select **bob.com**
1. Select **Reader** Role
1. All check boxes are pre-ticked to show that the user needs *min* read access to the whole domain, and cannot give partial access to a domain
1. Click **create policy**


```
Reader	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, domainId: 7ad7341865246f5df482ad9f76aafb5a	
Viewer	Resource	Only service instance cis-test-instance of CIS 	
```

### Instance level - all your domains

This policy must be created and managed through the IAM manage page.

Instance level access means that Bob can give Tony permission to Instance 1 out of the 10 instances present.
User B is able to view all the domains in this instance. 

If Bob wants to give Writer or Manager to access the following, he needs to give instance level access:
1. Load balancer - pools and monitors
2. Firewall access rules
2. Workers etc

Steps:
In the manage IAM page:
Create a writer/manger policy on the service instance cis-test-instance

```
Manager	Resource	Only service instance cis-test-instance of CIS 	
or
Writer	Resource	Only service instance cis-test-instance of CIS 	
```

## Manage IAM policies 

CIS allows users to create IAM policies, but management must be done through the [IAM Page](
https://cloud.ibm.com/iam#/overview).

## Note
For every policy created on the Access page in the CIS instance, 2-3 policies will be created in turn.

1. The service instance Platform viewer role allows the added user to view the instance on the dashboard.
example:
```
Viewer	Resource	Only service instance cis-instance-instance of CIS 	
```
2. The domain level read access is the min requirement for fine grained access to work.
```
Reader	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, domainId: 4b23ec772965f672f96f05670e36827e	
```
3. The policy you created with config type present.
```
Writer	Resource	serviceName: internet-svcs, serviceInstance: 8571763b-a0c2-40f4-af5e-e87f9b1e16b9, cfgType: security, domainId: 4b23ec772965f672f96f05670e36827e
```
