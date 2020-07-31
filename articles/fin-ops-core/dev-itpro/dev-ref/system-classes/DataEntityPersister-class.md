---
title: DataEntityPersister class
description: This topic describes the DataEntityPersister class.
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

# Class DataEntityPersister

[!include [banner](../../includes/banner.md)]

```xpp
class DataEntityPersister extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                                                            | Description |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| public boolean doSaveDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                             |             |
| public Common doFindDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                              |             |
| public boolean hasDataSourceRecordChanged(int dataSourceId, Common originalRecord, Common updatedRecord)                                                                                                          |             |
| public str getCompanyForDataSource(DataEntityRuntimeContext entityCtx, int dataSourceId)                                                                                                                          |             |
| public int getValidTimeStateUpdateModeForDataSource(DataEntityRuntimeContext entityCtx, int dataSourceId)                                                                                                         |             |
| public Common findDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                                |             |
| public boolean saveDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                               |             |
| public void doMapEntityToDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                         |             |
| public void mapEntityToDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                           |             |
| public void doMapDataSourceToEntity(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                         |             |
| public void selectDataSourceBufferByRecId(Common dataSourceBuffer, Int64 dataSourceRecId, Boolean explicitlyForUpdate, Boolean fetchActiveRecordOnly)                                                             |             |
| public void doPersistEntity(DataEntityRuntimeContext entityCtx)                                                                                                                                                   |             |
| public void doInitializeDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)                                                                                          |             |
| public void initializeDataSource(DataEntityRuntimeContext entityCtx, str dataSourceName, Common dataSourceBuffer, int dataSourceId, Boolean optional, Boolean readonly, Boolean oneToMany, Boolean dateEffective) |             |

## Method doSaveDataSource

```xpp
public boolean doSaveDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)
```

### Parameters - doSaveDataSource

entityCtx  

<!-- -->

dataSourceCtx  

### Return Value - doSaveDataSource

## Method doFindDataSource

```xpp
public Common doFindDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)
```

### Parameters - doFindDataSource

entityCtx  

<!-- -->

dataSourceCtx  

### Return Value - doFindDataSource

## Method hasDataSourceRecordChanged

```xpp
public boolean hasDataSourceRecordChanged(int dataSourceId, Common originalRecord, Common updatedRecord)
```

### Parameters - hasDataSourceRecordChanged

dataSourceId  

<!-- -->

originalRecord  

<!-- -->

updatedRecord  

### Return Value - hasDataSourceRecordChanged

## Method getCompanyForDataSource

```xpp
public str getCompanyForDataSource(DataEntityRuntimeContext entityCtx, int dataSourceId)
```

### Parameters - getCompanyForDataSource

entityCtx  

<!-- -->

dataSourceId  

### Return Value - getCompanyForDataSource

## Method getValidTimeStateUpdateModeForDataSource

```xpp
public int getValidTimeStateUpdateModeForDataSource(DataEntityRuntimeContext entityCtx, int dataSourceId)
```

### Parameters - getValidTimeStateUpdateModeForDataSource

entityCtx  

<!-- -->

dataSourceId  

### Return Value - getValidTimeStateUpdateModeForDataSource

## Method findDataSource

```xpp
public Common findDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)
```

### Parameters - findDataSource

entityCtx  

<!-- -->

dataSourceCtx  

### Return Value - findDataSource

## Method saveDataSource

```xpp
public boolean saveDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)
```

### Parameters - saveDataSource

entityCtx  

<!-- -->

dataSourceCtx  

### Return Value - saveDataSource

## Method doMapEntityToDataSource

```xpp
public void doMapEntityToDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)
```

### Parameters - doMapEntityToDataSource

entityCtx  

<!-- -->

dataSourceCtx  

## Method mapEntityToDataSource

```xpp
public void mapEntityToDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)
```

### Parameters - mapEntityToDataSource

entityCtx  

<!-- -->

dataSourceCtx  

## Method doMapDataSourceToEntity

```xpp
public void doMapDataSourceToEntity(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)
```

### Parameters - doMapDataSourceToEntity

entityCtx  

<!-- -->

dataSourceCtx  

## Method selectDataSourceBufferByRecId

```xpp
public void selectDataSourceBufferByRecId(Common dataSourceBuffer, Int64 dataSourceRecId, Boolean explicitlyForUpdate, Boolean fetchActiveRecordOnly)
```

### Parameters - selectDataSourceBufferByRecId

dataSourceBuffer  

<!-- -->

dataSourceRecId  

<!-- -->

explicitlyForUpdate  

<!-- -->

fetchActiveRecordOnly  

## Method doPersistEntity

```xpp
public void doPersistEntity(DataEntityRuntimeContext entityCtx)
```

### Parameters - doPersistEntity

entityCtx  

## Method doInitializeDataSource

```xpp
public void doInitializeDataSource(DataEntityRuntimeContext entityCtx, DataEntityDataSourceRuntimeContext dataSourceCtx)
```

### Parameters - doInitializeDataSource

entityCtx  

<!-- -->

dataSourceCtx  

## Method initializeDataSource

```xpp
public void initializeDataSource(DataEntityRuntimeContext entityCtx, str dataSourceName, Common dataSourceBuffer, int dataSourceId, Boolean optional, Boolean readonly, Boolean oneToMany, Boolean dateEffective)
```

### Parameters - initializeDataSource

entityCtx  

<!-- -->

dataSourceName  

<!-- -->

dataSourceBuffer  

<!-- -->

dataSourceId  

<!-- -->

optional  

<!-- -->

readonly  

<!-- -->

oneToMany  

<!-- -->

dateEffective  

