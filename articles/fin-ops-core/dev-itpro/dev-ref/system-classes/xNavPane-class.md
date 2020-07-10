---
title: xNavPane class
description: This topic describes the xNavPane class.
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

# Class xNavPane

[!include [banner](../../includes/banner.md)]

```xpp
class xNavPane extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                | Description                                       |
|-------------------------------------------------------------------------------------------------------|---------------------------------------------------|
| public boolean collapseFavoriteNode(str path)                                                         |                                                   |
| public boolean collapseNode(str path)                                                                 |                                                   |
| public boolean expandFavoriteNode(str path)                                                           |                                                   |
| public boolean expandNode(str path)                                                                   |                                                   |
| public boolean favPaneVisible(\[boolean value\])                                                      |                                                   |
| public container getButtons()                                                                         |                                                   |
| public str getCurrMenuName()                                                                          |                                                   |
| public TreeNode getSelectedFavoriteNode()                                                             |                                                   |
| public TreeNode getSelectedNode()                                                                     |                                                   |
| public boolean navPaneVisible(\[boolean value\])                                                      |                                                   |
| public boolean runFavoriteNode(str path)                                                              |                                                   |
| public boolean runNode(str path)                                                                      |                                                   |
| public str selectedFavoriteGroup(\[str groupName\])                                                   |                                                   |
| public str selectedGroup(\[str groupName\])                                                           |                                                   |
| public boolean setSelectedFavoriteNode(str path)                                                      |                                                   |
| public boolean setSelectedNode(str path)                                                              |                                                   |
| public void refreshFavorites(\[str selectFavoriteGroup\], \[int workspaceNum\], \[boolean saveToDB\]) |                                                   |
| public void setCurrMenuButtons(container buttons)                                                     |                                                   |
| public void loadStartupButtons()                                                                      |                                                   |
| public void new()                                                                                     | Initializes a new instance of the xNavPane class. |

## Method collapseFavoriteNode

```xpp
public boolean collapseFavoriteNode(str path)
```

### Parameters - collapseFavoriteNode

path  

### Return Value - collapseFavoriteNode

## Method collapseNode

```xpp
public boolean collapseNode(str path)
```

### Parameters - collapseNode

path  

### Return Value - collapseNode

## Method expandFavoriteNode

```xpp
public boolean expandFavoriteNode(str path)
```

### Parameters - expandFavoriteNode

path  

### Return Value - expandFavoriteNode

## Method expandNode

```xpp
public boolean expandNode(str path)
```

### Parameters - expandNode

path  

### Return Value - expandNode

## Method favPaneVisible

```xpp
public boolean favPaneVisible([boolean value])
```

### Parameters - favPaneVisible

value  

### Return Value - favPaneVisible

## Method getButtons

```xpp
public container getButtons()
```

### Return Value - getButtons

## Method getCurrMenuName

```xpp
public str getCurrMenuName()
```

### Return Value - getCurrMenuName

## Method getSelectedFavoriteNode

```xpp
public TreeNode getSelectedFavoriteNode()
```

### Return Value - getSelectedFavoriteNode

## Method getSelectedNode

```xpp
public TreeNode getSelectedNode()
```

### Return Value - getSelectedNode

## Method navPaneVisible

```xpp
public boolean navPaneVisible([boolean value])
```

### Parameters - navPaneVisible

value  

### Return Value - navPaneVisible

## Method runFavoriteNode

```xpp
public boolean runFavoriteNode(str path)
```

### Parameters - runFavoriteNode

path  

### Return Value - runFavoriteNode

## Method runNode

```xpp
public boolean runNode(str path)
```

### Parameters - runNode

path  

### Return Value - runNode

## Method selectedFavoriteGroup

```xpp
public str selectedFavoriteGroup([str groupName])
```

### Parameters - selectedFavoriteGroup

groupName  

### Return Value - selectedFavoriteGroup

## Method selectedGroup

```xpp
public str selectedGroup([str groupName])
```

### Parameters - selectedGroup

groupName  

### Return Value - selectedGroup

## Method setSelectedFavoriteNode

```xpp
public boolean setSelectedFavoriteNode(str path)
```

### Parameters - setSelectedFavoriteNode

path  

### Return Value - setSelectedFavoriteNode

## Method setSelectedNode

```xpp
public boolean setSelectedNode(str path)
```

### Parameters - setSelectedNode

path  

### Return Value - setSelectedNode

## Method refreshFavorites

```xpp
public void refreshFavorites([str selectFavoriteGroup], [int workspaceNum], [boolean saveToDB])
```

### Parameters - refreshFavorites

selectFavoriteGroup  

<!-- -->

workspaceNum  

<!-- -->

saveToDB  

## Method setCurrMenuButtons

```xpp
public void setCurrMenuButtons(container buttons)
```

### Parameters - setCurrMenuButtons

buttons  

## Method loadStartupButtons

```xpp
public void loadStartupButtons()
```

## Method new

Initializes a new instance of the xNavPane class.

```xpp
public void new()
```

