---
title: xCompany class
description: This topic describes the xCompany class.
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

# Class xCompany

[!include [banner](../../includes/banner.md)]

```xpp
class xCompany extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                              | Description                                        |
|-------------------------------------------------------------------------------------|----------------------------------------------------|
| public DataAreaId dataArea(TableId tableId)                                         |                                                    |
| public SelectableDataArea ext()                                                     |                                                    |
| public boolean log(DatabaseLogType typeOfLog, TableId tableId, \[FieldId fieldId\]) |                                                    |
| public boolean logAlways(DatabaseLogType typeOfLog, \[boolean log\])                | Enables or disables logging for non-system tables. |
| public boolean reindex(\[TableId tableId\])                                         |                                                    |
| public void reloadLog()                                                             |                                                    |
| public void new(SelectableDataArea company)                                         | Initializes a new instance of the Object class.    |
| public void check()                                                                 |                                                    |
| public void reloadRights()                                                          |                                                    |
| public void flushCache(TableId tableId)                                             |                                                    |
| public void reloadTableCollections()                                                |                                                    |

## Method dataArea

```xpp
public DataAreaId dataArea(TableId tableId)
```

### Parameters - dataArea

tableId  

### Return Value - dataArea

## Method ext

```xpp
public SelectableDataArea ext()
```

### Return Value - ext

## Method log

```xpp
public boolean log(DatabaseLogType typeOfLog, TableId tableId, [FieldId fieldId])
```

### Parameters - log

typeOfLog  

<!-- -->

tableId  

<!-- -->

fieldId  

### Return Value - log

## Method logAlways

Enables or disables logging for non-system tables.

```xpp
public boolean logAlways(DatabaseLogType typeOfLog, [boolean log])
```

### Parameters - logAlways

typeOfLog  

<!-- -->

log  

### Return Value - logAlways

The status of the database logging for the indicated operation before the call.

### Remarks - logAlways

Without the optional typeOfLog parameter, this method will report the status of the database logging for the indicated operation. Note that if the optional parameter is provided, the method is guarded by CAS and the calling code must assert SysDatabaselogPermission.

## Method reindex

```xpp
public boolean reindex([TableId tableId])
```

### Parameters - reindex

tableId  

### Return Value - reindex

## Method reloadLog

```xpp
public void reloadLog()
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(SelectableDataArea company)
```

### Parameters - new

company  

## Method check

```xpp
public void check()
```

## Method reloadRights

```xpp
public void reloadRights()
```

## Method flushCache

```xpp
public void flushCache(TableId tableId)
```

### Parameters - flushCache

tableId  

## Method reloadTableCollections

```xpp
public void reloadTableCollections()
```

