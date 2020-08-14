---
title: FormDesignView class
description: This topic describes the FormDesignView class.
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

# Class FormDesignView

[!include [banner](../../includes/banner.md)]

```xpp
class FormDesignView extends ObjectRun
```

## Remarks

## Examples

## Methods

| Method                                                 | Description                                     |
|--------------------------------------------------------|-------------------------------------------------|
| public FormBuildDesign design(\[int value\])           |                                                 |
| public Form form(\[Form value\])                       |                                                 |
| public str name()                                      |                                                 |
| public FormBuildObjectSet objectPool(\[AnyType pool\]) |                                                 |
| public void finalize()                                 |                                                 |
| public void new(\[str name\], \[Form form\])           | Initializes a new instance of the Object class. |

## Method design

```xpp
public FormBuildDesign design([int value])
```

### Parameters - design

value  

### Return Value - design

## Method form

```xpp
public Form form([Form value])
```

### Parameters - form

value  

### Return Value - form

## Method name

```xpp
public str name()
```

### Return Value - name

## Method objectPool

```xpp
public FormBuildObjectSet objectPool([AnyType pool])
```

### Parameters - objectPool

pool  

### Return Value - objectPool

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new([str name], [Form form])
```

### Parameters - new

name  

<!-- -->

form  

