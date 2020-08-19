---
title: COM class
description: This topic describes the COM class.
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

# Class COM

[!include [banner](../../includes/banner.md)]

```xpp
class COM
```

The COM class is used to create Component Object Model (COM) objects.

## Remarks

The COM class also supports Distributed Component Object Model (DCOM). DCOM enables objects that support DCOM to run on remote computers. When a COM object has been instantiated by using the COM class, its methods and properties can be accessed by using either the COMDispFunction class or the extended syntax for the COM class. The extended syntax enables methods and properties to be directly called on the COM object, even though they don't appear in the Lookup list (for example, com.comMethod("Hello World");). The extended syntax supports calls to methods and properties that take any number of arguments. Some COM objects support the concept of optional arguments. Only optional variant arguments can be omitted. If optional arguments are omitted, the COM object uses its default values. To omit an argument for the COM object and force it to use its default value, specify the COMArgument::NoValue enumeration, as shown in the following example.

```xpp
com.comMethod(COMArgument::NoValue, "Hello Another World");
```


If the arguments to omit from the COM object appear at the end of the argument list, omit them from the code. The following types are supported for the extended syntax for the COM class argument type and return type:

-   array
-   COM
-   COMVariant
-   date
-   enum
-   int
-   real
-   str

If a COM object returns a date, and if the extended syntax is used, the return value of the COM method should be assigned to a COMVariant class variable. The actual date and time (format) can then be extracted from the COMVariant class by using the date and time properties. If the date return value is assigned to a date variable instead of a COMVariant class, the time component of the date is lost. When the extended syntax is used, you can still call the COM class methods (the methods that appear in the Lookup list) on the objects. The COM class methods have a higher priority than the methods on the actual COM object. If a method on the COM object has the same name as a method on the COM class (for example, attach), you cannot call that method on the COM object. To be able to call the method on the COM object instead of the method that has the same name on the COM class, prefix the duplicate method name with an underscore (for example, com.\_detach();). The extended syntax for the COM class is evaluated at run time, not compile time, which causes a slight decrease in performance. If high-performance code is required, consider using the COMDispFunction class. This class offers performance improvements over the extended syntax for the COM class.

## Examples

This example calls the GetFileName method from the Scripting.FileSystemObject COM object.

```xpp
void COMExample() 
{ 
    COM               com; 
    str               result; 
    InteropPermission perm; 
    ; 
```

```xpp
    // Set code access permission to help protect the use of the 
    // COM object. 
    perm = new InteropPermission(InteropKind::ComInterop); 
    if (perm == null) 
    { 
        return; 
    } 
    // Permission scope starts here. 
    perm.assert(); 
```

```xpp
    com = new COM("Scripting.FileSystemObject"); 
    if (com != null) 
    { 
        result = com.GetFileName(@"c:\boot.ini"); 
    } 
```

```xpp
    // Close code access permission scope. 
    CodeAccessPermission::revertAssert(); 
}
```

## Methods

| Method                                                                                                      | Description                                                                                                                                  |
|-------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| public AnyType dispatch(VarArg )                                                                            | Reserved. Do not explicitly call this method.                                                                                                |
| public str documentationName()                                                                              | Returns the textual name of the COM object that is associated with the instance of the COM class.                                            |
| public COMError error()                                                                                     | Returns a COMError object that is associated with the instance of the COM class.                                                             |
| public ComInterface interface()                                                                             | Returns the interface that is associated with the COM object.                                                                                |
| public int lcid(\[int lcid\])                                                                               |                                                                                                                                              |
| public str toString()                                                                                       | Returns a string that represents the instance of the COM class.                                                                              |
| ::public static COM createFromInterface(ComInterface interface)                                             | Creates an instance of the COM class by using the specified COM interface.                                                                   |
| ::public static COM createFromObject(COM object)                                                            | Creates an instance of the COM class by using the specified COM object.                                                                      |
| ::public static COM createFromVariant(COMVariant variant)                                                   | Creates an instance of the COM class by using the specified instance of the COMVariant class.                                                |
| ::public static COM getObject(str className)                                                                | Returns an instance of a COM object that is running.                                                                                         |
| ::public static COM getObjectEx(str fileName)                                                               | Returns an instance of a COM object that is specified by its file name.                                                                      |
| ::public static AnyType unsupported(int action, \[AnyType param1\], \[AnyType param2\], \[AnyType param3\]) | Reserved.                                                                                                                                    |
| public void finalize()                                                                                      | Frees resources that are associated with the instance of the COM class.                                                                      |
| public void new(\[str className\], \[str computerName\])                                                    | Creates an instance of the COM class that can be attached to the COM class and optionally instantiates a COM object on a specified computer. |
| public void attach(ComInterface interface)                                                                  | Attaches an instance of the COM class to a COM interface.                                                                                    |
| public void detach()                                                                                        | Detaches a COM object from the class that it was associated with.                                                                            |

