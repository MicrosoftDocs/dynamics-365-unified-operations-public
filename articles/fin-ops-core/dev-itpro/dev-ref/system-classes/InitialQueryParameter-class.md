---
title: InitialQueryParameter class
description: This topic describes the InitialQueryParameter class.
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

# Class InitialQueryParameter

[!include [banner](../../includes/banner.md)]

```xpp
class InitialQueryParameter extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                       | Description                                                    |
|--------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------|
| public boolean applyQuery(FormDataSource datasource)                                                         |                                                                |
| public str dataSourceName(\[str dataSourceName\])                                                            |                                                                |
| public str modeledQueryName(\[str modeledQueryName\])                                                        |                                                                |
| public Query query(\[Query query\])                                                                          |                                                                |
| ::public static InitialQueryParameter createByModeledQueryName(str modeledQueryName, \[str dataSourceName\]) |                                                                |
| ::public static InitialQueryParameter createByQuery(Query query, \[str dataSourceName\])                     |                                                                |
| public void finalize()                                                                                       |                                                                |
| public void new()                                                                                            | Initializes a new instance of the InitialQueryParameter class. |

## Method applyQuery

```xpp
public boolean applyQuery(FormDataSource datasource)
```

### Parameters - applyQuery

datasource  

### Return Value - applyQuery

## Method dataSourceName

```xpp
public str dataSourceName([str dataSourceName])
```

### Parameters - dataSourceName

dataSourceName  

### Return Value - dataSourceName

## Method modeledQueryName

```xpp
public str modeledQueryName([str modeledQueryName])
```

### Parameters - modeledQueryName

modeledQueryName  

### Return Value - modeledQueryName

## Method query

```xpp
public Query query([Query query])
```

### Parameters - query

query  

### Return Value - query

## Method createByModeledQueryName

```xpp
public static InitialQueryParameter createByModeledQueryName(str modeledQueryName, [str dataSourceName])
```

### Parameters - createByModeledQueryName

modeledQueryName  

<!-- -->

dataSourceName  

### Return Value - createByModeledQueryName

## Method createByQuery

```xpp
public static InitialQueryParameter createByQuery(Query query, [str dataSourceName])
```

### Parameters - createByQuery

query  

<!-- -->

dataSourceName  

### Return Value - createByQuery

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the InitialQueryParameter class.

```xpp
public void new()
```

