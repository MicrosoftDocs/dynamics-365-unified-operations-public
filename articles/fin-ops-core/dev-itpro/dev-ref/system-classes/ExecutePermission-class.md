---
title: ExecutePermission class
description: This topic describes the ExecutePermission class.
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

# Class ExecutePermission

[!include [banner](../../includes/banner.md)]

```xpp
class ExecutePermission extends CodeAccessPermission
```

The ExecutePermission class controls the execution of X++ code.

## Remarks

This class is designed to check permissions for specific APIs. For a list of all APIs that are protected by permissions, see Secured APIs. Before the protected API is executed, you must call the assert method on the same tier (which is usually the server tier) that the corresponding CodeAccessPermission::demand method is called on. Call a method on the server tier from one of the following methods:

-   A server static method
-   A class instance method that is set to run on the server by using the RunOn class property

## Examples

The following code example shows a new instance of the ExecutePermission class. The assert method is called to declare that the code can then call the Thread.new method to create a new thread.

```xpp
server static void main(Args args) 
{ 
    Thread _t; 
    ExecutePermission _perm; 
    _perm = new ExecutePermission(); 
    if (!_perm) 
    { 
        return; 
    } 
    _perm.assert(); 
    // Invoke the protected API. 
     _t = new Thread(); 
    // Call member methods. 
    if (_t) 
    { 
        _t.removeOnComplete(true); 
        _t.run(classnum(SysCodeProfiler), identifierstr(transferFile)); 
    } 
    // Optionally, call revertAssert() to limit scope of assert. 
    CodeAccessPermission::revertAssert(); 
}
```

## Methods

| Method                                                 | Description                                                                      |
|--------------------------------------------------------|----------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of the current permission class object.               |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission. |
| public void new()                                      | Initializes a new instance of the ExecutePermission class.                       |

## Method copy

Creates and returns a copy of the current permission class object.

```xpp
public CodeAccessPermission copy()
```

### Return Value - copy

A copy of the current permission object.

### Remarks - copy

You override this method when you derive a class from the CodeAccessPermission class.

## Method isSubsetOf

Determines whether a current permission is a subset of the specified permission.

```xpp
public boolean isSubsetOf(CodeAccessPermission target)
```

### Parameters - isSubsetOf

target  
A CodeAccessPermission class object.

### Return Value - isSubsetOf

true if a current permission is a subset of the specified permission; otherwise, false.

### Remarks - isSubsetOf

You override this method when you derive a class from the CodeAccessPermission class.

## Method new

Initializes a new instance of the ExecutePermission class. End.

```xpp
public void new()
```


