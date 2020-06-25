---
title: WebDisplayContentItem class
description: This topic describes the WebDisplayContentItem class.
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

# Class WebDisplayContentItem

[!include [banner](../../includes/banner.md)]

```xpp
class WebDisplayContentItem extends WebContentItem
```

The WebDisplayContentItem class enables you to create, read, update, and delete X++ code and metadata.

## Remarks

This class enables you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before calling this API.

## Examples

## Methods

| Method                    | Description                          |
|---------------------------|--------------------------------------|
| public void new(str name) | Creates a new WebDisplayContentItem. |

## Method new

Creates a new WebDisplayContentItem.

```xpp
public void new(str name)
```

### Parameters - new

name  

