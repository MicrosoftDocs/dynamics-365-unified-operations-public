---
title: InteropPermission class
description: This topic describes the InteropPermission class.
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

# Class InteropPermission

[!include [banner](../../includes/banner.md)]

```xpp
class InteropPermission extends CodeAccessPermission
```

The InteropPermission class controls the ability to call unmanaged and managed code.

## Remarks

The InteropPermission class is designed to check permissions for specific APIs. For a list of all APIs that are protected by permissions, see Secured APIs. Before the protected API is run, you must call the assert method on the same tier (usually the server tier) that the corresponding CodeAccessPermission::demand method is called on. Call a method on the server tier from one of the following methods:

-   A server static method
-   A class instance method that is set to run on the server by using the RunOn class property.

## Examples

The following code example shows a new instance of the InteropPermission class. The assert method is called to declare that the code can then instantiate the DLL class that provides the ability to communicate with a Microsoft Windows dynamic-link library (DLL).

```xpp
server static void main(Args args) 
{ 
    InteropPermission _perm; 
    DLL _dll; 
    _perm = new InteropPermission(InteropKind::DllInterop); 
    _perm.assert(); 
    // Invoke the protected API. 
    _dll = new DLL('cfx2032.dll'); 
    // Optionally, call revertAssert() to limit the scope of assert. 
    CodeAccessPermission::revertAssert(); 
}
```

## Methods

| Method                                                 | Description                                                                        |
|--------------------------------------------------------|------------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of the current permission class object.                 |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether the current permission is a subset of the specified permission. |
| public void new(InteropKind kind)                      | Creates a new instance of the InteropPermission class.                            |

## Method copy

Creates and returns a copy of the current permission class object.

```xpp
public CodeAccessPermission copy()
```

### Return Value - copy

A copy of the current permission object.

### Remarks - copy

You override this method when you derive a class from the CodeAccessPermission class. For more information, see the copy method.

## Method isSubsetOf

Determines whether the current permission is a subset of the specified permission.

```xpp
public boolean isSubsetOf(CodeAccessPermission target)
```

### Parameters - isSubsetOf

target  
A CodeAccessPermission class object.

### Return Value - isSubsetOf

true if the current permission is a subset of the specified permission; otherwise, false.

### Remarks - isSubsetOf

You override this method when you derive a class from the CodeAccessPermission class. For more information, see the isSubsetOf method.

## Method new

Creates a new instance of the InteropPermission class.

```xpp
public void new(InteropKind kind)
```

### Parameters - new

kind  
An InteropKind system enumeration value that specifies access to managed or unmanaged code.

### Examples - new

The following code example shows a new instance of the InteropPermission class that specifies access to Win32 DLLs.

```xpp
server static void main(Args args) 
{ 
    InteropPermission _perm; 
    _perm = new InteropPermission(InteropKind::DllInterop); 
}
```

