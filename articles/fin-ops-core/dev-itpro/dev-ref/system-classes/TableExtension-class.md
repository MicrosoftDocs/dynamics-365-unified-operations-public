---
title: TableExtension class
description: This topic describes the TableExtension class.
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

# Class TableExtension

[!include [banner](../../includes/banner.md)]


```xpp
class TableExtension extends Object
```

## Remarks

## Examples

## Methods

| Method                                                    | Description                                             |
|-----------------------------------------------------------|---------------------------------------------------------|
| public void new()                                         | Initializes a new instance of the TableExtension class. |
| public void modifiedField(Common record, FieldId fieldId) |                                                         |
| public void defaultRow(Common record)                     |                                                         |
| public void defaultField(Common record, FieldId fieldId)  |                                                         |

## Method new

Initializes a new instance of the TableExtension class.

```xpp
public void new()
```

## Method modifiedField

```xpp
public void modifiedField(Common record, FieldId fieldId)
```

### Parameters - modifiedField

record  

<!-- -->

fieldId  

## Method defaultRow

```xpp
public void defaultRow(Common record)
```

### Parameters - defaultRow

record  

## Method defaultField

```xpp
public void defaultField(Common record, FieldId fieldId)
```

### Parameters - defaultField

record  

<!-- -->

fieldId  

