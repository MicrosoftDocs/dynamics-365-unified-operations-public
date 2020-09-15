---
title: DictClass class
description: This topic describes the DictClass class.
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

# Class DictClass

[!include [banner](../../includes/banner.md)]

```xpp
class DictClass extends Object
```

The DictClass class provides information about a class.

## Remarks

## Examples

## Methods

| Method                                                            | Description                                                                                                                                   |
|-------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public AnyType callObject(str methodName, Object Called, VarArg ) | Calls a method on an object.                                                                                                                  |
| public AnyType callStatic(str methodName, VarArg )                | Calls a static method.                                                                                                                        |
| public ClassId extend()                                           | Provides the ID for the class that a specified class extends.                                                                                 |
| public List extendedBy(\[boolean allLevels\])                     | Provides a List object for the classes that extend a specified class.                                                                         |
| public Array getAllAttributes()                                   | Retrieves the full set of attributes for the class.                                                                                           |
| public Object getAttribute(str attribute)                         | Gets the first matching attribute from the class header metadata, creates an instance of the Object class that represents it, and returns it. |
| public Array getAttributes(str attribute)                         |                                                                                                                                               |
| public ClassId id()                                               | Provides the ID for a specified class.                                                                                                        |
| public ClassId implements(int no)                                 | Provides the ID for a specified interface that a class implements.                                                                            |
| public int implementsCnt()                                        | Indicates the number of interfaces that a class implements.                                                                                   |
| public boolean isAbstract()                                       | Indicates whether a class is abstract.                                                                                                        |
| public boolean isFinal()                                          | Indicates whether a class is final.                                                                                                           |
| public boolean isInterface()                                      | Indicates whether an object is an interface.                                                                                                  |
| public boolean isKernel()                                         | Indicates whether a class is a kernel class.                                                                                                  |
| public boolean isRunable()                                        | Indicates whether a class can be run.                                                                                                         |
| public Object makeObject(VarArg )                                 | Creates an object.                                                                                                                            |
| public str name()                                                 | Provides the name of a class.                                                                                                                 |
| public str objectMethod(int methodNumber)                         | Provides the name of a specified instance method in a class.                                                                                  |
| public int objectMethodCnt()                                      | Indicates the number of instance methods in a class.                                                                                          |
| public DictMethod objectMethodObject(int methodNumber)            | Provides information about a specified instance method in a class by returning a DictMethod object.                                           |
| public ClassRunMode RunMode()                                     | Specifies where a class is executed.                                                                                                          |
| public str staticMethod(int methodNumber)                         | Provides the name of a specified static method in a class.                                                                                    |
| public int staticMethodCnt()                                      | Indicates the number of static methods in a class.                                                                                            |
| public DictMethod staticMethodObject(int methodNumber)            | Provides information about a specified static method in a class by returning a DictMethod object.                                             |
| ::public static Array getAttributedClasses(str attribute)         |                                                                                                                                               |
| ::public static Object createObject(str className, VarArg )       |                                                                                                                                               |
| public void new(ClassId classId)                                  | Initializes a new instance of the Object class.                                                                                               |

## Method callObject

Calls a method on an object.

```xpp
public AnyType callObject(str methodName, Object Called, VarArg )
```

### Parameters - callObject

methodName  

<!-- -->

Called  

<!-- -->


### Return Value - callObject

An anytype data type value that is returned by the specified method.

### Remarks - callObject

You must create an instance of the DictClass object by using a class that contains the method that you pass to the callObject method. If an attacker can control the input to the callObject method, a security risk exists. Therefore, this method runs under code access security. Calls to this method on the server require permission from the InteropPermission class. Make sure that the user has development rights by setting the security key to SysDevelopment on the control that calls this method.

### Examples - callObject

This example calls the toString instance method in the Info class, for which the global instance of this class is named infolog, and then prints the value that is returned from the call.

