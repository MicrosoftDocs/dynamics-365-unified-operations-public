---
title: MethodInfo class
description: This topic describes the MethodInfo class.
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

# Class MethodInfo

[!include [banner](../../includes/banner.md)]

```xpp
class MethodInfo extends Object
```

Provides information about a specified method.

## Remarks

Assign a table method to MethodInfo by using the SysDictTable class. Assign a class method by using the SysDictClass class. The following classes extend MethodInfo:

-   SysMethodInfo
-   DictMethod

## Examples

The following example uses the SysDictClass::ObjectMethodObject method to assign a method of a FormBuildDataSource Class object to an instance of the MethodInfo class. An integer value specifies the method. The MethodInfo.name Method method returns the method name.

```xpp
void getMethodInfo() 
{ 
    MethodInfo methodInfo; 
    SysDictClass sysDictClass; 
    str name; 
    try 
    { 
        sysDictClass = new SysDictClass(classnum(FormBuildDataSource)); 
        methodInfo = sysDictClass.objectMethodObject(1); 
        if(!methodInfo) 
        { 
            throw exception::Error; 
        } 
        name = methodInfo.name(); 
        print name; 
        pause; 
     } 
     catch (exception::Error) 
     { 
        print "The specified method does not exist"; 
        pause; 
     } 
}
```

## Methods

| Method                                                      | Description                                                                                                                                   |
|-------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public AccessSpecifier accessSpecifier()                    | Specifies whether the method is public, protected, or private.                                                                                |
| public boolean compiledOk()                                 | Specifies whether the method has compiled.                                                                                                    |
| public TableId displayTableId()                             |                                                                                                                                               |
| public DisplayFunctionType displayType()                    | Specifies the display function type of a method.                                                                                              |
| public Array getAllAttributes()                             | Gets the full set of attributes for the method.                                                                                               |
| public Object getAttribute(str attribute)                   | Gets the first matching attribute from the class header metadata, creates an instance of the Object class that represents it, and returns it. |
| public Array getAttributes(str attribute)                   |                                                                                                                                               |
| public boolean isAbstract()                                 | Indicates whether the method is abstract.                                                                                                     |
| public boolean isStatic()                                   | Specifies whether the method is static.                                                                                                       |
| public str name()                                           | Specifies the name of a method.                                                                                                               |
| public int noParms()                                        | Specifies the number of parameters in a method.                                                                                               |
| public int noVars()                                         | Specifies the number of variables in a method.                                                                                                |
| public int parentId()                                       | Specifies the table ID for a table method or the class ID for a class method.                                                                 |
| public str propertyHelp()                                   | Specifies the Help text that a method sets or returns for a control.                                                                          |
| public NoYes PropertyMethod()                               | Specifies whether a method is a property method.                                                                                              |
| public int returnId()                                       | Specifies the ID for certain return data types, such as extended data types and classes, for a method that returns a value.                   |
| public Types returnType()                                   | Specifies a method return type.                                                                                                               |
| public ClassRunMode runMode()                               | Specifies where a method is executed.                                                                                                         |
| public int varId(int variableNumber)                        | Specifies the ID for certain variable data types, such as extended data types and enums, for a method that contains variables.                |
| public int varIdOld(int variableNumber)                     |                                                                                                                                               |
| public Types varType(int variableNumber)                    | Specifies a variable data type by using values from the Types enumeration.                                                                    |
| public void new(UtilElementType utilType, int Id, str Name) | Creates a new instance of the MethodInfo class.                                                                                               |
| public void setMethod(MemberFunction method)                | Specifies the application object type of a node in the Application Object Tree (AOT) by using an instance of the .                            |

## Method accessSpecifier

Specifies whether the method is public, protected, or private.

```xpp
public AccessSpecifier accessSpecifier()
```

### Return Value - accessSpecifier

An AccessSpecifier enum value that specifies whether the method is public, protected, or private.

## Method compiledOk

Specifies whether the method has compiled.

```xpp
public boolean compiledOk()
```

### Return Value - compiledOk

true if the method has compiled; otherwise, false.

## Method displayTableId

```xpp
public TableId displayTableId()
```

### Return Value - displayTableId

## Method displayType

Specifies the display function type of a method.

```xpp
public DisplayFunctionType displayType()
```

### Return Value - displayType

A DisplayFunctionType enumeration value that indicates the display function type of a method.

### Remarks - displayType

The following table lists the possible values returned by the displayType method.

|           |                                             |
|-----------|---------------------------------------------|
| Get       | The method is a display method.             |
| None      | The method is not a display or edit method. |
| RecordGet | The method gets a record.                   |
| RecordSet | The method sets a record.                   |
| Set       | The method is an edit method.               |

