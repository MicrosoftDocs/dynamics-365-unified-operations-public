---
title: DataImportSessionInfo class
description: This topic describes the DataImportSessionInfo class.
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

# Class DataImportSessionInfo

[!include [banner](../../includes/banner.md)]

```xpp
class DataImportSessionInfo extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                         | Description                                     |
|--------------------------------------------------------------------------------|-------------------------------------------------|
| public int addImportTable(str szTabName, int ulTableId, boolean fAlwaysUpdate) |                                                 |
| public int getCurrentProgress()                                                |                                                 |
| public str getCurrentTable()                                                   |                                                 |
| public int setSourceGUID(Guid szSourceGUID)                                    |                                                 |
| public int setSysDataImpLogId(int sysDataImpLogId)                             |                                                 |
| public void new(str szInpFileName, boolean fUpdateExistingData)                | Initializes a new instance of the Object class. |

## Method addImportTable

```xpp
public int addImportTable(str szTabName, int ulTableId, boolean fAlwaysUpdate)
```

### Parameters - addImportTable

szTabName  

<!-- -->

ulTableId  

<!-- -->

fAlwaysUpdate  

### Return Value - addImportTable

## Method getCurrentProgress

```xpp
public int getCurrentProgress()
```

### Return Value - getCurrentProgress

## Method getCurrentTable

```xpp
public str getCurrentTable()
```

### Return Value - getCurrentTable

## Method setSourceGUID

```xpp
public int setSourceGUID(Guid szSourceGUID)
```

### Parameters - setSourceGUID

szSourceGUID  

### Return Value - setSourceGUID

## Method setSysDataImpLogId

```xpp
public int setSysDataImpLogId(int sysDataImpLogId)
```

### Parameters - setSysDataImpLogId

sysDataImpLogId  

### Return Value - setSysDataImpLogId

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(str szInpFileName, boolean fUpdateExistingData)
```

### Parameters - new

szInpFileName  

<!-- -->

fUpdateExistingData  

