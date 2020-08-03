---
title: VSItemNode class
description: This topic describes the VSItemNode class.
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

# Class VSItemNode

[!include [banner](../../includes/banner.md)]

```xpp
class VSItemNode extends TreeNode
```

The VSItemNode class is a base class for Microsoft Visual Studio project nodes in the Application Object Tree (AOT).

## Remarks

## Examples

## Methods

| Method                                                             | Description                                          |
|--------------------------------------------------------------------|------------------------------------------------------|
| public str AOTgetSource()                                          | Returns the source code of this node.                |
| public BinData getFileData()                                       |                                                      |
| ::public static void notifyFileDeleted(TreeNode node, str aotPath) | Notifies listeners that a file has been deleted.     |
| ::public static void notifyFileUpdated(TreeNode node)              | Notifies listeners that a file has been updated.     |
| public void setFileData(BinData data)                              |                                                      |
| public void AOTsetSource(str source, \[boolean isStatic\])         | Sets the source code of this node.                   |
| public void getFile(str fileName)                                  |                                                      |
| ::public static void notifyFileCreated(TreeNode node)              | Notifies listeners that a new file has been created. |
| ::public static void notifyFileRenamed(TreeNode node, str oldName) | Notifies listeners that a file has been renamed.     |
| public void setFile(str fileName)                                  |                                                      |

## Method AOTgetSource

Returns the source code of this node.

```xpp
public str AOTgetSource()
```

### Return Value - AOTgetSource

The string that contains the source code, if there is any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Remarks - AOTgetSource

This function is overridden by nodes that have source code.

## Method getFileData

```xpp
public BinData getFileData()
```

### Return Value - getFileData

## Method notifyFileDeleted

Notifies listeners that a file has been deleted.

```xpp
public static void notifyFileDeleted(TreeNode node, str aotPath)
```

### Parameters - notifyFileDeleted

node  
The AOT path of the file.

<!-- -->

aotPath  
The AOT path of the file.

## Method notifyFileUpdated

Notifies listeners that a file has been updated.

```xpp
public static void notifyFileUpdated(TreeNode node)
```

### Parameters - notifyFileUpdated

node  
The node that has been updated.

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

Notifies listeners that a new file has been created.

```xpp
public static void notifyFileCreated(TreeNode node)
```

### Parameters - notifyFileCreated

node  
The node that has been created.

## Method notifyFileRenamed

Notifies listeners that a file has been renamed.

```xpp
public static void notifyFileRenamed(TreeNode node, str oldName)
```

### Parameters - notifyFileRenamed

node  
The old name of the file.

<!-- -->

oldName  
The old name of the file.

## Method setFile

```xpp
public void setFile(str fileName)
```

### Parameters - setFile

fileName  

