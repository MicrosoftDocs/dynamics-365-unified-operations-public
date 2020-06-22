---
title: QueryBuildFieldList class
description: This topic describes the QueryBuildFieldList class.
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

# Class QueryBuildFieldList

[!include [banner](../../includes/banner.md)]

```xpp
class QueryBuildFieldList extends TreeNode
```

The QueryBuildFieldList class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                                                                 | Description |
|--------------------------------------------------------------------------------------------------------|-------------|
| public int addAllFields(TableName tableName)                                                           |             |
| public QueryBuildFieldList addField(FieldId fieldId, \[SelectionField fieldType\], \[int arrayIndex\]) |             |
| public int dynamic(\[int value\])                                                                      |             |
| public FieldId field(int index)                                                                        |             |
| public int fieldCount()                                                                                |             |
| public SelectionField fieldKind(int index)                                                             |             |
| public TableId tableSelector(int index)                                                                |             |
| public void clearFieldList()                                                                           |             |

## Method addAllFields

```xpp
public int addAllFields(TableName tableName)
```

### Parameters - addAllFields

tableName  

### Return Value - addAllFields

## Method addField

```xpp
public QueryBuildFieldList addField(FieldId fieldId, [SelectionField fieldType], [int arrayIndex])
```

### Parameters - addField

fieldId  

<!-- -->

fieldType  

<!-- -->

arrayIndex  

### Return Value - addField

## Method dynamic

```xpp
public int dynamic([int value])
```

### Parameters - dynamic

value  

### Return Value - dynamic

## Method field

```xpp
public FieldId field(int index)
```

### Parameters - field

index  

### Return Value - field

## Method fieldCount

```xpp
public int fieldCount()
```

### Return Value - fieldCount

## Method fieldKind

```xpp
public SelectionField fieldKind(int index)
```

### Parameters - fieldKind

index  

### Return Value - fieldKind

## Method tableSelector

```xpp
public TableId tableSelector(int index)
```

### Parameters - tableSelector

index  

### Return Value - tableSelector

## Method clearFieldList

```xpp
public void clearFieldList()
```

