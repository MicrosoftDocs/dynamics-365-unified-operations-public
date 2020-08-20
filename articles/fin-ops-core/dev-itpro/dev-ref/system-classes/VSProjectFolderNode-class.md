---
title: VSProjectFolderNode class
description: This topic describes the VSProjectFolderNode class.
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

# Class VSProjectFolderNode

[!include [banner](../../includes/banner.md)]

```xpp
class VSProjectFolderNode extends TreeNode
```

The VSProjectFolderNode class represents folders in the Microsoft Visual Studio project nodes in the Application Object Tree (AOT).

## Remarks

## Examples

## Methods

| Method                                                                                       | Description                                                                                              |
|----------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| public str AOTgetSource()                                                                    | Returns the source code of this node.                                                                    |
| public VSProjectFileNode createFileNode(str name)                                            | Creates a new instance of the VSProjectFileNode class as a child of this VSProjectFolderNode instance.   |
| public VSProjectFolderNode createFolderNode(str name)                                        | Creates a new instance of the VSProjectFolderNode class as a child of this VSProjectFolderNode instance. |
| public VSProjectLinkNode createLinkNode(str name, str aotPath, \[boolean createLinkedNode\]) | Creates a new instance of the VSProjectLinkNode class as a child of this VSProjectFolderNode instance.   |
| public BinData getFileData()                                                                 |                                                                                                          |
| ::public static void notifyFileUpdated(TreeNode node)                                        |                                                                                                          |
| ::public static void notifyFileDeleted(TreeNode node, str aotPath)                           |                                                                                                          |
| public void setFileData(BinData data)                                                        |                                                                                                          |
| public void AOTsetSource(str source, \[boolean isStatic\])                                   | Sets the source code of this node.                                                                       |
| public void getFile(str fileName)                                                            |                                                                                                          |
| ::public static void notifyFileCreated(TreeNode node)                                        |                                                                                                          |
| ::public static void notifyFileRenamed(TreeNode node, str oldName)                           |                                                                                                          |
| public void setFile(str fileName)                                                            |                                                                                                          |

## Method AOTgetSource

Returns the source code of this node.

```xpp
public str AOTgetSource()
```

### Return Value - AOTgetSource

The string that contains source code, if there is any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Remarks - AOTgetSource

This function is overridden by nodes that have source code.

## Method createFileNode

Creates a new instance of the VSProjectFileNode class as a child of this VSProjectFolderNode instance.

```xpp
public VSProjectFileNode createFileNode(str name)
```

### Parameters - createFileNode

name  
The name of the file node.

### Return Value - createFileNode

The new instance of the VSProjectFileNode class.

## Method createFolderNode

Creates a new instance of the VSProjectFolderNode class as a child of this VSProjectFolderNode instance.

```xpp
public VSProjectFolderNode createFolderNode(str name)
```

### Parameters - createFolderNode

name  
The name of the folder node.

### Return Value - createFolderNode

The new instance of the VSProjectFolderNode class.

## Method createLinkNode

Creates a new instance of the VSProjectLinkNode class as a child of this VSProjectFolderNode instance.

```xpp
public VSProjectLinkNode createLinkNode(str name, str aotPath, [boolean createLinkedNode])
```

### Parameters - createLinkNode

name  

<!-- -->

aotPath  

<!-- -->

createLinkedNode  

### Return Value - createLinkNode

The new instance of the VSProjectLinkNode class.

## Method getFileData

```xpp
public BinData getFileData()
```

### Return Value - getFileData

## Method notifyFileUpdated

```xpp
public static void notifyFileUpdated(TreeNode node)
```

### Parameters - notifyFileUpdated

node  

## Method notifyFileDeleted

```xpp
public static void notifyFileDeleted(TreeNode node, str aotPath)
```

### Parameters - notifyFileDeleted

node  

<!-- -->

aotPath  

## Method setFileData

```xpp
public void setFileData(BinData data)
```

### Parameters - setFileData

data  

## Method AOTsetSource

Sets the source code of this node.

```xpp
public void AOTsetSource(str source, [boolean isStatic])
```

### Parameters - AOTsetSource

source  
The value that specifies whether the method is static; optional.

<!-- -->

isStatic  
The value that specifies whether the method is static; optional.

### Remarks - AOTsetSource

This method is overridden by nodes that have source code.

## Method getFile

```xpp
public void getFile(str fileName)
```

### Parameters - getFile

fileName  

## Method notifyFileCreated

```xpp
public static void notifyFileCreated(TreeNode node)
```

### Parameters - notifyFileCreated

node  

## Method notifyFileRenamed

```xpp
public static void notifyFileRenamed(TreeNode node, str oldName)
```

### Parameters - notifyFileRenamed

node  

<!-- -->

oldName  

## Method setFile

```xpp
public void setFile(str fileName)
```

### Parameters - setFile

fileName  

