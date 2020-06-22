---
title: CLRInterop class
description: This topic describes the CLRInterop class.
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

# Class CLRInterop

[!include [banner](../../includes/banner.md)]

```xpp
class CLRInterop extends Object
```

The ClrInterop class is a utility class that provides functionality for type marshaling and exception handling. Because all the methods are static, no instantiation of the class is required.

## Remarks

## Examples

## Methods

| Method                                                                               | Description                                                                                                                              |
|--------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| ::public static AnyType getAnyTypeForObject(CLRObject clrObject)                     | Converts a common language runtime (CLR) object to a value of the X++ anytype data type.                                                 |
| ::public static CLRObject getLastException()                                         | Retrieves the most recent CLR exception.                                                                                                 |
| ::public static CLRObject getObjectForAnyType(AnyType anyType)                       | Converts a value of the X++ anytype data type to a value of the CLRObject data type.                                                     |
| ::public static CLRObject getType(str clrTypeName)                                   |                                                                                                                                          |
| ::public static boolean isNull(CLRObject clrObject)                                  | Confirms whether the specified CLRObject instance is set to nullNothingnullptrunita null reference (Nothing in Visual Basic).            |
| ::public static CLRObject Null(str clrTypeName)                                      | Returns a CLR data type that has a value of nullNothingnullptrunita null reference (Nothing in Visual Basic).                            |
| ::public static CLRObject parseClrEnum(str clrEnumTypeName, str enumValues)          | Converts the string representation of the name or numeric value of one or more enumerated constants to an equivalent CLRObject instance. |
| ::public static CLRObject staticInvoke(str className, str methodName, VarArg params) | Calls a static method on a CLR data type.                                                                                                |
| ::public static void loadAssembly(str clrAssemblyName)                               |                                                                                                                                          |
| public void new()                                                                    | Initializes a new instance of the CLRInterop class.                                                                                      |

## Method getAnyTypeForObject

Converts a common language runtime (CLR) object to a value of the X++ anytype data type.

```xpp
public static AnyType getAnyTypeForObject(CLRObject clrObject)
```

### Parameters - getAnyTypeForObject

clrObject  
The CLR object to convert to an X++ data type.

### Return Value - getAnyTypeForObject

An X++ anytype date type that has the value of the \_object argument.

### Remarks - getAnyTypeForObject

If an attacker can control input to the getAnyTypeForObject method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method. If the argument cannot be converted to an X++ data type, an exception of the Exception::ClrError type is thrown.

### Examples - getAnyTypeForObject

The following example sets the value of a CLR string to an X++ str data type.

```xpp
{ 
    CLRObject clrObj; 
    InteropPermission perm; 
    System.String   clrStr = "Calculate total"; 
    str             s; 
```

```xpp
    perm = new InteropPermission(InteropKind::ClrInterop); 
    if (perm == null) 
    { 
        return; 
    } 
    perm.assert(); 
```

```xpp
    s = ClrInterop::getAnyTypeForObject(clrStr); 
    CodeAccessPermission::revertAssert(); 
}
```

## Method getLastException

Retrieves the most recent CLR exception.

```xpp
public static CLRObject getLastException()
```

### Return Value - getLastException

The most recent exception of the Exception::ClrError type; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Remarks - getLastException

If an attacker can control input to the getLastException method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method.

### Examples - getLastException

The following example tries to pass in a date that has an invalid format. The CLR exception that is thrown is converted to an X++ exception and then printed to the Infolog. Any nested exceptions are also printed to the Infolog.

```xpp
static void Job2(Args _args) 
{ 
    CLRObject clrObj; 
    InteropPermission perm; 
```

```xpp
    try 
    { 
        System.DateTime::Parse( "-1/-1/-1"); 
    } 
    catch( Exception::CLRError ) 
    { 
        perm = new InteropPermission(InteropKind::ClrInterop); 
        if (perm == null) 
        { 
            return; 
        } 
        perm.assert(); 
```

```xpp
        e = ClrInterop::getLastException(); 
```

```xpp
        CodeAccessPermission::revertAssert(); 
```

```xpp
        while( e ) 
        { 
            info( e.get_Message() ); 
            e = e.get_InnerException(); 
        } 
    } 
```

```xpp
}
```

## Method getObjectForAnyType

Converts a value of the X++ anytype data type to a value of the CLRObject data type.

```xpp
public static CLRObject getObjectForAnyType(AnyType anyType)
```

### Parameters - getObjectForAnyType

anyType  
The X++ value to convert to a value of the CLRObject data type.

### Return Value - getObjectForAnyType

The CLR object that has the value of the \_anytype argument.

### Remarks - getObjectForAnyType

If an attacker can control input to the getObjectForAnyType method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method. If the argument cannot be converted to the CLRObject type, an exception of the Exception::CLRError type is thrown.

### Examples - getObjectForAnyType

The following example converts a string value to a CLR string object.

```xpp
static void Job3(Args _args) 
{ 
    CLRObject clrObj; 
    InteropPermission perm; 
    System.String s; 
```

```xpp
    perm = new InteropPermission(InteropKind::ClrInterop); 
    if (perm == null) 
    { 
        return; 
    } 
    perm.assert(); 
```

```xpp
    s = CLRInterop::getObjectForAnyType("Calculate total"); 
```

```xpp
    CodeAccessPermission::revertAssert(); 
}
```

## Method getType

```xpp
public static CLRObject getType(str clrTypeName)
```

### Parameters - getType

clrTypeName  

### Return Value - getType

## Method isNull

