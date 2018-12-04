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

Restrict access to CIS by three types, based on the navigation tree: reliability, security, and performance. This section walks through how to provide fine-grained access control of your instance.

## Roles

Use the following three roles to leverage IAM
* Reader - GET calls
* Writer - PATCH and PUT calls
* Manager - POST and DELETE calls

## Access groups and users

A policy can be assigned to a User directly or to an Access Group.
We recommend assigning it to an access group to minimize the number of policies created and to reduce the effort of managing these policies.


## Scenarios
This section walks through the different kinds of access allowed, from most restrictive to least.

### Domain level with `config` type

#### Access to single domain with `security config` - Manage and Writer

User A has a CIS instance A, and has two domains, Domain 1 and Domain 2.
User A wants to provide all security engineers (User B) in the company access to manage and edit only the *security actions* of *Domain 1*.

These steps show how to create an IAM policy to make this scenario possible.

After User A logs into Instance A, they:
1. Click on **Account > Access** tab in the nav bar
1. Select the **access group/ user B** you want to provide access
1. Select **Domain 1**
1. Select **Manage Role/ Writer** role
1. Select the **Security config** option
1. Click **create policy**

Now User B has access to see only Domain 1, and can modify values pertaining to security. 


#### Access to all domains with `security config`

If you want to provide security actions for Domain 1 and Domain 2 from the previous example, you must create a new policy by repeating the steps for each domain. The only difference is selecting the respective domain for each policy.


#### Access to single domain with `security config` and `performance config`

User A has a CIS instance A, and has 2 domains, Domain 1 and Domain 2.
User A wants to provide all with User B access to edit only the *security and performance actions* of *Domain 1*.

After User A logs into Instance A, they:
1. Click on **Account > Access** tab in the nav bar
1. Select the **access group/ user B** you want to provide access
1. Select **Domain 1**
1. Select **Writer Role**
1. Select the checkbox for **Security and performance** option 
1. Click **create policy**

This creates two policies on the backend for each config type.

### Domain level without config 

A user A wants to grant read/write/mange at a domain level to User B

#### Write/manage
After User A logs into Instance A, they:
1. Click on **Account > Access** tab in the nav bar
1. Select the **access group/ user B** you want to provide access
1. Select **Domain 1**
1. Select **Writer Role**
1. Click **create policy**

#### Reader
After User A logs into Instance A, they:
1. Click on **Account > Access** tab in the nav bar
1. Select the **access group/ user B** you want to provide access
1. Select **Domain 1**
1. Select **Reader Role**
1. All check boxes are pre-ticked to show that the user needs *min* read access to the whole domain, and cannot give partial access to a domain
1. Click **create policy**


### Instance level - all your domains

This policy must be created and managed through the IAM manage page.

Instance level access means that User A can give User B permission to Instance 1 out of the 10 instances present.
User B is able to view all the domains in this instance. 


## Manage IAM policies 

CIS allows users to create IAM policies, but management must be done through the [IAM Page](
https://cloud.ibm.com/iam#/overview).

## Note
For every policy created on the Access page in the CIS instance, 2-3 policies will be created in turn.

1. The service instance Platform viewer role allows the added user to view the instance on the dashboard.
1. The domain level read access is the min requirement for fine grained access to work.
1. The policy you created with config type present.
