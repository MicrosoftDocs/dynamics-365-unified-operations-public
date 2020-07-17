---
title: DictMethod class
description: This topic describes the DictMethod class.
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

# Class DictMethod

[!include [banner](../../includes/banner.md)]

```xpp
class DictMethod extends MethodInfo
```

## Remarks

## Examples

## Methods

| Method                                                      | Description                                                                                                                                                  |
|-------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public AccessSpecifier accessSpecifier()                    | Specifies whether the method is public, protected, or private.                                                                                               |
| public str clrParameterType(int variableNumber)             |                                                                                                                                                              |
| public str clrReturnType()                                  |                                                                                                                                                              |
| public str clrVarType(int variableNumber)                   |                                                                                                                                                              |
| public boolean compiledOk()                                 | Indicates whether the method compiled successfully.                                                                                                          |
| public TableId displayId()                                  |                                                                                                                                                              |
| public DisplayFunctionType displayType()                    | Indicates the type of display function of a method.                                                                                                          |
| public boolean hasImplementation()                          | Determines whether the actual method implementation is on the class or derived from the base class.                                                          |
| public boolean isAbstract()                                 | Indicates whether the method is abstract.                                                                                                                    |
| public boolean isDelegate()                                 | Indicates whether the method is a delegate.                                                                                                                  |
| public boolean isStatic()                                   | Indicates whether the method is static.                                                                                                                      |
| public str name()                                           | Gets the name of the method.                                                                                                                                 |
| public int parameterCnt()                                   | Gets the number of parameters for the method.                                                                                                                |
| public int parameterId(int variableNumber)                  | Gets the ID of the specified parameter.                                                                                                                      |
| public str parameterName(int variableNumber)                | Gets the name of the specified parameter.                                                                                                                    |
| public boolean parameterOptional(int variableNumber)        | Indicates whether the specified parameter of the method is optional.                                                                                         |
| public Types parameterType(int variableNumber)              |                                                                                                                                                              |
| public int parentId()                                       | Gets the ID of the parent that owns the method.                                                                                                              |
| public str propertyHelp()                                   | Gets the Help string for the property that is associated with the method.                                                                                    |
| public NoYes propertyMethod()                               | Indicates whether the method is a property method.                                                                                                           |
| public int returnId()                                       | Specifies the ID for certain return data types, such as extended data types and classes, for a method that returns a value.                                  |
| public Types returnType()                                   | Specifies a method return type.                                                                                                                              |
| public ClassRunMode runMode()                               | Specifies where a method is run.                                                                                                                             |
| public int varCnt()                                         | Gets the number of variables for the method.                                                                                                                 |
| public str varName(int variableNumber)                      | Gets the name of the specified variable.                                                                                                                     |
| public void setMethod(MemberFunction method)                | Specifies the application object type of a node in the Application Object Tree (AOT) by using an instance of the MemberFunction class. |
| public void new(UtilElementType utilType, int id, str name) | Initializes a new instance of the Object class.                                                                                                              |

## Method accessSpecifier

Specifies whether the method is public, protected, or private.

```xpp
public AccessSpecifier accessSpecifier()
```

### Return Value - accessSpecifier

An AccessSpecifier enumeration value that specifies whether the method is public, protected, or private.

## Method clrParameterType

```xpp
public str clrParameterType(int variableNumber)
```

### Parameters - clrParameterType

variableNumber  

### Return Value - clrParameterType

## Method clrReturnType

```xpp
public str clrReturnType()
```

### Return Value - clrReturnType

## Method clrVarType

```xpp
public str clrVarType(int variableNumber)
```

### Parameters - clrVarType

variableNumber  

### Return Value - clrVarType

## Method compiledOk

Indicates whether the method compiled successfully.

```xpp
public boolean compiledOk()
```

### Return Value - compiledOk

true if the method compiled successfully; otherwise, false.

## Method displayId

```xpp
public TableId displayId()
```

### Return Value - displayId

## Method displayType

Indicates the type of display function of a method.

```xpp
public DisplayFunctionType displayType()
```

### Return Value - displayType

A DisplayFunctionType enumeration value that indicates the display function type of a method.

### Remarks - displayType

The following table lists the possible values that are returned by the displayType method.

|           |                                             |
|-----------|---------------------------------------------|
| Get       | The method is a display method.             |
| None      | The method is not a display or edit method. |
| RecordGet | The method retrieves a record.              |
| RecordSet | The method sets a record.                   |
| Set       | The method is an edit method.               |

