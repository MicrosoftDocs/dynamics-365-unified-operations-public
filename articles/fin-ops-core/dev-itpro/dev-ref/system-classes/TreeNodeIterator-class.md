---
title: TreeNodeIterator class
description: This topic describes the TreeNodeIterator class.
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

# Class TreeNodeIterator

[!include [banner](../../includes/banner.md)]

```xpp
class TreeNodeIterator extends Object
```

The TreeNodeIterator class traverses the child nodes of a tree node.

## Remarks

## Examples

The following example prints the names of all child nodes of the root node.

```xpp
static void example()  
{ 
    treeNode myTreeNode; 
    xInfo xi = new xInfo(); 
    void printChildNames (treeNode t) 
    { 
        treeNode child; 
        treenodeIterator it; 
        it = t.AOTiterator(); 
        child = it.next(); 
        while (child) 
        { 
            print child.treeNodeName(); 
            child = it.next(); 
        } 
    } 
    myTreeNode = xi.rootNode(); 
    printChildNames(myTreeNode); 
    pause; 
}
```

## Methods

| Method                 | Description                                                                                            |
|------------------------|--------------------------------------------------------------------------------------------------------|
| public TreeNode next() | Retrieves the next element in the list of child nodes.                                                 |
| public void reset()    | Resets the iterator so that the next call to the next method returns the first child node in the list. |

## Method next

Retrieves the next element in the list of child nodes.

```xpp
public TreeNode next()
```

### Return Value - next

The next child node in the tree.

## Method reset

Resets the iterator so that the next call to the next method returns the first child node in the list.

```xpp
public void reset()
```

