---
title: QueryBuildStaticlink class
description: This topic describes the QueryBuildStaticlink class.
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

# Class QueryBuildStaticlink

[!include [banner](../../includes/banner.md)]

```xpp
class QueryBuildStaticlink extends Object
```

The QueryBuildStaticLink class provides the information about the static links that are defined on a QueryBuildDataSource class.

## Remarks

## Examples

## Methods

| Method                 | Description                                                         |
|------------------------|---------------------------------------------------------------------|
| public FieldId field() | Provides the field information on which the static link is defined/ |
| public AnyType value() | Gets the value of the field on which the static link is defined.    |
| public void finalize() |                                                                     |

## Method field

Provides the field information on which the static link is defined/

```xpp
public FieldId field()
```

### Return Value - field

The FieldId value of the field on which the static link is defined.

## Method value

Gets the value of the field on which the static link is defined.

```xpp
public AnyType value()
```

### Return Value - value

The value of the static link.

## Method finalize

```xpp
public void finalize()
```

