---
title: CLRObject class
description: This topic describes the CLRObject class.
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

# Class CLRObject

[!include [banner](../../includes/banner.md)]

```xpp
class CLRObject extends Object
```

The CLRObject class holds a reference to an instance of a common language runtime (CLR) object and dispatches calls from X++ to the corresponding wrapped managed instance.

## Remarks

## Examples

## Methods

| Method                                            | Description                                   |
|---------------------------------------------------|-----------------------------------------------|
| private CLRObject dispatch(VarArg )               | Reserved: Do not explicitly call this method. |
| public void new(str className, \[VarArg params\]) | Creates an instance of the CLRObject class.   |

## Method dispatch

Reserved: Do not explicitly call this method.

```xpp
private CLRObject dispatch(VarArg )
```

### Parameters - dispatch


### Return Value - dispatch

### Remarks - dispatch

If an attacker can control input to the dispatch method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the InteropPermission class.

## Method new

Creates an instance of the CLRObject class.

```xpp
public void new(str className, [VarArg params])
```

### Parameters - new

className  
The arguments for the constructor of the CLR class to instantiate.

<!-- -->

params  
The arguments for the constructor of the CLR class to instantiate.

### Remarks - new

Instances of the CLRObject class are used to wrap values that are returned from calls to CLR methods. If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the InteropPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls the new method. If a new ClrObject object cannot be instantiated, the Exception:Internal exception is thrown. To obtain the original CLR exception, call the CLRInterop::getLastException method.

### Examples - new

This example creates a new System.Int32 CLR object.

```xpp
void ClrObjectExample() 
{ 
    CLRObject clrObj; 
    InteropPermission perm; 
    anytype retVal; 
```

```xpp
    perm = new InteropPermission(InteropKind::ClrInterop); 
    if (perm == null) 
    { 
        return; 
    } 
```

```xpp
    perm.assert(); 
```

```xpp
    clrObj = new CLRObject("System.Int32"); 
```

```xpp
    CodeAccessPermission::revertAssert(); 
}
```

