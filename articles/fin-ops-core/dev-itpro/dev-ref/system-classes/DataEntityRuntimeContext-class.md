---
title: DataEntityRuntimeContext class
description: This topic describes the DataEntityRuntimeContext class.
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

# Class DataEntityRuntimeContext

[!include [banner](../../includes/banner.md)]

```xpp
class DataEntityRuntimeContext extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                               | Description |
|------------------------------------------------------------------------------------------------------|-------------|
| public DataEntityDatabaseOperation getDatabaseOperation()                                            |             |
| public AnyType getCustomProperty(str name)                                                           |             |
| public Common getEntityRecord()                                                                      |             |
| public DataEntityDataSourceRuntimeContext getRuntimeContextByName(str datasourceName)                |             |
| public void new(DataEntityDatabaseOperation operation, Common record, DataEntityPersister persister) |             |
| public void setCustomProperty(str name, AnyType obj)                                                 |             |

## Method getDatabaseOperation

```xpp
public DataEntityDatabaseOperation getDatabaseOperation()
```

### Return Value - getDatabaseOperation

## Method getCustomProperty

```xpp
public AnyType getCustomProperty(str name)
```

### Parameters - getCustomProperty

name  

### Return Value - getCustomProperty

## Method getEntityRecord

```xpp
public Common getEntityRecord()
```

### Return Value - getEntityRecord

## Method getRuntimeContextByName

```xpp
public DataEntityDataSourceRuntimeContext getRuntimeContextByName(str datasourceName)
```

### Parameters - getRuntimeContextByName

datasourceName  

### Return Value - getRuntimeContextByName

## Method new

```xpp
public void new(DataEntityDatabaseOperation operation, Common record, DataEntityPersister persister)
```

### Parameters - new

operation  

<!-- -->

record  

<!-- -->

persister  

## Method setCustomProperty

```xpp
public void setCustomProperty(str name, AnyType obj)
```

### Parameters - setCustomProperty

name  

<!-- -->

obj  

