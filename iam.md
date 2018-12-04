---
copyright:
  years: 2018
lastupdated: "2018-12-03"
---

# IAM and CIS

CIS leverages IAM to perform authorization and Authentication.

If you dont wish to add anyone to your CIS instance please disregard this page

Cis has 3 config types you can restrict access by, Reliability, security and Performance based on the nav tree

We are going to walk through on how to provide fine grained access control on your instance/domain

## Roles

There are three roles we leverage from IAM
* Reader - GET calls
* Writer - PATCH and PUT calls
* Manager - POST and DELETE calls

## Access groups VS Users

A policy can be assigned to a User directly or to an Access Group.
We recommend assigning it to an access group to minimize the number of policies created and reducing the trouble of managing these policies.


## Scenarios
We are going to walk through the different kind of access allowed from most restrictive to least
### Domain level with config type

#### Access to 1 domain with security config - Manage and Writer

A User A has a CIS instance A and has 2 domains, Domain 1 and Domain 2
This User A wants to provide all its security engineer(User B) in the company access to manage/edit just the *security actions* of *domain 1*

Lets walk through how to make a IAM policy to make this scenario possible
1. User A logs into Instance A
2. Click on Account --> Access tab in the nav bar
3. Select the access group/ user B you want to provide access too
4. Select Domain 1
5. Select Manage Role/ Writer role
6. Select the Security config option and press create policy

To explain this a little more,
Now user B will have access to see only Domain 1 and can modify values pertaining to the security 


#### Access to all domains with security config

if you want to provide security actions for Domain 1 and Domain 2 from the above example, you need to create a new policy by repeating the above steps for each domain.
Only change will be in step 4 to modify Domain 1 to Domain 2

#### Access to 1 domain but security and performance config

A User A has a CIS instance A and has 2 domains, Domain 1 and Domain 2
This User A wants to provide all its User B access to edit just the *security and performance actions* of *domain 1*

1. User A logs into Instance A
2. Click on Account --> Access tab in the nav bar
3. Select the access group/ user B you want to provide access too
4. Select Domain 1
5. Select Writer role
6. Select the checkbox for  Security and performance option and press create policy

This will create two policies on the backend for each config type

### Domain level without config 

A user A wants to grant read/write/mange at a domain level to User B

Write/manage:
1. User A logs into Instance A
2. Click on Account --> Access tab in the nav bar
3. Select the access group/ user B you want to provide access too
4. Select Domain 1
5. Select Writer role
6. press create policy

Reader:
Write/manage:
1. User A logs into Instance A
2. Click on Account --> Access tab in the nav bar
3. Select the access group/ user B you want to provide access too
4. Select Domain 1
5. Select Reader role
6. All check boxes are pre-ticked to show that the user needs *min* read access to the whole domain and cannot give partial access to a domain
7. press create policy


### Instance level - all your domains

This policy must be created and managed through the IAM manage page.

What instance level access means, User A can give User B permission to Instance 1 out of the 10 instances present.
User B will be able to view all the domains in this instance. 


## Manage IAM policies 

This has to be done through the IAM Page
https://cloud.ibm.com/iam#/overview

## Note
For every policy create on the Access page in the CIS instance 2-3 policies will be created in turn.

1. The service instance Platform viewer role - So the added user can view the instance on the dashboard
2. The domain level read access. That is the min requirement for fine grained access to work
3. The policy you created with config type present.