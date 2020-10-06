---
title: IISViewState class
description: This topic describes the IISViewState class.
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

# Class IISViewState

[!include [banner](../../includes/banner.md)]

```xpp
class IISViewState extends Object
```

## Remarks

## Examples

## Methods

| Method                                         | Description                                           |
|------------------------------------------------|-------------------------------------------------------|
| public boolean viewStateContains(str key)      |                                                       |
| public str viewStateItem(str key, \[str val\]) |                                                       |
| public void finalize()                         |                                                       |
| public void viewStateDelete(str key)           |                                                       |
| public void new()                              | Initializes a new instance of the IISViewState class. |

## Method viewStateContains

```xpp
public boolean viewStateContains(str key)
```

### Parameters - viewStateContains

key  

### Return Value - viewStateContains

## Method viewStateItem

```xpp
public str viewStateItem(str key, [str val])
```

### Parameters - viewStateItem

key  

<!-- -->

val  

### Return Value - viewStateItem

## Method finalize

```xpp
public void finalize()
```

## Method viewStateDelete

```xpp
public void viewStateDelete(str key)
```

### Parameters - viewStateDelete

key  

## Method new

Initializes a new instance of the IISViewState class.

```xpp
public void new()
```

