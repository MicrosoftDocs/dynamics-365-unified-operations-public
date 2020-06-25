---
title: QueryOrderByField class
description: This topic describes the QueryOrderByField class.
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

# Class QueryOrderByField

[!include [banner](../../includes/banner.md)]

```xpp
class QueryOrderByField extends TreeNode
```

## Remarks

## Examples

## Methods

| Method                                                  | Description |
|---------------------------------------------------------|-------------|
| public boolean autoHeader(\[boolean value\])            |             |
| public int autoHeaderDetailLevel(\[int value\])         |             |
| public boolean autoSum(\[boolean value\])               |             |
| public int autoSumDetailLevel(\[int value\])            |             |
| public QueryBuildDataSource dataSource()                |             |
| public SortOrder direction()                            |             |
| public int fieldID()                                    |             |
| public TableId tableSelector(\[TableId tableSelector\]) |             |
| public void finalize()                                  |             |

## Method autoHeader

```xpp
public boolean autoHeader([boolean value])
```

### Parameters - autoHeader

value  

### Return Value - autoHeader

## Method autoHeaderDetailLevel

```xpp
public int autoHeaderDetailLevel([int value])
```

### Parameters - autoHeaderDetailLevel

value  

### Return Value - autoHeaderDetailLevel

## Method autoSum

```xpp
public boolean autoSum([boolean value])
```

### Parameters - autoSum

value  

### Return Value - autoSum

## Method autoSumDetailLevel

```xpp
public int autoSumDetailLevel([int value])
```

### Parameters - autoSumDetailLevel

value  

### Return Value - autoSumDetailLevel

## Method dataSource

```xpp
public QueryBuildDataSource dataSource()
```

### Return Value - dataSource

## Method direction

```xpp
public SortOrder direction()
```

### Return Value - direction

## Method fieldID

```xpp
public int fieldID()
```

### Return Value - fieldID

## Method tableSelector

```xpp
public TableId tableSelector([TableId tableSelector])
```

### Parameters - tableSelector

tableSelector  

### Return Value - tableSelector

## Method finalize

```xpp
public void finalize()
```

