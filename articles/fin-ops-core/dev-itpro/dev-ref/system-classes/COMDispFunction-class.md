---
title: COMDispFunction class
description: This topic describes the COMDispFunction class.
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

# Class COMDispFunction

[!include [banner](../../includes/banner.md)]

```xpp
class COMDispFunction extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                   | Description                                                                                          |
|--------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| public int call(VarArg )                                                 |                                                                                                      |
| public AnyType callContainerOfParms(container parms)                     |                                                                                                      |
| public str toString()                                                    | Returns a string that represents the current object.                                                 |
| public void finalize()                                                   |                                                                                                      |
| public void new(COM comObject, str functionName, COMDispContext context) | Creates a COMDispFunction object, which is used to access the functionality in an Automation object. |

## Method call

```xpp
public int call(VarArg )
```

### Parameters - call


### Return Value - call

### Remarks - call

If an attacker can control input to the call method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the InteropPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

## Method callContainerOfParms

```xpp
public AnyType callContainerOfParms(container parms)
```

### Parameters - callContainerOfParms

parms  

### Return Value - callContainerOfParms

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

## Method finalize

```xpp
public void finalize()
```

## Method new

Creates a COMDispFunction object, which is used to access the functionality in an Automation object.

```xpp
public void new(COM comObject, str functionName, COMDispContext context)
```

### Parameters - new

comObject  
The context of the functionality to access. The following values are used: COMDispContext::METHOD, COMDispContext::PROPERTYGET, COMDispContext::PROPERTYPUT, and COMDispContext::PROPERTYPUTREF

<!-- -->

functionName  
The context of the functionality to access. The following values are used: COMDispContext::METHOD, COMDispContext::PROPERTYGET, COMDispContext::PROPERTYPUT, and COMDispContext::PROPERTYPUTREF

<!-- -->

context  
The context of the functionality to access. The following values are used: COMDispContext::METHOD, COMDispContext::PROPERTYGET, COMDispContext::PROPERTYPUT, and COMDispContext::PROPERTYPUTREF

### Remarks - new

It is important that you specify the correct context of the functionality in the COM object that you want to access, because a COM object can supply up to four functions that use the same name. Because of the possible name clashing, the context is used to distinguish the method or properties. To specify the correct context, see the documentation for the COM object that you want to access.

### Examples - new



```xpp
{ 
    InteropPermission perm; 
    COM com; 
    COMDispFunction funcShow; 
    COMDispFunction getValue; 
    COMDispFunction putValue; 
    ; 
```

```xpp
    perm = new InteropPermission(InteropKind::ComInterop); 
    perm.assert(); 
    com = new COM("MyCOM.Object"); 
    funcShow = 
        new COMDispFunction(com, "show",  COMDispContext::METHOD); 
    getValue = 
        new COMDispFunction(com, "value", COMDispContext::PROPERTYGET); 
    putValue = 
        new COMDispFunction(com, "value", COMDispContext::PROPERTYPUT); 
}
```

