---
title: AsyncTaskResult class
description: This topic describes the AsyncTaskResult class.
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

# Class AsyncTaskResult

[!include [banner](../../includes/banner.md)]

```xpp
class AsyncTaskResult extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                               | Description |
|--------------------------------------------------------------------------------------|-------------|
| public container getResult()                                                         |             |
| public System.Exception getException()                                               |             |
| public container getInfologData()                                                    |             |
| public container getAsyncState()                                                     |             |
| ::public static AsyncTaskResult getAsyncTaskResult(System.Threading.Tasks.Task task) |             |

## Method getResult

```xpp
public container getResult()
```

### Return Value - getResult

## Method getException

```xpp
public System.Exception getException()
```

### Return Value - getException

## Method getInfologData

```xpp
public container getInfologData()
```

### Return Value - getInfologData

## Method getAsyncState

```xpp
public container getAsyncState()
```

### Return Value - getAsyncState

## Method getAsyncTaskResult

```xpp
public static AsyncTaskResult getAsyncTaskResult(System.Threading.Tasks.Task task)
```

### Parameters - getAsyncTaskResult

task  

### Return Value - getAsyncTaskResult

