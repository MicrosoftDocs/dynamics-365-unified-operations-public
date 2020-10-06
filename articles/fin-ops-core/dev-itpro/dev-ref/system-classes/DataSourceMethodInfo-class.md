---
title: DataSourceMethodInfo class
description: This topic describes the DataSourceMethodInfo class.
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

# Class DataSourceMethodInfo

[!include [banner](../../includes/banner.md)]

```xpp
class DataSourceMethodInfo extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                           | Description                                     |
|------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| public DisplayFunctionType displayType()                                                                         |                                                 |
| public boolean isStatic()                                                                                        |                                                 |
| public str name()                                                                                                |                                                 |
| public Types returnType()                                                                                        |                                                 |
| public int returnTypeId()                                                                                        |                                                 |
| public void new(str name, DisplayFunctionType displayType, Types returnType, int returnTypeId, boolean isStatic) | Initializes a new instance of the Object class. |
| public void finalize()                                                                                           |                                                 |

## Method displayType

```xpp
public DisplayFunctionType displayType()
```

### Return Value - displayType

## Method isStatic

```xpp
public boolean isStatic()
```

### Return Value - isStatic

## Method name

```xpp
public str name()
```

### Return Value - name

## Method returnType

```xpp
public Types returnType()
```

### Return Value - returnType

## Method returnTypeId

```xpp
public int returnTypeId()
```

### Return Value - returnTypeId

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(str name, DisplayFunctionType displayType, Types returnType, int returnTypeId, boolean isStatic)
```

### Parameters - new

name  

<!-- -->

displayType  

<!-- -->

returnType  

<!-- -->

returnTypeId  

<!-- -->

isStatic  

## Method finalize

```xpp
public void finalize()
```

