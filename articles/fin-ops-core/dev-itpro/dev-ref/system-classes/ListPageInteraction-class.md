---
title: ListPageInteraction class
description: This topic describes the ListPageInteraction class.
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

# Class ListPageInteraction

[!include [banner](../../includes/banner.md)]

```xpp
class ListPageInteraction extends PageInteraction
```

## Remarks

## Examples

## Methods

| Method                                           | Description                                                   |
|--------------------------------------------------|---------------------------------------------------------------|
| public ListPage listPage()                       |                                                               |
| public void tabChanged(container activeTabNames) | Called when the active tab is changed.                        |
| public void initializing()                       |                                                               |
| public void initialized()                        |                                                               |
| public void selectionChanged()                   |                                                               |
| public void initializeQuery(Query query)         |                                                               |
| public void new(ListPage listPage)               | Creates a new PageInteraction object operating on a listPage. |

## Method listPage

```xpp
public ListPage listPage()
```

### Return Value - listPage

## Method tabChanged

Called when the active tab is changed.

```xpp
public void tabChanged(container activeTabNames)
```

### Parameters - tabChanged

activeTabNames  
A container containing the names of the active tabs.

## Method initializing

```xpp
public void initializing()
```

## Method initialized

```xpp
public void initialized()
```

## Method selectionChanged

```xpp
public void selectionChanged()
```

## Method initializeQuery

```xpp
public void initializeQuery(Query query)
```

### Parameters - initializeQuery

query  

## Method new

Creates a new PageInteraction object operating on a listPage.

```xpp
public void new(ListPage listPage)
```

### Parameters - new

listPage  
The specified ListPage object.

