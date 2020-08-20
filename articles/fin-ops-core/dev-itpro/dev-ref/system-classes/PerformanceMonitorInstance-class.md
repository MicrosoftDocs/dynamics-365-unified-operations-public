---
title: PerformanceMonitorInstance class
description: This topic describes the PerformanceMonitorInstance class.
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

# Class PerformanceMonitorInstance

[!include [banner](../../includes/banner.md)]

```xpp
class PerformanceMonitorInstance extends Object
```

The PerformanceMonitorInstance class represents a process that is running on the machine on which the Process Monitor runs.

## Remarks

This class allows for queries of the process counters. You can use objects of this class to query the processes counters. Each counter represents a process parameter.

## Examples

## Methods

| Method                                                       | Description                                                                                    |
|--------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| public PerformanceMonitorCounter getCounter(str counterName) |                                                                                                |
| public str name()                                            |                                                                                                |
| public str toString()                                        | Returns a string that contains the class handle and name, and possibly additional information. |

## Method getCounter

```xpp
public PerformanceMonitorCounter getCounter(str counterName)
```

### Parameters - getCounter

counterName  

### Return Value - getCounter

## Method name

```xpp
public str name()
```

### Return Value - name

## Method toString

Returns a string that contains the class handle and name, and possibly additional information.

```xpp
public str toString()
```

### Return Value - toString

Returns a textual description of the class.

### Remarks - toString

By default, for most classes, the toString method returns a string that contains the class handle and name. However, in some classes additional information is returned in the string.