## Method dispatch

Reserved. Do not explicitly call this method.

```xpp
public AnyType dispatch(VarArg )
```

### Parameters - dispatch


### Return Value - dispatch

## Method documentationName

Returns the textual name of the COM object that is associated with the instance of the COM class.

```xpp
public str documentationName()
```

### Return Value - documentationName

The textual name of the COM object that is associated with the instance of the COM class; an empty string if there is no documentation name for the COM object.

### Remarks - documentationName

The textual name of a class is used by the class to describe itself. The textual name differs from the class name that is used to instantiate the class.

### Examples - documentationName

The following example shows how to retrieve the documentation name for a COM object.

```xpp
str docName; 
; 
// The obj that was previously instantiated. 
docName = obj.documentationName(); 
info(strfmt("documentationName: %1", docName));
```

## Method error

Returns a COMError object that is associated with the instance of the COM class.

```xpp
public COMError error()
```

### Return Value - error

A COMError value that represents the error that is associated with the instance of the COM class.

### Examples - error

The following example shows how to retrieve the error object that is associated with an instance of the COM class.

```xpp
COMError err; 
```

```xpp
// The obj variable was previously instantiated. 
err = obj.error(); 
```

```xpp
// Output the error number. 
info(strfmt("Error: %1", err.number()))
```

## Method interface

Returns the interface that is associated with the COM object.

```xpp
public ComInterface interface()
```

### Return Value - interface

The interface that is associated with the COM object; 0 (zero) if no interface is associated with the COM object.

### Examples - interface

The following example shows how to retrieve the interface that is associated with a COM object.

```xpp
// The obj variable was previously instantiated. 
info(strfmt("Interface: %1", obj.interface()));
```

## Method lcid

```xpp
public int lcid([int lcid])
```

### Parameters - lcid

lcid  

### Return Value - lcid

## Method toString

Returns a string that represents the instance of the COM class.

```xpp
public str toString()
```

### Return Value - toString

A string that contains a description of the instance of the COM class.

### Examples - toString

The following example shows how to use the toString method.

```xpp
print objCOM.toString();
```

## Method createFromInterface

Creates an instance of the COM class by using the specified COM interface.

```xpp
public static COM createFromInterface(ComInterface interface)
```

### Parameters - createFromInterface

interface  
The interface to use to create the new instance of the COM class.

### Return Value - createFromInterface

An instance of the COM class for the COM interface that is specified by the interface parameter; nullNothingnullptrunita null reference (Nothing in Visual Basic) if the instance of the COM class could not be created.

### Remarks - createFromInterface

To help reduce security risks that are associated with unmanaged code, make sure that you validate the objects that are passed to this method, and that all DLLs used for your COM objects are protected by access control lists.

## Method createFromObject

Creates an instance of the COM class by using the specified COM object.

```xpp
public static COM createFromObject(COM object)
```

### Parameters - createFromObject

object  
The instance of the COM class to use to create the new instance of the COM class.

### Return Value - createFromObject

An instance of the COM class for the COM object that is specified by the object parameter; nullNothingnullptrunita null reference (Nothing in Visual Basic) if the instance of the COM class could not be created.

### Remarks - createFromObject

To help reduce security risks that are associated with unmanaged code, make sure that you validate the objects that are passed to this method, and that all DLLs used for your COM objects are protected by access control lists.

## Method createFromVariant

Creates an instance of the COM class by using the specified instance of the COMVariant class.

```xpp
public static COM createFromVariant(COMVariant variant)
```

### Parameters - createFromVariant

variant  
The instance of the COMVariant class to use to create the new instance of the COM class.

### Return Value - createFromVariant

An instance of the COM class for the COM object that is specified by the variant parameter; nullNothingnullptrunita null reference (Nothing in Visual Basic) if the instance of the COM class could not be created.

### Remarks - createFromVariant

To help reduce security risks that are associated with unmanaged code, make sure that you validate the objects that are passed to this method, and that all DLLs used for your COM objects are protected by access control lists.

## Method getObject

Returns an instance of a COM object that is running.

```xpp
public static COM getObject(str className)
```

### Parameters - getObject

className  
The ProgID value or class name of the COM object that is used to create the instance of the COM class.

### Return Value - getObject

An instance of the COM class for the class that is specified by the className parameter; nullNothingnullptrunita null reference (Nothing in Visual Basic) if the instance could not be created.

### Remarks - getObject

If multiple instances of the specified COM object are running, we cannot guarantee which instance will be returned by the getObject method. Some COM objects do not support the extended features that enable calls to this method.

### Examples - getObject

