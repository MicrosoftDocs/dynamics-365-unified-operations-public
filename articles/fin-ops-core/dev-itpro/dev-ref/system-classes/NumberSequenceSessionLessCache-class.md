---
title: NumberSequenceSessionLessCache class
description: This topic describes the NumberSequenceSessionLessCache class.
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

# Class NumberSequenceSessionLessCache

[!include [banner](../../includes/banner.md)]

```xpp
class NumberSequenceSessionLessCache extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                         | Description                                                             |
|--------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| public int getNumFromCache(Common numbersequencetable)                         |                                                                         |
| public int valueLastNumFromCache(Int64 numbersequecerecordid)                  |                                                                         |
| public int valueNextNumFromCache(Int64 numbersequecerecordid)                  |                                                                         |
| public void flushCache(Int64 numbersequecerecordid)                            |                                                                         |
| public void fillCache(Int64 numbersequecerecordid, int nextRec, int blockSize) |                                                                         |
| public void new()                                                              | Initializes a new instance of the NumberSequenceSessionLessCache class. |

## Method getNumFromCache

```xpp
public int getNumFromCache(Common numbersequencetable)
```

### Parameters - getNumFromCache

numbersequencetable  

### Return Value - getNumFromCache

## Method valueLastNumFromCache

```xpp
public int valueLastNumFromCache(Int64 numbersequecerecordid)
```

### Parameters - valueLastNumFromCache

numbersequecerecordid  

### Return Value - valueLastNumFromCache

## Method valueNextNumFromCache

```xpp
public int valueNextNumFromCache(Int64 numbersequecerecordid)
```

### Parameters - valueNextNumFromCache

numbersequecerecordid  

### Return Value - valueNextNumFromCache

## Method flushCache

```xpp
public void flushCache(Int64 numbersequecerecordid)
```

### Parameters - flushCache

numbersequecerecordid  

## Method fillCache

```xpp
public void fillCache(Int64 numbersequecerecordid, int nextRec, int blockSize)
```

### Parameters - fillCache

numbersequecerecordid  

<!-- -->

nextRec  

<!-- -->

blockSize  

## Method new

Initializes a new instance of the NumberSequenceSessionLessCache class.

```xpp
public void new()
```