## Method getAllAttributes

Gets the full set of attributes for the method.

```xpp
public Array getAllAttributes()
```

### Return Value - getAllAttributes

The Array of SysAttribute objects for the method.

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

## Method isAbstract

Indicates whether the method is abstract.

```xpp
public boolean isAbstract()
```

### Return Value - isAbstract

true if the method is abstract; otherwise, false.

### Remarks - isAbstract

An abstract method is declared but not implemented in a parent class. For more information, see Method Modifiers.

## Method isStatic

Specifies whether the method is static.

```xpp
public boolean isStatic()
```

### Return Value - isStatic

true if the method is static; otherwise, false.

### Remarks - isStatic

For more information, see Static Methods.

## Method name

Specifies the name of a method.

```xpp
public str name()
```

### Return Value - name

A string that indicates the method name.

## Method noParms

Specifies the number of parameters in a method.

```xpp
public int noParms()
```

### Return Value - noParms

An integer value that indicates the number of parameters in a method.

## Method noVars

Specifies the number of variables in a method.

```xpp
public int noVars()
```

### Return Value - noVars

An integer value that indicates the number of variables in a method.

## Method parentId

Specifies the table ID for a table method or the class ID for a class method.

```xpp
public int parentId()
```

### Return Value - parentId

An integer value that indicates a table ID or a class ID.

## Method propertyHelp

Specifies the Help text that a method sets or returns for a control.

```xpp
public str propertyHelp()
```

### Return Value - propertyHelp

A string that contains the Help text.

## Method PropertyMethod

Specifies whether a method is a property method.

```xpp
public NoYes PropertyMethod()
```

### Return Value - PropertyMethod

1 if the method is a property method; otherwise, 0.

### Remarks - PropertyMethod

A property method sets or returns a property.

## Method returnId

Specifies the ID for certain return data types, such as extended data types and classes, for a method that returns a value.

```xpp
public int returnId()
```

### Return Value - returnId

An integer value that indicates the ID for the return data type.

### Remarks - returnId

The return value is 0 if the data type does not have an ID or if a method does not return a value.

## Method returnType

Specifies a method return type.

```xpp
public Types returnType()
```

### Return Value - returnType

A Types enumeration value that indicates a method return type.

### Remarks - returnType

The following list indicates the possible values. :

-   AnyType
-   BLOB
-   Class
-   Container
-   Date
-   DateTime
-   Enum
-   Grid
-   Int64
-   Integer
-   Real
-   Record
-   RString
-   String
-   UserType
-   VarString
-   void

## Method runMode

Specifies where a method is executed.

```xpp
public ClassRunMode runMode()
```

### Return Value - runMode

A ClassRunMode enumeration value that indicates where a method is executed.

### Remarks - runMode

The following list indicates the possible values.

-   Called
-   Client
-   ClientorServer
-   Server

## Method varId

Specifies the ID for certain variable data types, such as extended data types and enums, for a method that contains variables.

```xpp
public int varId(int variableNumber)
```

### Parameters - varId

variableNumber  
An integer value that specifies a method variable based on the order of the variables listed in the method.

### Return Value - varId

An integer value that indicates the variable data type ID.

### Remarks - varId

The return value is 0 if the data type does not have an ID or if a method does not have variables.

## Method varIdOld

```xpp
public int varIdOld(int variableNumber)
```

### Parameters - varIdOld

variableNumber  

### Return Value - varIdOld

## Method varType

Specifies a variable data type by using values from the Types enumeration.

```xpp
public Types varType(int variableNumber)
```

### Parameters - varType

variableNumber  
An integer that specifies a method variable based on the order of the variables listed in the method.

### Return Value - varType

A Types enumeration value that indicates the variable data type.

### Remarks - varType

Following are the possible values:

-   AnyType
-   BLOB
-   Class
-   Container
-   Date
-   DateTime
-   Enum
-   Grid
-   Int64
-   Integer
-   Real
-   Record
-   RString
-   String
-   UserType
-   VarString
-   void

## Method new

Creates a new instance of the MethodInfo class.

```xpp
public void new(UtilElementType utilType, int Id, str Name)
```

### Parameters - new

utilType  
A string that specifies the name of the element.

<!-- -->

Id  
A string that specifies the name of the element.

<!-- -->

Name  
A string that specifies the name of the element.

## Method setMethod

Specifies the application object type of a node in the Application Object Tree (AOT).

```xpp
public void setMethod(MemberFunction method)
```

### Parameters - setMethod

method  
An instance of the MemberFunction class that represents a node in the AOT.

