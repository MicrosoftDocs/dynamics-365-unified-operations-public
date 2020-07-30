---
title: xSqlEnumerator class
description: This topic describes the xSqlEnumerator class.
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

# Class xSqlEnumerator

[!include [banner](../../includes/banner.md)]

```xpp
class xSqlEnumerator extends Object
```

## Remarks

## Examples

## Methods

| Method                                               | Description                                             |
|------------------------------------------------------|---------------------------------------------------------|
| public str getConnStr(str database)                  |                                                         |
| public List getDatabases(str server, \[str driver\]) |                                                         |
| public List getServers(str driver)                   |                                                         |
| public void new()                                    | Initializes a new instance of the xSqlEnumerator class. |

## Method getConnStr

```xpp
public str getConnStr(str database)
```

### Parameters - getConnStr

database  

### Return Value - getConnStr

## Method getDatabases

```xpp
public List getDatabases(str server, [str driver])
```

### Parameters - getDatabases

server  

<!-- -->

driver  

### Return Value - getDatabases

## Method getServers

```xpp
public List getServers(str driver)
```

### Parameters - getServers

driver  

### Return Value - getServers

## Method new

Initializes a new instance of the xSqlEnumerator class.

```xpp
public void new()
```

