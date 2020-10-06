---
title: NumberSequence class
description: This topic describes the NumberSequence class.
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

# Class NumberSequence

[!include [banner](../../includes/banner.md)]


```xpp
class NumberSequence extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                | Description                                             |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| ::public static int getNextNumber(Connection connection, Int64 numbersequencerecordid, Int64 globaltransid, str userid, int sessionid, DateTime sessionLoginDateTime) |                                                         |
| public void new()                                                                                                                                                     | Initializes a new instance of the NumberSequence class. |

## Method getNextNumber

```xpp
public static int getNextNumber(Connection connection, Int64 numbersequencerecordid, Int64 globaltransid, str userid, int sessionid, DateTime sessionLoginDateTime)
```

### Parameters - getNextNumber

connection  

<!-- -->

numbersequencerecordid  

<!-- -->

globaltransid  

<!-- -->

userid  

<!-- -->

sessionid  

<!-- -->

sessionLoginDateTime  

### Return Value - getNextNumber

## Method new

Initializes a new instance of the NumberSequence class.

```xpp
public void new()
```

