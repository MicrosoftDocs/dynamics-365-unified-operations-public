---
title: OleCommand class
description: This topic describes the OleCommand class.
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

# Class OleCommand

[!include [banner](../../includes/banner.md)]

```xpp
class OleCommand extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                              | Description                                     |
|-------------------------------------------------------------------------------------|-------------------------------------------------|
| public COMVariant exec(str cmdGroup, int cmdId, int cmdExecOption, COMVariant parm) |                                                 |
| public void finalize()                                                              |                                                 |
| public void new(ComInterface comObject)                                             | Initializes a new instance of the Object class. |

## Method exec

```xpp
public COMVariant exec(str cmdGroup, int cmdId, int cmdExecOption, COMVariant parm)
```

### Parameters - exec

cmdGroup  

<!-- -->

cmdId  

<!-- -->

cmdExecOption  

<!-- -->

parm  

### Return Value - exec

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(ComInterface comObject)
```

### Parameters - new

comObject  