## Method hasImplementation

Determines whether the actual method implementation is on the class or derived from the base class.

```xpp
public boolean hasImplementation()
```

### Return Value - hasImplementation

true if the method is implemented on the class; otherwise, false.

## Method isAbstract

Indicates whether the method is abstract.

```xpp
public boolean isAbstract()
```

### Return Value - isAbstract

true if the method is abstract; otherwise, false.

## Method isDelegate

Indicates whether the method is a delegate.

```xpp
public boolean isDelegate()
```

### Return Value - isDelegate

true if the method is a delegate; otherwise, false.

## Method isStatic

Indicates whether the method is static.

```xpp
public boolean isStatic()
```

### Return Value - isStatic

true if the method is a static; otherwise, false.

## Method name

Gets the name of the method.

```xpp
public str name()
```

### Return Value - name

The name of the method.

## Method parameterCnt

Gets the number of parameters for the method.

```xpp
public int parameterCnt()
```

### Return Value - parameterCnt

The number of parameters for the method.

## Method parameterId

Gets the ID of the specified parameter.

```xpp
public int parameterId(int variableNumber)
```

### Parameters - parameterId

variableNumber  
The one-based index to the parameter list for the method.

### Return Value - parameterId

The ID of the specified parameter.

## Method parameterName

Gets the name of the specified parameter.

```xpp
public str parameterName(int variableNumber)
```

### Parameters - parameterName

variableNumber  
The one-based index to the parameter list for the method.

### Return Value - parameterName

The name of the specified parameter.

## Method parameterOptional

Indicates whether the specified parameter of the method is optional.

```xpp
public boolean parameterOptional(int variableNumber)
```

### Parameters - parameterOptional

variableNumber  
The one-based index to the parameter list for the method.

### Return Value - parameterOptional

true if the parameter is optional; otherwise, false.

## Method parameterType

```xpp
public Types parameterType(int variableNumber)
```

### Parameters - parameterType

variableNumber  

### Return Value - parameterType

## Method parentId

Gets the ID of the parent that owns the method.

```xpp
public int parentId()
```

### Return Value - parentId

The ID of the parent that owns the method.

## Method propertyHelp

Gets the Help string for the property that is associated with the method.

```xpp
public str propertyHelp()
```

### Return Value - propertyHelp

The Help string for the property that is associated with the method; an empty string if there is no Help string.

### Remarks - propertyHelp

This method calls the DictMethod::propertyMethod method to determine whether the method is a property method.

## Method propertyMethod

Indicates whether the method is a property method.

```xpp
public NoYes propertyMethod()
```

### Return Value - propertyMethod

A NoYes::No enumeration value if the method is a property method; otherwise, a NoYes::Yes enumeration value.

## Method returnId

Specifies the ID for certain return data types, such as extended data types and classes, for a method that returns a value.

```xpp
public int returnId()
```

### Return Value - returnId

The ID for the return data type; 0 (zero) if the data type does not have an ID or a method does not return a value..

## Method returnType

Specifies a method return type.

```xpp
public Types returnType()
```

### Return Value - returnType

A Types enumeration value that indicates the method return type.

### Remarks - returnType

The following list shows the possible values:

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

Specifies where a method is run.

```xpp
public ClassRunMode runMode()
```

### Return Value - runMode

A ClassRunMode enumeration value that indicates where a method is run.

### Remarks - runMode

The following list shows the possible values:

-   Called
-   Client
-   ClientorServer
-   Server

## Method varCnt

Gets the number of variables for the method.

```xpp
public int varCnt()
```

### Return Value - varCnt

The number of local and inherited variables for the method.

## Method varName

Gets the name of the specified variable.

```xpp
public str varName(int variableNumber)
```

### Parameters - varName

variableNumber  
The one-based index to the variable list for the method.

### Return Value - varName

The name of the specified variable.

## Method setMethod

Specifies the application object type of a node in the Application Object Tree (AOT) by using an instance of the MemberFunction class.

```xpp
public void setMethod(MemberFunction method)
```

### Parameters - setMethod

method  
An instance of the MemberFunction class that represents a node in the AOT.

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(UtilElementType utilType, int id, str name)
```

### Parameters - new

utilType  

<!-- -->

id  

<!-- -->

name  

