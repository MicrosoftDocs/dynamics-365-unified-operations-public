---
title: RelativeFieldBinding class
description: This topic describes the RelativeFieldBinding class.
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

# Class RelativeFieldBinding

[!include [banner](../../includes/banner.md)]

```xpp
class RelativeFieldBinding extends FieldBinding
```

## Remarks

## Examples

## Methods

| Method                                                                                   | Description                                                   |
|------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| public RelationPath relationPath()                                                       |                                                               |
| ::public static RelativeFieldBinding construct(str fieldName, RelationPath relationPath) |                                                               |
| ::public static RelativeFieldBinding create(container packedRelativeFieldBinding)        |                                                               |
| private void new()                                                                       | Initializes a new instance of the RelativeFieldBinding class. |

## Method relationPath

```xpp
public RelationPath relationPath()
```

### Return Value - relationPath

## Method construct

```xpp
public static RelativeFieldBinding construct(str fieldName, RelationPath relationPath)
```

### Parameters - construct

fieldName  

<!-- -->

relationPath  

### Return Value - construct

## Method create

```xpp
public static RelativeFieldBinding create(container packedRelativeFieldBinding)
```

### Parameters - create

packedRelativeFieldBinding  

### Return Value - create

## Method new

Initializes a new instance of the RelativeFieldBinding class.

```xpp
private void new()
```

