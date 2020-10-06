---
title: AllowEncryptionKeyRetrievalPermission class
description: This topic describes the AllowEncryptionKeyRetrievalPermission class.
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

# Class AllowEncryptionKeyRetrievalPermission

[!include [banner](../../includes/banner.md)]

```xpp
class AllowEncryptionKeyRetrievalPermission extends CodeAccessPermission
```

## Remarks

## Examples

## Methods

| Method                                                 | Description                                                                                                               |
|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of a permission class object.                                                                  |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission when it is overridden by a derived class. |
| public void new()                                      | Initializes a new instance of the AllowEncryptionKeyRetrievalPermission class.                                            |

## Method copy

Creates and returns a copy of a permission class object.

```xpp
public CodeAccessPermission copy()
```

### Return Value - copy

A copy of the derived class object.

### Remarks - copy

You can override this method as part of the process of making an API more secure. For more information, see �Securing an API that Executes on the Server Tier.�

## Method isSubsetOf

Determines whether a current permission is a subset of the specified permission when it is overridden by a derived class.

```xpp
public boolean isSubsetOf(CodeAccessPermission target)
```

### Parameters - isSubsetOf

target  
A CodeAccessPermission class object.

### Return Value - isSubsetOf

true if a current permission is a subset of a specified permission; otherwise, false.

### Remarks - isSubsetOf

You can override the method as part of the process of making an API more secure. For more information, see �Securing an API that Executes on the Server Tier.�

## Method new

Initializes a new instance of the AllowEncryptionKeyRetrievalPermission class.

```xpp
public void new()
```

