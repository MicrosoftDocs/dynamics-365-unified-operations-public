---
title: SqlSyncPending class
description: This topic describes the SqlSyncPending class.
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

# Class SqlSyncPending

[!include [banner](../../includes/banner.md)]

```xpp
class SqlSyncPending extends Object
```

## Remarks

## Examples

## Methods

| Method                                               | Description                                             |
|------------------------------------------------------|---------------------------------------------------------|
| public ConfigurationKeyId configurationKeyTouched()  |                                                         |
| public boolean databaseTouched(\[boolean newValue\]) |                                                         |
| public ExtendedTypeId extendedDataTypeTouched()      |                                                         |
| public TableId indexesTouched()                      |                                                         |
| public TableId relationTouched()                     |                                                         |
| public TableId tableDeleted()                        |                                                         |
| public TableId tableTouched()                        |                                                         |
| public void new()                                    | Initializes a new instance of the SqlSyncPending class. |

## Method configurationKeyTouched

```xpp
public ConfigurationKeyId configurationKeyTouched()
```

### Return Value - configurationKeyTouched

## Method databaseTouched

```xpp
public boolean databaseTouched([boolean newValue])
```

### Parameters - databaseTouched

newValue  

### Return Value - databaseTouched

## Method extendedDataTypeTouched

```xpp
public ExtendedTypeId extendedDataTypeTouched()
```

### Return Value - extendedDataTypeTouched

## Method indexesTouched

```xpp
public TableId indexesTouched()
```

### Return Value - indexesTouched

## Method relationTouched

```xpp
public TableId relationTouched()
```

### Return Value - relationTouched

## Method tableDeleted

```xpp
public TableId tableDeleted()
```

### Return Value - tableDeleted

## Method tableTouched

```xpp
public TableId tableTouched()
```

### Return Value - tableTouched

## Method new

Initializes a new instance of the SqlSyncPending class.

```xpp
public void new()
```

