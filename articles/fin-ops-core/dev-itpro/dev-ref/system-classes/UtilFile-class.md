---
title: UtilFile class
description: This topic describes the UtilFile class.
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

# Class UtilFile

[!include [banner](../../includes/banner.md)]

```xpp
class UtilFile extends Object
```

## Remarks

## Examples

## Methods

| Method                                                      | Description                                                      |
|-------------------------------------------------------------|------------------------------------------------------------------|
| public boolean aodFileExist(UtilEntryLevel layer)           |                                                                  |
| public int importAODFile(UtilEntryLevel layer, int modelId) |                                                                  |
| public str layers()                                         |                                                                  |
| public boolean needReindex()                                |                                                                  |
| public void check(str layer, str action)                    |                                                                  |
| public void new(str fileType)                               | Initializes a new instance of the Object class.                  |
| public void reindex()                                       | Lets you create, read, update, and delete X++ code and metadata. |
| public void flushCache()                                    |                                                                  |

## Method aodFileExist

```xpp
public boolean aodFileExist(UtilEntryLevel layer)
```

### Parameters - aodFileExist

layer  

### Return Value - aodFileExist

## Method importAODFile

```xpp
public int importAODFile(UtilEntryLevel layer, int modelId)
```

### Parameters - importAODFile

layer  

<!-- -->

modelId  

### Return Value - importAODFile

## Method layers

```xpp
public str layers()
```

### Return Value - layers

## Method needReindex

```xpp
public boolean needReindex()
```

### Return Value - needReindex

## Method check

```xpp
public void check(str layer, str action)
```

### Parameters - check

layer  

<!-- -->

action  

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(str fileType)
```

### Parameters - new

fileType  

## Method reindex

Lets you create, read, update, and delete X++ code and metadata.

```xpp
public void reindex()
```

### Remarks - reindex

Make sure that the user has access to the development security key (SysDevelopment) before you call this API.

### Examples - reindex

The following example calls the UtilFile.reindex method. It checks whether the user has the required security key before you perform a modification.

```xpp
server static public void Main(Args _args) 
{ 
    UtilFile u; 
    u = new UtilFile("util"); 
    if (u) 
    { 
        u.reindex(); 
    } 
}
```

## Method flushCache

```xpp
public void flushCache()
```


