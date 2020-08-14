---
title: VSProjectNode class
description: This topic describes the VSProjectNode class.
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

# Class VSProjectNode

[!include [banner](../../includes/banner.md)]

```xpp
class VSProjectNode extends xResourceNode
```

The VSProjectNode class represents projects in the Microsoft Visual Studio project nodes in the Application Object Tree (AOT).

## Remarks

## Examples

## Methods

| Method                                                                | Description                                                                                       |
|-----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| public container extract(\[str path\], \[boolean extractReferenced\]) | Extracts the whole project to disk.                                                               |
| public VSProjectFolderNode getContentNode()                           | Gets the content VSProjectFolderNode object that contains the Visual Studio project files.        |
| public DeployTo getDeployTo()                                         | Gets value of the deployTo property.                                                              |
| public VSProjectFolderNode getOutputNode()                            | Gets the output VSProjectFolderNode object that contains the Visual Studio project output files.  |
| public VSProjectFileNode getPrimaryOutputNode()                       | Gets the VSProjectFileNode object that represent the primary output of the Visual Studio project. |
| public str getPrimaryTargetFileName()                                 | Gets the primary target file name of the Visual Studio project.                                   |
| public Map getProxies()                                               | Gets the proxies in this project.                                                                 |
| public container getProxiesContainer()                                | Gets the proxies in this project.                                                                 |
| public str getReferencedProjectsInAOT()                               | Gets the AOT paths of the projects that are referenced by this Visual Studio project.             |
| public str referencedProjects(\[str value\])                          |                                                                                                   |
| public void setPrimaryTargetFileName(str targetFileName)              | Sets the primary target file name of the Visual Studio project.                                   |
| public void extractToSpecificDir(str directory)                       |                                                                                                   |
| public void setDeployTo(DeployTo deployTo)                            | Sets the value of the deployTo property.                                                          |

## Method extract

Extracts the whole project to disk.

```xpp
public container extract([str path], [boolean extractReferenced])
```

### Parameters - extract

path  
A Boolean value that determines whether to extract the referenced projects.

<!-- -->

extractReferenced  
A Boolean value that determines whether to extract the referenced projects.

### Return Value - extract

A list of paths where the project was extracted.

## Method getContentNode

Gets the content VSProjectFolderNode object that contains the Visual Studio project files.

```xpp
public VSProjectFolderNode getContentNode()
```

### Return Value - getContentNode

The content VSProjectFolderNode object that contains the Visual Studio project files.

## Method getDeployTo

Gets value of the deployTo property.

```xpp
public DeployTo getDeployTo()
```

### Return Value - getDeployTo

The deployTo property value.

## Method getOutputNode

Gets the output VSProjectFolderNode object that contains the Visual Studio project output files.

```xpp
public VSProjectFolderNode getOutputNode()
```

### Return Value - getOutputNode

The output VSProjectFolderNode object that contains the Visual Studio project output files.

## Method getPrimaryOutputNode

Gets the VSProjectFileNode object that represent the primary output of the Visual Studio project.

```xpp
public VSProjectFileNode getPrimaryOutputNode()
```

### Return Value - getPrimaryOutputNode

A VSProjectFileNode object that represent the primary output of the Visual Studio project.

## Method getPrimaryTargetFileName

Gets the primary target file name of the Visual Studio project.

```xpp
public str getPrimaryTargetFileName()
```

### Return Value - getPrimaryTargetFileName

The primary target file name of the Visual Studio project.

## Method getProxies

Gets the proxies in this project.

```xpp
public Map getProxies()
```

### Return Value - getProxies

A map that contains the Class, Enum, and Table keys. Each key contains a list of proxies.

## Method getProxiesContainer

Gets the proxies in this project.

```xpp
public container getProxiesContainer()
```

### Return Value - getProxiesContainer

A container that holds the packed representation of a map that contains the Class, Enum, and Table keys. Each key contains a list of proxies.

## Method getReferencedProjectsInAOT

Gets the AOT paths of the projects that are referenced by this Visual Studio project.

```xpp
public str getReferencedProjectsInAOT()
```

### Return Value - getReferencedProjectsInAOT

A list of AOT paths of the projects that are referenced by this Visual Studio project.

## Method referencedProjects

```xpp
public str referencedProjects([str value])
```

### Parameters - referencedProjects

value  

### Return Value - referencedProjects

## Method setPrimaryTargetFileName

Sets the primary target file name of the Visual Studio project.

```xpp
public void setPrimaryTargetFileName(str targetFileName)
```

### Parameters - setPrimaryTargetFileName

targetFileName  
The primary target file name of the Visual Studio project.

## Method extractToSpecificDir

```xpp
public void extractToSpecificDir(str directory)
```

### Parameters - extractToSpecificDir

directory  

## Method setDeployTo

Sets the value of the deployTo property.

```xpp
public void setDeployTo(DeployTo deployTo)
```

### Parameters - setDeployTo

deployTo  
The deployTo property value.

