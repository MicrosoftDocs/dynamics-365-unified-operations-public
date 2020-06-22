---
title: FormObjectSetPagingParamsChangedEvtArgs class
description: This topic describes the FormObjectSetPagingParamsChangedEvtArgs class.
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

# Class FormObjectSetPagingParamsChangedEvtArgs

[!include [banner](../../includes/banner.md)]

```xpp
class FormObjectSetPagingParamsChangedEvtArgs extends ManagedEventArgs
```

## Remarks

## Examples

## Methods

| Method                                                                  | Description                                               |
|-------------------------------------------------------------------------|-----------------------------------------------------------|
| public int pageSize()                                                   |                                                           |
| public boolean pagingEnabled()                                          |                                                           |
| public int startRowIndex()                                              |                                                           |
| public void finalize()                                                  |                                                           |
| public void new(boolean pagingEnabled, int startRowIndex, int pageSize) | Initializes a new instance of the ManagedEventArgs class. |

## Method pageSize

```xpp
public int pageSize()
```

### Return Value - pageSize

## Method pagingEnabled

```xpp
public boolean pagingEnabled()
```

### Return Value - pagingEnabled

## Method startRowIndex

```xpp
public int startRowIndex()
```

### Return Value - startRowIndex

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the ManagedEventArgs class.

```xpp
public void new(boolean pagingEnabled, int startRowIndex, int pageSize)
```

### Parameters - new

pagingEnabled  

<!-- -->

startRowIndex  

<!-- -->

pageSize  

