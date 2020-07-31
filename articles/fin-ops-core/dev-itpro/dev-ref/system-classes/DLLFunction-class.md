---
title: DLLFunction class
description: This topic describes the DLLFunction class.
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

# Class DLLFunction

[!include [banner](../../includes/banner.md)]

```xpp
class DLLFunction extends Object
```

## Remarks

## Examples

## Methods

| Method                                           | Description                                     |
|--------------------------------------------------|-------------------------------------------------|
| public AnyType call(VarArg )                     |                                                 |
| public ExtTypes returns(\[ExtTypes returnType\]) |                                                 |
| public void new(DLL dll, str functionname)       | Initializes a new instance of the Object class. |
| public void finalize()                           |                                                 |
| public void arg(VarArg )                         |                                                 |

## Method call

```xpp
public AnyType call(VarArg )
```

### Parameters - call


### Return Value - call

### Remarks - call

If an attacker can control input to the call method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - call

The following example uses the DLL and DLLFunction classes to interoperate with the GetVersion API in Kernel32.dll. It asserts the use of the InteropPermission class to provide code access protection, and then it loads the DLL. If this is successful, the return type is set from the call to the DLLFunction class.

```xpp
{ 
    Dll               dll; 
    DllFunction       dllFunc; 
    anytype           retVal; 
    InteropPermission perm; 
    perm = new InteropPermission(InteropKind::DllInterop); 
    // Grants permission to execute the DLL.new method. 
    // DLL.new is protected by code access security. 
    perm.assert(); 
    dll = new Dll("Kernel32.dll"); 
    // Closes the code access permission scope. 
    CodeAccessPermission::revertAssert(); 
    if (dll != null) 
    { 
        // Grants permission to execute the DLLFunction.new method. 
        // DLLFunction.new is protected by code access security. 
        perm = new InteropPermission(InteropKind::DllInterop); 
        perm.assert(); 
        dllFunc = new DllFunction(dll, "GetVersion"); 
        if (dllFunc != null) 
         { 
            dllFunc.returns(ExtTypes::DWord); 
             retVal = dllFunc.call(); 
         } 
       // Closes the code access permission scope. 
       CodeAccessPermission::revertAssert(); 
    } 
}
```

## Method returns

```xpp
public ExtTypes returns([ExtTypes returnType])
```

### Parameters - returns

returnType  

### Return Value - returns

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(DLL dll, str functionname)
```

### Parameters - new

dll  

<!-- -->

functionname  

## Method finalize

```xpp
public void finalize()
```

## Method arg

```xpp
public void arg(VarArg )
```

### Parameters - arg


