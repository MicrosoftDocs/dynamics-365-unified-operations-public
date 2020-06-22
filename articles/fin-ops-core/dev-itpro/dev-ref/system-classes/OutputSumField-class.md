---
title: OutputSumField class
description: This topic describes the OutputSumField class.
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

# Class OutputSumField

[!include [banner](../../includes/banner.md)]

```xpp
class OutputSumField extends OutputField
```

## Remarks

## Examples

## Methods

| Method                | Description                                             |
|-----------------------|---------------------------------------------------------|
| public str toString() | Returns a string that represents the current object.    |
| public Real value()   |                                                         |
| public void new()     | Initializes a new instance of the OutputSumField class. |

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and the type of the method, such as instance or static.

## Method value

```xpp
public Real value()
```

### Return Value - value

## Method new

Initializes a new instance of the OutputSumField class.

```xpp
public void new()
```