```xpp
static void Job_Example_DictClass_CallObject(Args _args) 
{ 
    DictClass dictClass; 
    anytype   retVal; 
    str      resultOutput; 
    ExecutePermission perm; 
    perm = new ExecutePermission(); 
    // Grants permission to execute the DictClass.callObject method. 
    // DictClass.callObject runs under code access security. 
    perm.assert(); 
    dictClass = new DictClass(classidget(infolog)); 
    if (dictClass != null) 
    { 
        retVal       = dictClass.callObject("toString", infolog); 
        resultOutput = strfmt("Return value is %1", retVal); 
        print resultOutput; 
        pause; 
    } 
    // Closes the code access permission scope. 
    CodeAccessPermission::revertAssert(); 
}
```

## Method callStatic

Calls a static method.

```xpp
public AnyType callStatic(str methodName, VarArg )
```

### Parameters - callStatic

methodName  

<!-- -->


### Return Value - callStatic

An anytype data type value that is returned by the specified method.

### Remarks - callStatic

You must create an instance of an object of the DictClass class by using a class that contains the method passed to the callStatic method. If an attacker can control the input to the callStatic method, a security risk exists. Therefore, this method runs under the code access security. Calls to this method on the server require permission from the ExecutePermission class. Make sure that the user has development rights by setting the security key to the SysDevelopment on the control that calls this method.

### Examples - callStatic

This example calls the AOSClientMode method in the Session class and then prints the value returned from the call.

```xpp
static void Job_Example_DictClass_CallStatic(Args _args) 
{ 
    DictClass dictClass; 
    anytype   retVal; 
    str       resultOutput; 
    ExecutePermission perm; 
    perm = new ExecutePermission(); 
    // Grants permission to execute the DictClass.callStatic method. 
    // DictClass.callStatic runs under code access security. 
    perm.assert(); 
    dictClass = new DictClass(classnum(Session)); 
    if (dictClass != null) 
    { 
        retVal       = dictClass.callStatic("AOSClientMode"); 
        resultOutput = strfmt( 
            "Return value of AOSClientMode is %1",  
            retVal); 
        print resultOutput; 
        pause; 
    } 
    // Closes the code access permission scope. 
    CodeAccessPermission::revertAssert(); 
}
```

## Method extend

Provides the ID for the class that a specified class extends.

```xpp
public ClassId extend()
```

### Return Value - extend

A value of the classID system data type that indicates the class ID; 0 if a class does not extend another class.

## Method extendedBy

Provides a List object for the classes that extend a specified class.

```xpp
public List extendedBy([boolean allLevels])
```

### Parameters - extendedBy

allLevels  

### Return Value - extendedBy

A List object for the classes that extend the class.

## Method getAllAttributes

Retrieves the full set of attributes for the class.

```xpp
public Array getAllAttributes()
```

### Return Value - getAllAttributes

The array of SysAttribute objects for the class.

## Method getAttribute

Gets the first matching attribute from the class header metadata, creates an instance of the Object class that represents it, and returns it.

```xpp
public Object getAttribute(str attribute)
```

### Parameters - getAttribute

attribute  
The attribute for which to search.

### Return Value - getAttribute

The attribute as an instance of the Object class.

## Method getAttributes

```xpp
public Array getAttributes(str attribute)
```

### Parameters - getAttributes

attribute  

### Return Value - getAttributes

## Method id

Provides the ID for a specified class.

```xpp
public ClassId id()
```

### Return Value - id

A value of the classId system data type that indicates the class ID.

## Method implements

Provides the ID for a specified interface that a class implements.

```xpp
public ClassId implements(int no)
```

### Parameters - implements

no  
An integer data type that specifies the interface, based on the order of the interfaces in the class declaration.

### Return Value - implements

A value of the classID system data type that indicates the class ID.

## Method implementsCnt

Indicates the number of interfaces that a class implements.

```xpp
public int implementsCnt()
```

### Return Value - implementsCnt

An integer data type value for the number of interfaces that a class implements.

## Method isAbstract

Indicates whether a class is abstract.

```xpp
public boolean isAbstract()
```

### Return Value - isAbstract

true if the class is abstract; otherwise, false.

## Method isFinal

Indicates whether a class is final.

```xpp
public boolean isFinal()
```

### Return Value - isFinal

