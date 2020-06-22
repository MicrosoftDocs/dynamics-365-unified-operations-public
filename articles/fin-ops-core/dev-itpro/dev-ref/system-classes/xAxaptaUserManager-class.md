---
title: xAxaptaUserManager class
description: This topic describes the xAxaptaUserManager class.
author: robinarh
manager: tonyafehr
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

audience: Developer
ms.reviewer: rhaertle
ms.search.scope: Operations
ms.search.region: Global
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Class xAxaptaUserManager

[!include [banner](../../includes/banner.md)]

```xpp
class xAxaptaUserManager extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                               | Description                                                            |
|------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| public container enumerateDomains(str server)                                                        |                                                                        |
| public xAxaptaUserDetails enumerateDomainUsers(str domainName)                                       |                                                                        |
| public str generatePassword()                                                                        |                                                                        |
| public xAxaptaUserDetails getDomainUser(str domainName, str userLogin)                               |                                                                        |
| public str getFQDN(str domainName, \[boolean throwError\])                                           |                                                                        |
| public container getGroupsForUser(str userName)                                                      |                                                                        |
| public container getRolesForUser(str userName, str company)                                          | Gets roles for the given user.                                         |
| public xAxaptaUserDetails getSIDFromName(str userLogin, str domainName, UserAccountType accountType) | Gets user details from the given user logon, domain, and account type. |
| public str getUserSid(str username, str domain)                                                      |                                                                        |
| public boolean validateDomain(str domain)                                                            |                                                                        |
| public boolean validateOrgUnit(str ouName)                                                           |                                                                        |
| public boolean validatePassword(str username, str domain, str password)                              |                                                                        |
| public boolean validateSecGroup(str secGroup)                                                        |                                                                        |
| public void new()                                                                                    | Initializes a new instance of the xAxaptaUserManager class.            |
| public void updateUserRoleAssignments(UserId userId, container roles, container removeRoles)         |                                                                        |
| public void finalize()                                                                               |                                                                        |

## Method enumerateDomains

```xpp
public container enumerateDomains(str server)
```

### Parameters - enumerateDomains

server  

### Return Value - enumerateDomains

## Method enumerateDomainUsers

```xpp
public xAxaptaUserDetails enumerateDomainUsers(str domainName)
```

### Parameters - enumerateDomainUsers

domainName  

### Return Value - enumerateDomainUsers

## Method generatePassword

```xpp
public str generatePassword()
```

### Return Value - generatePassword

## Method getDomainUser

```xpp
public xAxaptaUserDetails getDomainUser(str domainName, str userLogin)
```

### Parameters - getDomainUser

domainName  

<!-- -->

userLogin  

### Return Value - getDomainUser

## Method getFQDN

```xpp
public str getFQDN(str domainName, [boolean throwError])
```

### Parameters - getFQDN

domainName  

<!-- -->

throwError  

### Return Value - getFQDN

## Method getGroupsForUser

```xpp
public container getGroupsForUser(str userName)
```

### Parameters - getGroupsForUser

userName  

### Return Value - getGroupsForUser

## Method getRolesForUser

Gets roles for the given user.

```xpp
public container getRolesForUser(str userName, str company)
```

### Parameters - getRolesForUser

userName  

<!-- -->

company  

### Return Value - getRolesForUser

A container that holds roles for the given user.

## Method getSIDFromName

Gets user details from the given user logon, domain, and account type.

```xpp
public xAxaptaUserDetails getSIDFromName(str userLogin, str domainName, UserAccountType accountType)
```

### Parameters - getSIDFromName

userLogin  

<!-- -->

domainName  

<!-- -->

accountType  

### Return Value - getSIDFromName

A xAxaptaUserDetails class instance that contains user details.

## Method getUserSid

```xpp
public str getUserSid(str username, str domain)
```

### Parameters - getUserSid

username  

<!-- -->

domain  

### Return Value - getUserSid

## Method validateDomain

```xpp
public boolean validateDomain(str domain)
```

### Parameters - validateDomain

domain  

### Return Value - validateDomain

## Method validateOrgUnit

```xpp
public boolean validateOrgUnit(str ouName)
```

### Parameters - validateOrgUnit

ouName  

### Return Value - validateOrgUnit

## Method validatePassword

```xpp
public boolean validatePassword(str username, str domain, str password)
```

### Parameters - validatePassword

username  

<!-- -->

domain  

<!-- -->

password  

### Return Value - validatePassword

## Method validateSecGroup

```xpp
public boolean validateSecGroup(str secGroup)
```

### Parameters - validateSecGroup

secGroup  

### Return Value - validateSecGroup

## Method new

Initializes a new instance of the xAxaptaUserManager class.

```xpp
public void new()
```

## Method updateUserRoleAssignments

```xpp
public void updateUserRoleAssignments(UserId userId, container roles, container removeRoles)
```

### Parameters - updateUserRoleAssignments

userId  

<!-- -->

roles  

<!-- -->

removeRoles  

## Method finalize

```xpp
public void finalize()
```

