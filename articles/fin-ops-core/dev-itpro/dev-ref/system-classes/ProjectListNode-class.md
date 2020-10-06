---
title: ProjectListNode class
description: This topic describes the ProjectListNode class.
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

# Class ProjectListNode

[!include [banner](../../includes/banner.md)]

```xpp
class ProjectListNode extends TreeNode
```

The ProjectListNode class corresponds to the Private and Shared lists of projects in the project overview window. Use the ProjectListNode.addProject method to add a new project from X++ code.

## Remarks

This class enables you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before calling this API.

## Examples

## Methods

| Method                                                               | Description                     |
|----------------------------------------------------------------------|---------------------------------|
| public ProjectNode addProject(str projectName, \[str projectClass\]) | Adds a new project to the list. |

## Method addProject

Adds a new project to the list.

```xpp
public ProjectNode addProject(str projectName, [str projectClass])
```

### Parameters - addProject

projectName  
The name of the projecttype; optional. This should be the name of a class associated with the project (see the setProjectClass method). If no value is supplied, the project becomes a standard project.

<!-- -->

projectClass  
The name of the projecttype; optional. This should be the name of a class associated with the project (see the setProjectClass method). If no value is supplied, the project becomes a standard project.

### Return Value - addProject

The newly added projectNode.

