---
title: DataImportManager class
description: This topic describes the DataImportManager class.
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

# Class DataImportManager

[!include [banner](../../includes/banner.md)]

```xpp
class DataImportManager extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                        | Description                                                |
|-----------------------------------------------------------------------------------------------|------------------------------------------------------------|
| ::public static int commitImportSessionInfo(DataImportSessionInfo impInfo)                    |                                                            |
| ::public static int endTableDataCopy(ImportTableDataInfo dataInfo)                            |                                                            |
| ::public static int endTableSchemaCopy(ImportTableSchemaInfo schInfo)                         |                                                            |
| ::public static int finishMergeTableData()                                                    |                                                            |
| ::public static int getImportSessionProgress(DataImportSessionInfo impInfo)                   |                                                            |
| ::public static int mergeAllData()                                                            |                                                            |
| ::public static int mergeTableData(int mergeStep, TableId tableId, boolean updateHeartbeat)   |                                                            |
| ::public static int recoverImportSession(DataImportSessionInfo impInfo, boolean fTryToResume) |                                                            |
| public void new()                                                                             | Initializes a new instance of the DataImportManager class. |

## Method commitImportSessionInfo

```xpp
public static int commitImportSessionInfo(DataImportSessionInfo impInfo)
```

### Parameters - commitImportSessionInfo

impInfo  

### Return Value - commitImportSessionInfo

## Method endTableDataCopy

```xpp
public static int endTableDataCopy(ImportTableDataInfo dataInfo)
```

### Parameters - endTableDataCopy

dataInfo  

### Return Value - endTableDataCopy

## Method endTableSchemaCopy

```xpp
public static int endTableSchemaCopy(ImportTableSchemaInfo schInfo)
```

### Parameters - endTableSchemaCopy

schInfo  

### Return Value - endTableSchemaCopy

## Method finishMergeTableData

```xpp
public static int finishMergeTableData()
```

### Return Value - finishMergeTableData

## Method getImportSessionProgress

```xpp
public static int getImportSessionProgress(DataImportSessionInfo impInfo)
```

### Parameters - getImportSessionProgress

impInfo  

### Return Value - getImportSessionProgress

## Method mergeAllData

```xpp
public static int mergeAllData()
```

### Return Value - mergeAllData

## Method mergeTableData

```xpp
public static int mergeTableData(int mergeStep, TableId tableId, boolean updateHeartbeat)
```

### Parameters - mergeTableData

mergeStep  

<!-- -->

tableId  

<!-- -->

updateHeartbeat  

### Return Value - mergeTableData

## Method recoverImportSession

```xpp
public static int recoverImportSession(DataImportSessionInfo impInfo, boolean fTryToResume)
```

### Parameters - recoverImportSession

impInfo  

<!-- -->

fTryToResume  

### Return Value - recoverImportSession

## Method new

Initializes a new instance of the DataImportManager class.

```xpp
public void new()
```

