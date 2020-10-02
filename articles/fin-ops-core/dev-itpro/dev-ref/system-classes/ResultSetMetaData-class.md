---
title: ResultSetMetaData class
description: This topic describes the ResultSetMetaData class.
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

# Class ResultSetMetaData

[!include [banner](../../includes/banner.md)]

```xpp
class ResultSetMetaData extends Object
```

## Remarks

## Examples

## Methods

| Method                                        | Description |
|-----------------------------------------------|-------------|
| public int getColumnCount()                   |             |
| public int getColumnDisplaySize(int ColumnID) |             |
| public str getColumnName(int ColumnID)        |             |
| public int getColumnType(int ColumnID)        |             |
| public int getPrecision(int ColumnID)         |             |
| public int getScale(int ColumnID)             |             |
| public int isNullable(int ColumnID)           |             |

## Method getColumnCount

```xpp
public int getColumnCount()
```

### Return Value - getColumnCount

## Method getColumnDisplaySize

```xpp
public int getColumnDisplaySize(int ColumnID)
```

### Parameters - getColumnDisplaySize

ColumnID  

### Return Value - getColumnDisplaySize

## Method getColumnName

```xpp
public str getColumnName(int ColumnID)
```

### Parameters - getColumnName

ColumnID  

### Return Value - getColumnName

## Method getColumnType

```xpp
public int getColumnType(int ColumnID)
```

### Parameters - getColumnType

ColumnID  

### Return Value - getColumnType

## Method getPrecision

```xpp
public int getPrecision(int ColumnID)
```

### Parameters - getPrecision

ColumnID  

### Return Value - getPrecision

## Method getScale

```xpp
public int getScale(int ColumnID)
```

### Parameters - getScale

ColumnID  

### Return Value - getScale

## Method isNullable

```xpp
public int isNullable(int ColumnID)
```

### Parameters - isNullable

ColumnID  

### Return Value - isNullable

