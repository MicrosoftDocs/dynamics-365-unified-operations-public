---
title: VSProjectsNode class
description: This topic describes the VSProjectsNode class.
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

# Class VSProjectsNode

[!include [banner](../../includes/banner.md)]

```xpp
class VSProjectsNode extends xResourceNode
```

The VSProjectNode class is the root of the Microsoft Visual Studio project nodes in the Application Object Tree (AOT).

## Remarks

## Examples

## Methods

| Method                                                                                            | Description                                                                                |
|---------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| public TreeNode AOTfindChild(str name, \[int nodeType\])                                          | Finds the specified child node of this node.                                               |
| public VSProjectNode createProjectNode(str name, str projectTypesString, \[boolean virtualNode\]) | Creates a new instance of the VSProjectNode class.                                         |
| public container getProjectsDeployingTo(DeployTo deployTo)                                        | Gets a list of VSProjectNode objects that have the specified deployTo property.            |
| public container getProjectsModifiedAfter(DateTime timestamp)                                     | Gets a list of VSProjectNode objects that were modified after the specified date and time. |
| public VSProjectTypeNode getTypeNodeFromGuid(str projectTypesString)                              |                                                                                            |
| public Object getVSProjectNodeObservable()                                                        | Gets the VSProjectNodeObservable object.                                                   |
| public void AOTrefresh()                                                                          | Updates the node with the latest changes to the .aod file.                                 |

## Method AOTfindChild

Finds the specified child node of this node.

```xpp
public TreeNode AOTfindChild(str name, [int nodeType])
```

### Parameters - AOTfindChild

name  

<!-- -->

nodeType  

### Return Value - AOTfindChild

The specified tree node.

## Method createProjectNode

Creates a new instance of the VSProjectNode class.

```xpp
public VSProjectNode createProjectNode(str name, str projectTypesString, [boolean virtualNode])
```

### Parameters - createProjectNode

name  
A Boolean value that indicates whether the node is created only in memory. In this case, the node will not be persisted in the Finance and Operations Store.

<!-- -->

projectTypesString  
A Boolean value that indicates whether the node is created only in memory. In this case, the node will not be persisted in the Finance and Operations Store.

<!-- -->

virtualNode  
A Boolean value that indicates whether the node is created only in memory. In this case, the node will not be persisted in the Finance and Operations Store.

### Return Value - createProjectNode

The VSProjectNode object that is created.

## Method getProjectsDeployingTo

Gets a list of VSProjectNode objects that have the specified deployTo property.

```xpp
public container getProjectsDeployingTo(DeployTo deployTo)
```

### Parameters - getProjectsDeployingTo

deployTo  
The value of the deployTo property.

### Return Value - getProjectsDeployingTo

A list of VSProjectNode objects.

## Method getProjectsModifiedAfter

Gets a list of VSProjectNode objects that were modified after the specified date and time.

```xpp
public container getProjectsModifiedAfter(DateTime timestamp)
```

### Parameters - getProjectsModifiedAfter

timestamp  
The date and time as a DB\_DATETIME\_TYPE value.

### Return Value - getProjectsModifiedAfter

A list of VSProjectNode objects.

## Method getTypeNodeFromGuid

```xpp
public VSProjectTypeNode getTypeNodeFromGuid(str projectTypesString)
```

### Parameters - getTypeNodeFromGuid

projectTypesString  

### Return Value - getTypeNodeFromGuid

## Method getVSProjectNodeObservable

Gets the VSProjectNodeObservable object.

```xpp
public Object getVSProjectNodeObservable()
```

### Return Value - getVSProjectNodeObservable

The VSProjectNodeObservable object.

### Remarks - getVSProjectNodeObservable

Observers can register with this and get notified of CRUD operations on Visual Studio projects.

## Method AOTrefresh

Updates the node with the latest changes to the .aod file.

```xpp
public void AOTrefresh()
```

