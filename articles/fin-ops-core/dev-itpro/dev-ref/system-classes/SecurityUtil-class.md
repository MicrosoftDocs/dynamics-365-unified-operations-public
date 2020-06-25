---
title: SecurityUtil class
description: This topic describes the SecurityUtil class.
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

# Class SecurityUtil

[!include [banner](../../includes/banner.md)]

```xpp
class SecurityUtil extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                 | Description                                                                |
|------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| ::public static boolean isImplicitFlushMode()                                                                          | Indicates whether implicit security flushing mode is on.                   |
| ::public static int getRoleEffectiveAccess(Int64 roleID, str secObjectName, int secObjectType, str secObjectChildName) | Retrieves an effective access for role value of securable object.          |
| ::public static container getRolePermissions(Int64 roleID)                                                             | Gets a container of securable objects and their effective access.          |
| ::public static boolean sysAdminMode(\[boolean active\])                                                               | Gets and sets the security administrator mode.                             |
| ::public static void refreshRolePermissions(Int64 roleID)                                                              | Retrieves the effective access of a specified role for a securable object. |
| ::public static void runSecondPassAutoInference()                                                                      | Runs the second pass auto inference.                                       |
| ::public static void flushPermissions()                                                                                | Flushes the permissions.                                                   |
| public void new()                                                                                                      | Initializes a new instance of the SecurityUtil class.                      |
| ::public static void flushAll()                                                                                        |                                                                            |

## Method isImplicitFlushMode

Indicates whether implicit security flushing mode is on.

```xpp
public static boolean isImplicitFlushMode()
```

### Return Value - isImplicitFlushMode

A Boolean value.

## Method getRoleEffectiveAccess

Retrieves an effective access for role value of securable object.

```xpp
public static int getRoleEffectiveAccess(Int64 roleID, str secObjectName, int secObjectType, str secObjectChildName)
```

### Parameters - getRoleEffectiveAccess

roleID  

<!-- -->

secObjectName  

<!-- -->

secObjectType  

<!-- -->

secObjectChildName  

### Return Value - getRoleEffectiveAccess

The effective access value.

## Method getRolePermissions

Gets a container of securable objects and their effective access.

```xpp
public static container getRolePermissions(Int64 roleID)
```

### Parameters - getRolePermissions

roleID  
The role ID.

### Return Value - getRolePermissions

A container of securable objects and their effective access.

## Method sysAdminMode

Gets and sets the security administrator mode.

```xpp
public static boolean sysAdminMode([boolean active])
```

### Parameters - sysAdminMode

active  
A Boolean value.

### Return Value - sysAdminMode

The old state of the security administrator mode.

## Method refreshRolePermissions

Retrieves the effective access of a specified role for a securable object.

```xpp
public static void refreshRolePermissions(Int64 roleID)
```

### Parameters - refreshRolePermissions

roleID  

## Method runSecondPassAutoInference

Runs the second pass auto inference.

```xpp
public static void runSecondPassAutoInference()
```

## Method flushPermissions

Flushes the permissions.

```xpp
public static void flushPermissions()
```

## Method new

Initializes a new instance of the SecurityUtil class.

```xpp
public void new()
```

## Method flushAll

```xpp
public static void flushAll()
```

