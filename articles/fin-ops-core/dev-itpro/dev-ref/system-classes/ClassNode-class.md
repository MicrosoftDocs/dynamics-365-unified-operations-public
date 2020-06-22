---
title: ClassNode class
description: This topic describes the ClassNode class.
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

# Class ClassNode

[!include [banner](../../includes/banner.md)]


```xpp
class ClassNode extends TreeNode
```

The ClassNode class is a specialization of the TreeNode class that represents a class in the Application Object Tree (AOT).

## Remarks

This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                            | Description                                                                                                                                   |
|---------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public TreeNode AOToverrideMethod(str methodName) |                                                                                                                                               |
| public str changedBy(\[str value\])               | Gets or sets the name of the user who last changed the application object.                                                                    |
| public Date changedDate(\[Date value\])           | Gets or sets the date an application object was last changed.                                                                                 |
| public str changedTime(\[str value\])             | Gets or sets the time an application object was last changed.                                                                                 |
| public str createdBy(\[str value\])               | Gets or sets the name of the user who created the application object.                                                                         |
| public Date creationDate(\[Date value\])          | Gets or sets the date an application object was created.                                                                                      |
| public str creationTime(\[str value\])            |                                                                                                                                               |
| public str extends(\[str value\])                 |                                                                                                                                               |
| public int iD(\[int value\])                      |                                                                                                                                               |
| public boolean isDetached()                       |                                                                                                                                               |
| public int legacyId(\[int value\])                |                                                                                                                                               |
| public str name(\[str value\])                    | Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object. |
| public Guid origin(\[Guid value\])                |                                                                                                                                               |
| public int runOn(\[int value\])                   |                                                                                                                                               |
| public void AOTedit(\[int Line\], \[int Column\]) | Opens the class so that it can be modified in the editor.                                                                                     |

## Method AOToverrideMethod

```xpp
public TreeNode AOToverrideMethod(str methodName)
```

### Parameters - AOToverrideMethod

methodName  

### Return Value - AOToverrideMethod

## Method changedBy

Gets or sets the name of the user who last changed the application object.

```xpp
public str changedBy([str value])
```

### Parameters - changedBy

value  

### Return Value - changedBy

The name of the user.

## Method changedDate

Gets or sets the date an application object was last changed.

```xpp
public Date changedDate([Date value])
```

### Parameters - changedDate

value  

### Return Value - changedDate

The date an application object was last changed.

## Method changedTime

Gets or sets the time an application object was last changed.

```xpp
public str changedTime([str value])
```

### Parameters - changedTime

value  

### Return Value - changedTime

The time an application object was last changed.

## Method createdBy

Gets or sets the name of the user who created the application object.

```xpp
public str createdBy([str value])
```

### Parameters - createdBy

value  

### Return Value - createdBy

The name of the user.

## Method creationDate

Gets or sets the date an application object was created.

```xpp
public Date creationDate([Date value])
```

### Parameters - creationDate

value  

### Return Value - creationDate

The date an application object was created.

## Method creationTime

```xpp
public str creationTime([str value])
```

### Parameters - creationTime

value  

### Return Value - creationTime

## Method extends

```xpp
public str extends([str value])
```

### Parameters - extends

value  

### Return Value - extends

## Method iD

```xpp
public int iD([int value])
```

### Parameters - iD

value  

### Return Value - iD

## Method isDetached

```xpp
public boolean isDetached()
```

### Return Value - isDetached

## Method legacyId

```xpp
public int legacyId([int value])
```

### Parameters - legacyId

value  

### Return Value - legacyId

## Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

The name that is used in the code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Does not exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumerations, classes, and so on.

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method runOn

```xpp
public int runOn([int value])
```

### Parameters - runOn

value  

### Return Value - runOn

## Method AOTedit

Opens the class so that it can be modified in the editor.

```xpp
public void AOTedit([int Line], [int Column])
```

### Parameters - AOTedit

Line  
A value that is ignored; optional.

<!-- -->

Column  
A value that is ignored; optional.

### Remarks - AOTedit

All methods are loaded into the editor. The arguments are included in the signature for backward compatibility only; they are ignored.

### Examples - AOTedit

```xpp
static void example() 
{ 
    ClassNode classNode; 
```

```xpp
    classNode = infolog.findNode('\Classes\SysClassWizard'); 
    classNode.AOTedit(); 
}
```