The following example shows how to retrieve an instance of a running COM object.

```xpp
COM objExcel, objWorkBook, objWorkBooks; 
InteropPermission perm; 
```

```xpp
// Set code access permission to help protect the use of COM.new. 
perm = new InteropPermission(InteropKind::ComInterop); 
perm.assert(); 
```

```xpp
objExcel = COM::getObject("Excel.Application"); 
```

```xpp
if (!objExcel) 
{ 
    // Unable to connect to a running instance of Microsoft Excel. 
    // Try starting it. 
    objExcel = new COM("Excel.Application"); 
    if (!objExcel) 
    { 
        Info ("Unable to find or create an instance of Excel"); 
        return;  // Or other error action. 
    }  
} 
// Close code access permission scope. 
CodeAccessPermission::revertAssert(); 
```

```xpp
objExcel.visible(true); 
objWorkBooks = objExcel.workbooks(); 
if (objWorkBooks) 
{ 
    objWorkBook = objWorkBooks.open("d:\mydata\book1.xls"); 
}
```

## Method getObjectEx

Returns an instance of a COM object that is specified by its file name.

```xpp
public static COM getObjectEx(str fileName)
```

### Parameters - getObjectEx

fileName  
The name of the file that provides the functionality for the COM object that is used to create the instance of the COM class.

### Return Value - getObjectEx

An instance of the COM class that is specified by the filename parameter; nullNothingnullptrunita null reference (Nothing in Visual Basic) if the instance could not be created.

### Remarks - getObjectEx

To help reduce security risks that are associated with unmanaged code, make sure that you validate the objects that are passed to this method, and that all DLLs used for your COM objects are protected by access control lists.

## Method unsupported

Reserved.

```xpp
public static AnyType unsupported(int action, [AnyType param1], [AnyType param2], [AnyType param3])
```

### Parameters - unsupported

action  

<!-- -->

param1  

<!-- -->

param2  

<!-- -->

param3  

### Return Value - unsupported

## Method finalize

Frees resources that are associated with the instance of the COM class.

```xpp
public void finalize()
```

### Examples - finalize

The following example how to use the finalize method.

```xpp
objCOM.finalize();
```

## Method new

Creates an instance of the COM class that can be attached to the COM class and optionally instantiates a COM object on a specified computer.

```xpp
public void new([str className], [str computerName])
```

### Parameters - new

className  
The name of the remote computer on which to instantiate the COM object; optional. If this parameter is omitted, the COM object is instantiated on the local computer. If the computer name is specified, the DCOM system component must be installed on both the local computer and the remote computer. The specific COM object must support DCOM, and it must be correctly configured on both the local computer and the remote computer. The system component is a standard component of Microsoft Windows 98, Windows NT, and later versions. In Windows 95, the DCOM system component must be installed.

<!-- -->

computerName  
The name of the remote computer on which to instantiate the COM object; optional. If this parameter is omitted, the COM object is instantiated on the local computer. If the computer name is specified, the DCOM system component must be installed on both the local computer and the remote computer. The specific COM object must support DCOM, and it must be correctly configured on both the local computer and the remote computer. The system component is a standard component of Microsoft Windows 98, Windows NT, and later versions. In Windows 95, the DCOM system component must be installed.

### Remarks - new

The class name of a COM object is either its programmatic identifier (ProgID) or its class identifier (CLSID):

-   ProgIDs have the following format: program.component.version
-   CLSIDs are 128-bit values and have the following format: {xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}

If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the InteropPermission class. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - new

This example calls the GetFileName method from the Scripting.FileSystemObject COM object.

```xpp
void COMExample() 
{ 
    COM               com; 
    str               result; 
    InteropPermission perm; 
```

```xpp
    // Set the code access permission to help protect the use of the 
    // COM object. 
    perm = new InteropPermission(InteropKind::ComInterop); 
    if (perm == null) 
    { 
        return; 
    } 
    // Permission scope starts here. 
    perm.assert(); 
```

```xpp
    com = new COM("Scripting.FileSystemObject"); 
    if (com != null) 
    { 
        result = com.GetFileName(@"c:\boot.ini"); 
    } 
```

```xpp
    // Close the code access permission scope. 
    CodeAccessPermission::revertAssert(); 
}
```

## Method attach

Attaches an instance of the COM class to a COM interface.

```xpp
public void attach(ComInterface interface)
```

### Parameters - attach

interface  
The interface to attach to the instance of the COM class.

### Remarks - attach

This method is provided because some COM objects can be instantiated only by other COM objects and cannot be instantiated directly by the COM class.

## Method detach

Detaches a COM object from the class that it was associated with.

```xpp
public void detach()
```

### Remarks - detach

For example, this method can be called to detach a COM object from a call to the attach or new method.

