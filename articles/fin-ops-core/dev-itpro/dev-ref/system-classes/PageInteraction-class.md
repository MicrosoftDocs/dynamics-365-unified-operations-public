---
title: PageInteraction class
description: This topic describes the PageInteraction class.
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

# Class PageInteraction

[!include [banner](../../includes/banner.md)]

```xpp
class PageInteraction extends Object
```

The PageInteraction class provides functionality for interacting with a list page.

## Remarks

## Examples

## Methods

| Method                                           | Description                                                        |
|--------------------------------------------------|--------------------------------------------------------------------|
| public Page page()                               | Gets the ListPage instance.                                        |
| public void tabChanged(container activeTabNames) |                                                                    |
| public void new(Page page)                       | Creates a new PageInteraction object that operates on a list page. |

## Method page

Gets the ListPage instance.

```xpp
public Page page()
```

### Return Value - page

Returns the ListPage instance for this PageInteraction instance.

## Method tabChanged

```xpp
public void tabChanged(container activeTabNames)
```

### Parameters - tabChanged

activeTabNames  

## Method new

Creates a new PageInteraction object that operates on a list page.

```xpp
public void new(Page page)
```

### Parameters - new

page  

