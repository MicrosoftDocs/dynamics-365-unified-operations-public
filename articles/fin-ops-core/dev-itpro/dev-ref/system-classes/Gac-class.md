---
title: Gac class
description: This topic describes the Gac class.
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

# Class Gac

[!include [banner](../../includes/banner.md)]


```xpp
class Gac extends Object
```

The Gac class lets you enumerate the assemblies of the global assembly cache (GAC).

## Remarks

## Examples

## Methods

| Method                                 | Description                                                   |
|----------------------------------------|---------------------------------------------------------------|
| public container enumerateAssemblies() | Enumerates the assemblies of the global assembly cache (GAC). |
| public void new()                      | Initializes a new instance of the Gac class.                  |

## Method enumerateAssemblies

Enumerates the assemblies of the global assembly cache (GAC).

```xpp
public container enumerateAssemblies()
```

### Return Value - enumerateAssemblies

A container that represents the assemblies of the GAC.

## Method new

Initializes a new instance of the Gac class.

```xpp
public void new()
```


