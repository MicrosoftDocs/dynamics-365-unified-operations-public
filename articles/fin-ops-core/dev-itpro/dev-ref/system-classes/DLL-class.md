---
title: DLL class
description: This topic describes the DLL class.
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

# Class DLL

[!include [banner](../../includes/banner.md)]

```xpp
class DLL extends Object
```

The DLL class enables communication with a Microsoft Windows dynamic-link library (DLL).

## Remarks

If you are using a Unicode DLL, do the following:

-   Use ExtTypes::WString instead of ExtTypes::String to specify a string type.
-   Use Binary::WString instead of Binary::String if you have character data embedded in a binary structure.
-   Use the Binary.wstring method instead of the Binary.string method if you have to read a string from a binary object.

## Examples

The following example uses the DLL and DLLFunction classes to interoperate with the GetVersion API in Kernel32.dll. This example asserts the use of the InteropPermission class, which is required only if the code is running on the server. It loads the DLL and, if it is successful, sets the return type from the call to the DLLFunction class.

```xpp
void DLLExample() 
{ 
    Dll               dll; 
    DllFunction       dllFunc; 
    anytype           retVal; 
    InteropPermission perm; 
    perm = new InteropPermission(InteropKind::DllInterop); 
    // Grants permission to execute the DLL.new method.  
    // DLL.new runs under code access security. 
    perm.assert(); 
    dll = new Dll("Kernel32.dll"); 
    // Closes the code access permission scope. 
       CodeAccessPermission::revertAssert(); 
    if (dll != null) 
    { 
        perm = new InteropPermission(InteropKind::DllInterop); 
    // Grants permission to execute the DLLFunction.new method.  
    // DLLFunction.new runs under code access security. 
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

## Methods

| Method                             | Description                                                                               |
|------------------------------------|-------------------------------------------------------------------------------------------|
| ::public static int lastDLLError() | Sets or retrieves the last error that was reported by the DLL.                            |
| public void new(str filename)      | Creates an instance of the DLL class.                                                     |
| public void finalize()             | Releases resources and performs clean-up before an instance of the DLL class is released. |

## Method lastDLLError

Sets or retrieves the last error that was reported by the DLL.

```xpp
public static int lastDLLError()
```

### Return Value - lastDLLError

The last error that was reported by the DLL.

## Method new

Creates an instance of the DLL class.

```xpp
public void new(str filename)
```

### Parameters - new

filename  
The file name of the DLL to use to create the instance of the DLL class.

### Remarks - new

To access a DLL function, use a created instance of the DLL class in a call to the DLLFunction::new method. If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the InteropPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - new

The following example uses the DLL and DLLFunction classes to interoperate with the GetVersion API in Kernel32.dll. This example asserts the use of the InteropPermission class. It loads the DLL and, if it is successful, sets the return type from the call in the DLLFunction class.

```xpp
void DLLExample() 
{ 
    Dll               dll; 
    DllFunction       dllFunc; 
    anytype           retVal; 
    InteropPermission perm; 
    perm = new InteropPermission(InteropKind::DllInterop); 
    // Grants permission to execute the DLL.new method. 
    // DLL.new runs under code access security. 
    perm.assert(); 
    dll = new Dll("Kernel32.dll"); 
    // Closes the code access permission scope. 
       CodeAccessPermission::revertAssert(); 
    if (dll != null) 
    { 
        perm = new InteropPermission(InteropKind::DllInterop); 
       // Grants permission to execute the DLLFunction.new method. 
       // DLLFunction.new runs under code access security. 
        perm.assert(); 
        dllFunc = new DllFunction(dll, "GetVersion"); 
        if (dllFunc != null) 
        { 
             dllFunc.returns(ExtTypes::DWord); 
            retVal = dllFunc.call(); 
        } 
        // Close the code access permission scope. 
       CodeAccessPermission::revertAssert(); 
    } 
}
```

## Method finalize

Releases resources and performs clean-up before an instance of the DLL class is released.

```xpp
public void finalize()
```

