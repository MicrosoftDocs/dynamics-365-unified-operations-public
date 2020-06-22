---
title: QueryFilter class
description: This topic describes the QueryFilter class.
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

# Class QueryFilter

[!include [banner](../../includes/banner.md)]

```xpp
class QueryFilter extends Object
```

## Remarks

## Examples

## Methods

| Method                                                        | Description                                          |
|---------------------------------------------------------------|------------------------------------------------------|
| public QueryBuildDataSource dataSource()                      |                                                      |
| public FieldName field()                                      |                                                      |
| public QueryRangeType rangeType(\[QueryRangeType rangeType\]) |                                                      |
| public int status(\[int status\])                             |                                                      |
| public str toString()                                         | Returns a string that represents the current object. |
| public str value(\[str value\])                               |                                                      |
| public void finalize()                                        |                                                      |

## Method dataSource

```xpp
public QueryBuildDataSource dataSource()
```

### Return Value - dataSource

## Method field

```xpp
public FieldName field()
```

### Return Value - field

## Method rangeType

```xpp
public QueryRangeType rangeType([QueryRangeType rangeType])
```

### Parameters - rangeType

rangeType  

### Return Value - rangeType

## Method status

```xpp
public int status([int status])
```

### Parameters - status

status  

### Return Value - status

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

## Method value

```xpp
public str value([str value])
```

### Parameters - value

value  

### Return Value - value

## Method finalize

```xpp
public void finalize()
```

