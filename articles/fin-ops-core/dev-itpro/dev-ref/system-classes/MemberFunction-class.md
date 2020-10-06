---
title: MemberFunction class
description: This topic describes the MemberFunction class.
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

# Class MemberFunction

[!include [banner](../../includes/banner.md)]

```xpp
class MemberFunction extends TreeNode
```

The MemberFunction class provides information about a specified node in the Application Object Tree (AOT), such as a form, report, or class.

## Remarks

This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. You can use the ::findNode method to assign a node to an instance of the MemberFunction class.

## Examples

The following example uses the TreeNode::findNode method to assign the node for the AddressSelectForm.callerDataSource method to an instance of the MemberFunction class. The MemberFunction.AOTgetSource Method method returns the method source code.

```xpp
void getMemberFunction() 
{ 
    MemberFunction memberFunction; 
    str name; 
    boolean isStatic; 
    str source; 
    try 
    { 
        memberFunction = TreeNode::findNode( 
           '\\Classes\\AddressSelectForm\\callerDataSource'); 
        if(!memberFunction) 
        { 
            throw exception::Error; 
        } 
        source = memberFunction.AOTgetSource(); 
        print source; 
        pause; 
    } 
    catch (exception::Error) 
    { 
        print "The specified node does not exist."; 
        pause; 
        } 
    } 
}
```

## Methods

| Method                                                     | Description                                                                                                                             |
|------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| public str AOTgetSource()                                  | Provides the source code for a specified node in the AOT, such as a class or method.                                                    |
| public boolean canAddEventHandler()                        |                                                                                                                                         |
| public boolean isEvent()                                   |                                                                                                                                         |
| public boolean isStatic()                                  | Indicates whether a method is static.                                                                                                   |
| public str name(\[str value\])                             | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public void AOTedit(\[int Line\], \[int Column\])          | Opens the appropriate editor for a specified node in the AOT.                                                                           |
| public void new()                                          | Initializes a new instance of the MemberFunction class.                                                                                 |
| public void AOTsetSource(str source, \[boolean isStatic\]) | Sets the source code for a specified node in the AOT, such as a class or method.                                                        |

## Method AOTgetSource

Provides the source code for a specified node in the AOT, such as a class or method.

```xpp
public str AOTgetSource()
```

### Return Value - AOTgetSource

A string value for the source code; nullNothingnullptrunita null reference (Nothing in Visual Basic) if the node does not contain source code.

## Method canAddEventHandler

```xpp
public boolean canAddEventHandler()
```

### Return Value - canAddEventHandler

## Method isEvent

```xpp
public boolean isEvent()
```

### Return Value - isEvent

## Method isStatic

Indicates whether a method is static.

```xpp
public boolean isStatic()
```

### Return Value - isStatic

true if the method is static; otherwise, false.

### Remarks - isStatic

This method is associated with a specified node in the AOT, such as a form, report, or class. This method is used primarily in conjunction with the MemberFunction::AOTsetSource method.

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  
A string that specifies a node; optional.

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It starts with a letter.
-   It doesn't exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, and classes.

## Method AOTedit

Opens the appropriate editor for a specified node in the AOT.

```xpp
public void AOTedit([int Line], [int Column])
```

### Parameters - AOTedit

Line  
An integer that specifies the column position for the cursor; optional.

<!-- -->

Column  
An integer that specifies the column position for the cursor; optional.

## Method new

Initializes a new instance of the MemberFunction class.

```xpp
public void new()
```

## Method AOTsetSource

Sets the source code for a specified node in the AOT, such as a class or method.

```xpp
public void AOTsetSource(str source, [boolean isStatic])
```

### Parameters - AOTsetSource

source  
A Boolean value: true for a static method or false for an instance method; optional.

<!-- -->

isStatic  
A Boolean value: true for a static method or false for an instance method; optional.

