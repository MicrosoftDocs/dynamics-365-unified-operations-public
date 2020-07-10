---
title: ControlNode class
description: This topic describes the ControlNode class.
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

# Class ControlNode

[!include [banner](../../includes/banner.md)]

```xpp
class ControlNode extends TreeNode
```

The ControlNode class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                         | Description                                       |
|------------------------------------------------|---------------------------------------------------|
| public void new(str name, \[TreeNode parent\]) | Initializes a new instance of the TreeNode class. |

## Method new

Initializes a new instance of the TreeNode class.

```xpp
public void new(str name, [TreeNode parent])
```

### Parameters - new

name  

<!-- -->

parent  

