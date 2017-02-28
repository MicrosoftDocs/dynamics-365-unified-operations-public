---
# required metadata

title: J Classes
description: System API classes that start with the letter J.
author: RobinARH
manager: AnnBe
ms.date: 2016-03-05 00 - 12 - 53
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 58702
ms.assetid: e932e25e-b72a-428a-830a-20160e81e334
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.intro: 01-02-2016
ms.dyn365.ops.version: AX 7.0.0

---

# J Classes

System API classes that start with the letter J.

Class Job
---------

    class Job extends TreeNode

The Job class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                     | Description                                                                                                                                   |
|------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str AOTgetSource()                                  | Returns the source code of this node.                                                                                                         |
| public str changedBy(\[str value\])                        | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])                    | Gets or sets the date that an application object was last changed.                                                                            |
| public str changedTime(\[str value\])                      | Gets or sets the time that an application object was last changed.                                                                            |
| public str createdBy(\[str value\])                        | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\])                   | Gets or sets the date that an application object was created.                                                                                 |
| public str creationTime(\[str value\])                     |                                                                                                                                               |
| public str name(\[str value\])                             | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])                         |                                                                                                                                               |
| public void AOTsetSource(str source, \[boolean isStatic\]) | Sets the source code of this node.                                                                                                            |
| public void AOTrun()                                       | Compiles this node and its subtree in the Microsoft Dynamics AX Application Object Tree (AOT).                                                |
| public void AOTedit(\[int Line\], \[int Column\])          | Opens the appropriate editor for this node.                                                                                                   |

### Method AOTgetSource

Returns the source code of this node.

    public str AOTgetSource()

#### Return Value

A string that contains the source code, if there is any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

This function is overridden by nodes that have source code.

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date that an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date that an application object was last changed.

### Method changedTime

Gets or sets the time that an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time that an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date that an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date that an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method AOTsetSource

Sets the source code of this node.

    public void AOTsetSource(str source, [boolean isStatic])

#### Parameters

source  
A value that specifies whether the method is static; optional.

<!-- -->

isStatic  
A value that specifies whether the method is static; optional.

#### Remarks

This method is overridden by nodes that have source code.

### Method AOTrun

Compiles this node and its subtree in the Microsoft Dynamics AX Application Object Tree (AOT).

    public void AOTrun()

### Method AOTedit

Opens the appropriate editor for this node.

    public void AOTedit([int Line], [int Column])

#### Parameters

Line  
The column of the cursor position; optional.

<!-- -->

Column  
The column of the cursor position; optional.

#### Remarks

If the node is a method, the code editor opens. If the node is a documentation object, the Help editor opens.

