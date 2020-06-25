---
title: ImportTableSchemaInfo class
description: This topic describes the ImportTableSchemaInfo class.
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

# Class ImportTableSchemaInfo

[!include [banner](../../includes/banner.md)]

```xpp
class ImportTableSchemaInfo extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                             | Description                                     |
|------------------------------------------------------------------------------------|-------------------------------------------------|
| public int addColumnInfo(str szColName, Types eColType, int eColRole, int lColOrd) |                                                 |
| public int addColumnMapping(str szRefRecIdColName, str szRefTableIdColName)        |                                                 |
| public int hasEqualityCriteria(boolean fHasEqualityCriteria)                       |                                                 |
| public int shreddedMetadataTable(boolean fIsShreddedMetadataTable)                 |                                                 |
| public void new(int usTableId)                                                     | Initializes a new instance of the Object class. |

## Method addColumnInfo

```xpp
public int addColumnInfo(str szColName, Types eColType, int eColRole, int lColOrd)
```

### Parameters - addColumnInfo

szColName  

<!-- -->

eColType  

<!-- -->

eColRole  

<!-- -->

lColOrd  

### Return Value - addColumnInfo

## Method addColumnMapping

```xpp
public int addColumnMapping(str szRefRecIdColName, str szRefTableIdColName)
```

### Parameters - addColumnMapping

szRefRecIdColName  

<!-- -->

szRefTableIdColName  

### Return Value - addColumnMapping

## Method hasEqualityCriteria

```xpp
public int hasEqualityCriteria(boolean fHasEqualityCriteria)
```

### Parameters - hasEqualityCriteria

fHasEqualityCriteria  

### Return Value - hasEqualityCriteria

## Method shreddedMetadataTable

```xpp
public int shreddedMetadataTable(boolean fIsShreddedMetadataTable)
```

### Parameters - shreddedMetadataTable

fIsShreddedMetadataTable  

### Return Value - shreddedMetadataTable

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(int usTableId)
```

### Parameters - new

usTableId  

