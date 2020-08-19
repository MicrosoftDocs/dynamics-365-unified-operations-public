---
title: DataEntityDataSourceRuntimeContext class
description: This topic describes the DataEntityDataSourceRuntimeContext class.
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

# Class DataEntityDataSourceRuntimeContext

[!include [banner](../../includes/banner.md)]


```xpp
class DataEntityDataSourceRuntimeContext extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                         | Description |
|--------------------------------------------------------------------------------|-------------|
| public str name()                                                              |             |
| public int id()                                                                |             |
| public Common getBuffer()                                                      |             |
| public DataEntityDatabaseOperation getDatabaseOperation()                      |             |
| public str getCompany()                                                        |             |
| public boolean getDataSaved()                                                  |             |
| public boolean skipDataMethods(\[boolean skip\])                               |             |
| public boolean skipDeleteMethod(\[boolean b\])                                 |             |
| public boolean skipValidateWrite(\[boolean skip\])                             |             |
| public boolean skipValidateDelete(\[boolean skip\])                            |             |
| public boolean skipInitValue(\[boolean skip\])                                 |             |
| public boolean skipDefaultRow(\[boolean skip\])                                |             |
| public boolean readOnly()                                                      |             |
| public boolean oneToMany()                                                     |             |
| public boolean optional()                                                      |             |
| public boolean dateEffective()                                                 |             |
| public boolean conflictDetectionInvoked(\[boolean found\])                     |             |
| public void new(Common dataSourceBuffer, str dataSourceName, int dataSourceId) |             |
| public void setCompany(str company)                                            |             |
| public void setBuffer(Common buffer)                                           |             |
| public void setDatabaseOperation(DataEntityDatabaseOperation dbOperation)      |             |
| public void setDataSaved(boolean saved)                                        |             |

## Method name

```xpp
public str name()
```

### Return Value - name

## Method id

```xpp
public int id()
```

### Return Value - id

## Method getBuffer

```xpp
public Common getBuffer()
```

### Return Value - getBuffer

## Method getDatabaseOperation

```xpp
public DataEntityDatabaseOperation getDatabaseOperation()
```

### Return Value - getDatabaseOperation

## Method getCompany

```xpp
public str getCompany()
```

### Return Value - getCompany

## Method getDataSaved

```xpp
public boolean getDataSaved()
```

### Return Value - getDataSaved

## Method skipDataMethods

```xpp
public boolean skipDataMethods([boolean skip])
```

### Parameters - skipDataMethods

skip  

### Return Value - skipDataMethods

## Method skipDeleteMethod

```xpp
public boolean skipDeleteMethod([boolean b])
```

### Parameters - skipDeleteMethod

b  

### Return Value - skipDeleteMethod

## Method skipValidateWrite

```xpp
public boolean skipValidateWrite([boolean skip])
```

### Parameters - skipValidateWrite

skip  

### Return Value - skipValidateWrite

## Method skipValidateDelete

```xpp
public boolean skipValidateDelete([boolean skip])
```

### Parameters - skipValidateDelete

skip  

### Return Value - skipValidateDelete

## Method skipInitValue

```xpp
public boolean skipInitValue([boolean skip])
```

### Parameters - skipInitValue

skip  

### Return Value - skipInitValue

## Method skipDefaultRow

```xpp
public boolean skipDefaultRow([boolean skip])
```

### Parameters - skipDefaultRow

skip  

### Return Value - skipDefaultRow

## Method readOnly

```xpp
public boolean readOnly()
```

### Return Value - readOnly

## Method oneToMany

```xpp
public boolean oneToMany()
```

### Return Value - oneToMany

## Method optional

```xpp
public boolean optional()
```

### Return Value - optional

## Method dateEffective

```xpp
public boolean dateEffective()
```

### Return Value - dateEffective

## Method conflictDetectionInvoked

```xpp
public boolean conflictDetectionInvoked([boolean found])
```

### Parameters - conflictDetectionInvoked

found  

### Return Value - conflictDetectionInvoked

## Method new

```xpp
public void new(Common dataSourceBuffer, str dataSourceName, int dataSourceId)
```

### Parameters - new

dataSourceBuffer  

<!-- -->

dataSourceName  

<!-- -->

dataSourceId  

## Method setCompany

```xpp
public void setCompany(str company)
```

### Parameters - setCompany

company  

## Method setBuffer

```xpp
public void setBuffer(Common buffer)
```

### Parameters - setBuffer

buffer  

## Method setDatabaseOperation

```xpp
public void setDatabaseOperation(DataEntityDatabaseOperation dbOperation)
```

### Parameters - setDatabaseOperation

dbOperation  

## Method setDataSaved

```xpp
public void setDataSaved(boolean saved)
```

### Parameters - setDataSaved

saved  

