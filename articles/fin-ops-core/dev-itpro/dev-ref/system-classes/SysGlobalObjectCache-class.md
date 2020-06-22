---
title: SysGlobalObjectCache class
description: This topic describes the SysGlobalObjectCache class.
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

# Class SysGlobalObjectCache

[!include [banner](../../includes/banner.md)]

```xpp
class SysGlobalObjectCache extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                           | Description                                                   |
|----------------------------------------------------------------------------------|---------------------------------------------------------------|
| public container find(GlobalObjectCacheScope scope, container key)               |                                                               |
| public void finalize()                                                           |                                                               |
| public void remove(GlobalObjectCacheScope scope, container key)                  |                                                               |
| public void print(GlobalObjectCacheScope scope)                                  |                                                               |
| public void clear(GlobalObjectCacheScope scope)                                  |                                                               |
| ::public static void clearAllCaches()                                            |                                                               |
| public void new()                                                                | Initializes a new instance of the SysGlobalObjectCache class. |
| public void insert(GlobalObjectCacheScope scope, container key, container value) |                                                               |

## Method find

```xpp
public container find(GlobalObjectCacheScope scope, container key)
```

### Parameters - find

scope  

<!-- -->

key  

### Return Value - find

## Method finalize

```xpp
public void finalize()
```

## Method remove

```xpp
public void remove(GlobalObjectCacheScope scope, container key)
```

### Parameters - remove

scope  

<!-- -->

key  

## Method print

```xpp
public void print(GlobalObjectCacheScope scope)
```

### Parameters - print

scope  

## Method clear

```xpp
public void clear(GlobalObjectCacheScope scope)
```

### Parameters - clear

scope  

## Method clearAllCaches

```xpp
public static void clearAllCaches()
```

## Method new

Initializes a new instance of the SysGlobalObjectCache class.

```xpp
public void new()
```

## Method insert

```xpp
public void insert(GlobalObjectCacheScope scope, container key, container value)
```

### Parameters - insert

scope  

<!-- -->

key  

<!-- -->

value  

