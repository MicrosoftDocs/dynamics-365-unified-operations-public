---
title: SkipAOSValidationPermission class
description: This topic describes the SkipAOSValidationPermission class.
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

# Class SkipAOSValidationPermission

[!include [banner](../../includes/banner.md)]

```xpp
class SkipAOSValidationPermission extends CodeAccessPermission
```

The SkipAOSValidationPermission class controls the ability to skip AOS validation and check permissions for specific APIs.

## Remarks

For a list of all protected APIs, see Secured APIs. You must call the assert method on the same tier, usually the server tier, that the corresponding CodeAccessPermission.demand method is called on before the protected API is executed. Call a method on the server tier from one of the following: A server static method �or� A class instance method that is set to run on the server by using the RunOn class property.

## Examples

## Methods

| Method                                                 | Description                                                                                                         |
|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of a permission class object.                                                            |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission when overridden by a derived class. |
| public void new()                                      | Initializes a new instance of the SkipAOSValidationPermission class.                                                |

## Method copy

Creates and returns a copy of a permission class object.

```xpp
public CodeAccessPermission copy()
```

### Return Value - copy

A copy of the derived class object.

### Remarks - copy

You can override this method as part of the process of making an API more secure. For more information, see .

## Method isSubsetOf

Determines whether a current permission is a subset of the specified permission when overridden by a derived class.

```xpp
public boolean isSubsetOf(CodeAccessPermission target)
```

### Parameters - isSubsetOf

target  
A CodeAccessPermission class object.

### Return Value - isSubsetOf

true if a current permission is a subset of a specified permission; otherwise, false.

### Remarks - isSubsetOf

You can override the method as part of the process of making an API more secure. For more information, see .

## Method new

Initializes a new instance of the SkipAOSValidationPermission class.

```xpp
public void new()
```

### Examples - new

The following code example demonstrates how to create an instance of the SkipAOSValidationPermission class.

```xpp
server static void main(Args args) 
{ 
    SkipAOSValidationPermission perm; 
    ; 
    perm = new SkipAOSValidationPermission(); 
}
```

