---
title: ProjectGroupNode class
description: This topic describes the ProjectGroupNode class.
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

# Class ProjectGroupNode

[!include [banner](../../includes/banner.md)]

```xpp
class ProjectGroupNode extends TreeNode
```

The ProjectGroupNode class represents a group node within a project.

## Remarks

This class enables you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before you call this API.

## Examples

## Methods

| Method                                                                                       | Description                                                                                                                                   |
|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public TreeNode findGroupMember(str name, UtilElementType type, \[boolean searchSubgroups\]) | Searches the projectGroup for a specific element. It can be used to search a specific group or the whole project.                             |
| public str groupMask(\[str value\])                                                          |                                                                                                                                               |
| public str name(\[str value\])                                                               | Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object. |
| public boolean preventEditProperties(\[boolean value\])                                      |                                                                                                                                               |
| public GroupNodeType projectGroupType(\[GroupNodeType value\])                               |                                                                                                                                               |
| public void addUtilNode(UtilElementType type, str name)                                      | Adds a node to the projectGroup.                                                                                                              |
| public void addNode(TreeNode node)                                                           | Adds an existing node to the projectGroup.                                                                                                    |

## Method findGroupMember

Searches the projectGroup for a specific element. It can be used to search a specific group or the whole project.

```xpp
public TreeNode findGroupMember(str name, UtilElementType type, [boolean searchSubgroups])
```

### Parameters - findGroupMember

name  
A boolean flag that determines whether the search should be recursive (whether to search subprojects); optional.

<!-- -->

type  
A boolean flag that determines whether the search should be recursive (whether to search subprojects); optional.

<!-- -->

searchSubgroups  
A boolean flag that determines whether the search should be recursive (whether to search subprojects); optional.

### Return Value - findGroupMember

The first object that fits the criteria; returns nullNothingnullptrunita null reference (Nothing in Visual Basic) if no object is found.

### Remarks - findGroupMember

This method is also found on ProjectNode.

## Method groupMask

```xpp
public str groupMask([str value])
```

### Parameters - groupMask

value  

### Return Value - groupMask

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
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

## Method preventEditProperties

```xpp
public boolean preventEditProperties([boolean value])
```

### Parameters - preventEditProperties

value  

### Return Value - preventEditProperties

## Method projectGroupType

```xpp
public GroupNodeType projectGroupType([GroupNodeType value])
```

### Parameters - projectGroupType

value  

### Return Value - projectGroupType

## Method addUtilNode

Adds a node to the projectGroup.

```xpp
public void addUtilNode(UtilElementType type, str name)
```

### Parameters - addUtilNode

type  
The name of the node.

<!-- -->

name  
The name of the node.

### Remarks - addUtilNode

This method also is found on the ProjectNode class.

## Method addNode

Adds an existing node to the projectGroup.

```xpp
public void addNode(TreeNode node)
```

### Parameters - addNode

node  
The node to add.

