---
title: DataSourceRuntimeMetadataChangedEvtArgs class
description: This topic describes the DataSourceRuntimeMetadataChangedEvtArgs class.
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

# Class DataSourceRuntimeMetadataChangedEvtArgs

[!include [banner](../../includes/banner.md)]

```xpp
class DataSourceRuntimeMetadataChangedEvtArgs extends ManagedEventArgs
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                    | Description                                               |
|-------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| public str changedDataSourceName()                                                                                                        |                                                           |
| public FieldId changedFieldId()                                                                                                           |                                                           |
| public DataSourceMetadataChangeType changeType()                                                                                          |                                                           |
| public str referencedDataSourceName()                                                                                                     |                                                           |
| public void new(str changedDatasourceName, str referencedDatasourceName, FieldId changedFieldId, DataSourceMetadataChangeType changeType) | Initializes a new instance of the ManagedEventArgs class. |
| public void finalize()                                                                                                                    |                                                           |

## Method changedDataSourceName

```xpp
public str changedDataSourceName()
```

### Return Value - changedDataSourceName

## Method changedFieldId

```xpp
public FieldId changedFieldId()
```

### Return Value - changedFieldId

## Method changeType

```xpp
public DataSourceMetadataChangeType changeType()
```

### Return Value - changeType

## Method referencedDataSourceName

```xpp
public str referencedDataSourceName()
```

### Return Value - referencedDataSourceName

## Method new

Initializes a new instance of the ManagedEventArgs class.

```xpp
public void new(str changedDatasourceName, str referencedDatasourceName, FieldId changedFieldId, DataSourceMetadataChangeType changeType)
```

### Parameters - new

changedDatasourceName  

<!-- -->

referencedDatasourceName  

<!-- -->

changedFieldId  

<!-- -->

changeType  

## Method finalize

```xpp
public void finalize()
```

