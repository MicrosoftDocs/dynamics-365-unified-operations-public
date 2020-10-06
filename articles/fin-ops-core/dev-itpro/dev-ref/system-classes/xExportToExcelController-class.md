---
title: xExportToExcelController class
description: This topic describes the xExportToExcelController class.
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

# Class xExportToExcelController

[!include [banner](../../includes/banner.md)]

```xpp
class xExportToExcelController extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                             | Description |
|------------------------------------------------------------------------------------------------------------------------------------|-------------|
| public boolean export()                                                                                                            |             |
| public boolean exportGrid(FormGridControl gridControl, boolean onlyMarkedRows)                                                     |             |
| public boolean performStaticExport(xFormRun formRun, FormGridControl gridControl, System.IO.Stream stream, boolean onlyMarkedRows) |             |
| public void new()                                                                                                                  |             |

## Method export

```xpp
public boolean export()
```

### Return Value - export

## Method exportGrid

```xpp
public boolean exportGrid(FormGridControl gridControl, boolean onlyMarkedRows)
```

### Parameters - exportGrid

gridControl  

<!-- -->

onlyMarkedRows  

### Return Value - exportGrid

## Method performStaticExport

```xpp
public boolean performStaticExport(xFormRun formRun, FormGridControl gridControl, System.IO.Stream stream, boolean onlyMarkedRows)
```

### Parameters - performStaticExport

formRun  

<!-- -->

gridControl  

<!-- -->

stream  

<!-- -->

onlyMarkedRows  

### Return Value - performStaticExport

## Method new

```xpp
public void new()
```

