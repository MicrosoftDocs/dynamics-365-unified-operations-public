---
title: PerformanceMonitorCounter class
description: This topic describes the PerformanceMonitorCounter class.
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

# Class PerformanceMonitorCounter

[!include [banner](../../includes/banner.md)]

```xpp
class PerformanceMonitorCounter extends Object
```

The PerformanceMonitorCounter class identifies a counter that is assigned to a particular instance of a particular snapshot.

## Remarks

The data can be fetched by using the get methods.

## Examples

## Methods

| Method                 | Description                                                                                    |
|------------------------|------------------------------------------------------------------------------------------------|
| public int intData()   |                                                                                                |
| public str name()      |                                                                                                |
| public Time timeData() |                                                                                                |
| public str toString()  | Returns a string that contains the class handle and name, and possibly additional information. |

## Method intData

```xpp
public int intData()
```

### Return Value - intData

## Method name

```xpp
public str name()
```

### Return Value - name

## Method timeData

```xpp
public Time timeData()
```

### Return Value - timeData

## Method toString

Returns a string that contains the class handle and name, and possibly additional information.

```xpp
public str toString()
```

### Return Value - toString

A textual description of the class.

### Remarks - toString

By default, for most classes, the toString method returns a string that contains the class handle and name. However, in some classes additional information is returned in the string.

