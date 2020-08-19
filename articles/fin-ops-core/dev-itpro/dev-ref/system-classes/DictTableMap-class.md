---
title: DictTableMap class
description: This topic describes the DictTableMap class.
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

# Class DictTableMap

[!include [banner](../../includes/banner.md)]

```xpp
class DictTableMap extends Object
```

The DictTableMap class provides information about a table mapping.

## Remarks

## Examples

## Methods

| Method                                 | Description                                                    |
|----------------------------------------|----------------------------------------------------------------|
| public int table()                     | Retrieves the table that the mapping references.               |
| public int fieldCnt()                  | Retrieves the count of fields in the table mapping.            |
| public int fieldCnt2FieldTo(int cnt)   | Retrieves the table field that is referenced by the map field. |
| public int fieldCnt2FieldFrom(int cnt) | Retrieves the map field that is referencing a table field.     |

## Method table

Retrieves the table that the mapping references.

```xpp
public int table()
```

### Return Value - table

The table ID.

### Remarks - table

Use this method to get to the table mappings, instead of traversing to the tree node.

## Method fieldCnt

Retrieves the count of fields in the table mapping.

```xpp
public int fieldCnt()
```

### Return Value - fieldCnt

The count.

### Remarks - fieldCnt

Use this method to get to the table mappings, instead of traversing to the tree node.

## Method fieldCnt2FieldTo

Retrieves the table field that is referenced by the map field.

```xpp
public int fieldCnt2FieldTo(int cnt)
```

### Parameters - fieldCnt2FieldTo

cnt  

### Return Value - fieldCnt2FieldTo

The table field ID.

### Remarks - fieldCnt2FieldTo

Use this method to get to the table mappings, instead of traversing to the tree node.

## Method fieldCnt2FieldFrom

Retrieves the map field that is referencing a table field.

```xpp
public int fieldCnt2FieldFrom(int cnt)
```

### Parameters - fieldCnt2FieldFrom

cnt  

### Return Value - fieldCnt2FieldFrom

The map field ID.

### Remarks - fieldCnt2FieldFrom

Use this method to get to the table mappings, instead of traversing to the tree node.