true if the class is final; otherwise, false.

## Method isInterface

Indicates whether an object is an interface.

```xpp
public boolean isInterface()
```

### Return Value - isInterface

true if the object is an interface; otherwise, false.

## Method isKernel

Indicates whether a class is a kernel class.

```xpp
public boolean isKernel()
```

### Return Value - isKernel

true if the class is a kernel class; otherwise, false.

## Method isRunable

Indicates whether a class can be run.

```xpp
public boolean isRunable()
```

### Return Value - isRunable

true if the class can be run; otherwise, false.

## Method makeObject

Creates an object.

```xpp
public Object makeObject(VarArg )
```

### Parameters - makeObject


### Return Value - makeObject

An instance of the Object class.

### Remarks - makeObject

You can pass an instance of the Object class to the DictClass::callObject method.

## Method name

Provides the name of a class.

```xpp
public str name()
```

### Return Value - name

A string data type value for the class name.

## Method objectMethod

Provides the name of a specified instance method in a class.

```xpp
public str objectMethod(int methodNumber)
```

### Parameters - objectMethod

methodNumber  
An integer data type that specifies a method in a class, based on the order of the methods.

### Return Value - objectMethod

A string data type value for the method name.

### Remarks - objectMethod

The \_methodNumber parameter starts counting at 1.

## Method objectMethodCnt

Indicates the number of instance methods in a class.

```xpp
public int objectMethodCnt()
```

### Return Value - objectMethodCnt

An integer value that indicates the number of instance methods in a class.

## Method objectMethodObject

Provides information about a specified instance method in a class by returning a DictMethod object.

```xpp
public DictMethod objectMethodObject(int methodNumber)
```

### Parameters - objectMethodObject

methodNumber  
An integer data type that specifies a method in a class, based on the order of the methods. Numbering starts at 1.

### Return Value - objectMethodObject

A DictMethod object that contains information about a specified method in a class.

### Remarks - objectMethodObject

The \_methodNumber parameter starts counting at 1.

## Method RunMode

Specifies where a class is executed.

```xpp
public ClassRunMode RunMode()
```

### Return Value - RunMode

A ClassRunMode system enumeration value that indicates where a class is executed.

### Remarks - RunMode

The following are the possible return values:

-   The Called value.
-   The Client value.
-   The ClientorServer value.
-   The Server value.

## Method staticMethod

Provides the name of a specified static method in a class.

```xpp
public str staticMethod(int methodNumber)
```

### Parameters - staticMethod

methodNumber  
An integer data type that specifies a method in a class, based on the order of the methods.

### Return Value - staticMethod

A string data type value for the method name.

### Remarks - staticMethod

The \_methodNumber parameter starts counting at 1.

## Method staticMethodCnt

Indicates the number of static methods in a class.

```xpp
public int staticMethodCnt()
```

### Return Value - staticMethodCnt

An integer that indicates the number of static methods in a class.

## Method staticMethodObject

Provides information about a specified static method in a class by returning a DictMethod object.

```xpp
public DictMethod staticMethodObject(int methodNumber)
```

### Parameters - staticMethodObject

methodNumber  
An integer data type that specifies a method in a class, based on the order of the methods.

### Return Value - staticMethodObject

A DictMethod object that contains information about a specified method in a class.

### Remarks - staticMethodObject

The \_methodNumber parameter starts counting at 1.

## Method getAttributedClasses

```xpp
public static Array getAttributedClasses(str attribute)
```

### Parameters - getAttributedClasses

attribute  

### Return Value - getAttributedClasses

## Method createObject

```xpp
public static Object createObject(str className, VarArg )
```

### Parameters - createObject

className  

<!-- -->


### Return Value - createObject

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(ClassId classId)
```

### Parameters - new

classId  
A value of the classId system data type that indicates the system ID of a class.

### Remarks - new

Class IDs are unsigned integers and are therefore always in the range 0 to 65535. The method does not fail if an invalid class ID is passed. You can pass a class name to the method instead of a class ID by using the classNum intrinsic function. For more information, see �Intrinsic Functions.�

