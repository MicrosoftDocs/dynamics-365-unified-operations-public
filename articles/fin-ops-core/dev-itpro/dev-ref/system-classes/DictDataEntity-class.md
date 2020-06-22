---
title: DictDataEntity class
description: This topic describes the DictDataEntity class.
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

# Class DictDataEntity

[!include [banner](../../includes/banner.md)]

```xpp
class DictDataEntity extends DictView
```

## Remarks

## Examples

## Methods

| Method                                                  | Description |
|---------------------------------------------------------|-------------|
| public boolean isAggregateDataEntity()                  |             |
| public boolean isReadOnly()                             |             |
| public str primaryCompanyContext()                      |             |
| public str primaryKey()                                 |             |
| public boolean supportsSetBasedSqlOperations()          |             |
| public AutoNo enableSetBasedSqlOperations()             |             |
| public str modules()                                    |             |
| public EntityCategory entityCategory()                  |             |
| public boolean dataManagementEnabled()                  |             |
| public str dataManagementStagingTable()                 |             |
| public str publicCollectionName()                       |             |
| public str publicEntityName()                           |             |
| public boolean dataSourceIsReadOnly(str dataSourceName) |             |
| public str dataSourceID2Name(int dataSourceId)          |             |
| public boolean hasExtensionFields()                     |             |
| public List getExtensionFieldNames()                    |             |
| ::public static List listOfDataEntities()               |             |
| public void new(TableId tableId)                        |             |

## Method isAggregateDataEntity

```xpp
public boolean isAggregateDataEntity()
```

### Return Value - isAggregateDataEntity

## Method isReadOnly

```xpp
public boolean isReadOnly()
```

### Return Value - isReadOnly

## Method primaryCompanyContext

```xpp
public str primaryCompanyContext()
```

### Return Value - primaryCompanyContext

## Method primaryKey

```xpp
public str primaryKey()
```

### Return Value - primaryKey

## Method supportsSetBasedSqlOperations

```xpp
public boolean supportsSetBasedSqlOperations()
```

### Return Value - supportsSetBasedSqlOperations

## Method enableSetBasedSqlOperations

```xpp
public AutoNo enableSetBasedSqlOperations()
```

### Return Value - enableSetBasedSqlOperations

## Method modules

```xpp
public str modules()
```

### Return Value - modules

## Method entityCategory

```xpp
public EntityCategory entityCategory()
```

### Return Value - entityCategory

## Method dataManagementEnabled

```xpp
public boolean dataManagementEnabled()
```

### Return Value - dataManagementEnabled

## Method dataManagementStagingTable

```xpp
public str dataManagementStagingTable()
```

### Return Value - dataManagementStagingTable

## Method publicCollectionName

```xpp
public str publicCollectionName()
```

### Return Value - publicCollectionName

## Method publicEntityName

```xpp
public str publicEntityName()
```

### Return Value - publicEntityName

## Method dataSourceIsReadOnly

```xpp
public boolean dataSourceIsReadOnly(str dataSourceName)
```

### Parameters - dataSourceIsReadOnly

dataSourceName  

### Return Value - dataSourceIsReadOnly

## Method dataSourceID2Name

```xpp
public str dataSourceID2Name(int dataSourceId)
```

### Parameters - dataSourceID2Name

dataSourceId  

### Return Value - dataSourceID2Name

## Method hasExtensionFields

```xpp
public boolean hasExtensionFields()
```

### Return Value - hasExtensionFields

## Method getExtensionFieldNames

```xpp
public List getExtensionFieldNames()
```

### Return Value - getExtensionFieldNames

## Method listOfDataEntities

```xpp
public static List listOfDataEntities()
```

### Return Value - listOfDataEntities

## Method new

```xpp
public void new(TableId tableId)
```

### Parameters - new

tableId  

