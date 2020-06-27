---
title: Enumerator class
description: This topic describes the Enumerator class.
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

# Class Enumerator

[!include [banner](../../includes/banner.md)]

```xpp
class Enumerator extends Object
```

## Remarks

## Examples

## Methods

| Method                        | Description                                          |
|-------------------------------|------------------------------------------------------|
| public AnyType current()      |                                                      |
| public str definitionString() |                                                      |
| public boolean moveNext()     |                                                      |
| public str toString()         | Returns a string that represents the current object. |
| public void reset()           |                                                      |

## Method current

```xpp
public AnyType current()
```

### Return Value - current

## Method definitionString

```xpp
public str definitionString()
```

### Return Value - definitionString

## Method moveNext

```xpp
public boolean moveNext()
```

### Return Value - moveNext

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

## Method reset

```xpp
public void reset()
```