Confirms whether the specified CLRObject instance is set to nullNothingnullptrunita null reference (Nothing in Visual Basic).

```xpp
public static boolean isNull(CLRObject clrObject)
```

### Parameters - isNull

clrObject  
The CLRObject instance to evaluate.

### Return Value - isNull

true if the specified CLRObject instance is set to nullNothingnullptrunita null reference (Nothing in Visual Basic) or has not been initialized.

### Remarks - isNull

The isNull method should be used instead of the X++ nullNothingnullptrunita null reference (Nothing in Visual Basic) in conditional statements that evaluate whether a CLR data type is nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Examples - isNull

The following example sets the CLR string data type to nullNothingnullptrunita null reference (Nothing in Visual Basic) and assigns the type value to the CLR object. It then calls the isNull method and prints the result in the Infolog.

```xpp
static void Job5(Args _args) 
{ 
    System.String nullStr; 
```

```xpp
    nullStr = CLRInterop::Null("System.String"); 
```

```xpp
    print CLRInterop::isNull(nullStr); 
}
```

## Method Null

Returns a CLR data type that has a value of nullNothingnullptrunita null reference (Nothing in Visual Basic).

```xpp
public static CLRObject Null(str clrTypeName)
```

### Parameters - Null

clrTypeName  
The CLR data type to set to nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Return Value - Null

A CLRObject instance of the specified CLR data type.

### Remarks - Null

If you directly set CLR data types to nullNothingnullptrunita null reference (Nothing in Visual Basic) in X++, you only set the kernel reference to nullNothingnullptrunita null reference (Nothing in Visual Basic). This will make it impossible to use the type as a CLR data type. If you assign the CLR data type to CLRInterop:null("yourType"),, the type can be parsed at run time as a parameter of a static method invocation.

### Examples - Null

The following example sets the CLR string type to nullNothingnullptrunita null reference (Nothing in Visual Basic) and assigns the type value to a CLR object.

```xpp
static void Job5(Args _args) 
{ 
    System.String nullStr; 
```

```xpp
    nullStr = CLRInterop::Null("System.String"); 
```

```xpp
    print CLRInterop::isInitialized(nullStr); 
    print CLRInterop::isNull(nullStr); 
}
```

## Method parseClrEnum

Converts the string representation of the name or numeric value of one or more enumerated constants to an equivalent CLRObject instance.

```xpp
public static CLRObject parseClrEnum(str clrEnumTypeName, str enumValues)
```

### Parameters - parseClrEnum

clrEnumTypeName  
A string that contains the name or value to convert.

<!-- -->

enumValues  
A string that contains the name or value to convert.

### Return Value - parseClrEnum

The CLRObject instance that contains the specified CLR enumerator values.

### Remarks - parseClrEnum

The \_enumValues parameter contains a value, a named constant, or a list of named constants that are delimited by commas (,). One or more blanks spaces can precede or follow each value, name, or comma in \_enumValues. If \_enumValues is a list, the return value is the value of the specified names combined with a bitwise OR operation.

### Examples - parseClrEnum

The following example converts the enumerator value to the string value of Monday and prints the value in the Infolog.

```xpp
static void Job6(Args _args) 
{ 
    System.DayOfWeek    dayOfWeek; 
    System.Type         dayOfWeekType; 
```

```xpp
    dayOfWeek = CLRInterop::parseClrEnum( "System.DayOfWeek", "Monday"); 
```

```xpp
    dayOfWeekType = dayOfWeek.GetType(); 
```

```xpp
    info( dayOfWeek.ToString() ); 
}
```

## Method staticInvoke

Calls a static method on a CLR data type.

```xpp
public static CLRObject staticInvoke(str className, str methodName, VarArg params)
```

### Parameters - staticInvoke

className  
The arguments, if there are any, to the method that is specified in the \_methodName parameter.

<!-- -->

methodName  
The arguments, if there are any, to the method that is specified in the \_methodName parameter.

<!-- -->

params  
The arguments, if there are any, to the method that is specified in the \_methodName parameter.

### Return Value - staticInvoke

The CLRObject that contains the value that is returned by the static CLR method; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Remarks - staticInvoke

If an attacker can control input to the staticInvoke method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission. Make sure that the user has development privileges by setting the security key to SysDevelopment on the control that calls this method. If an error occurs when you call the get\_Now method, the Exception::ClrError exception is thrown.

### Examples - staticInvoke

The following example calls the get\_Now method on the System.DateTime CLR class and prints the results in the Infolog.

```xpp
static void Job7(Args _args) 
{ 
    CLRObject clrObj; 
    InteropPermission perm; 
    System.DateTime dateTime; 
```

```xpp
    perm = new InteropPermission(InteropKind::ClrInterop); 
    if (perm == null) 
    { 
        return; 
    } 
    perm.assert(); 
```

```xpp
    dateTime = CLRInterop::staticInvoke( 
                   "System.DateTime", 
                   "get_Now" ); 
    info(dateTime.ToString()); 
    CodeAccessPermission::revertAssert(); 
```

```xpp
    pause; 
```

```xpp
    // This is the same code using CLR syntax. 
    // dateTime = System.DateTime::get_Now(); 
    // info(dateTime.ToString()); 
}
```

## Method loadAssembly

```xpp
public static void loadAssembly(str clrAssemblyName)
```

### Parameters - loadAssembly

clrAssemblyName  

## Method new

Initializes a new instance of the CLRInterop class.

```xpp
public void new()
```

### Remarks - new

All members of the CLRInterop class are static. There is no requirement to instantiate this class. If an attacker can control input to the new method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the InteropPermission class.

