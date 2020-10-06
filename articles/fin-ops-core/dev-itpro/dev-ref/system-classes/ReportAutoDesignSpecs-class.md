---
title: ReportAutoDesignSpecs class
description: This topic describes the ReportAutoDesignSpecs class.
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

# Class ReportAutoDesignSpecs

[!include [banner](../../includes/banner.md)]

```xpp
class ReportAutoDesignSpecs extends TreeNode
```

The ReportAutoDesignSpecs class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                                            | Description                                                        |
|-----------------------------------------------------------------------------------|--------------------------------------------------------------------|
| public ReportSection addProgrammableSection(int number)                           |                                                                    |
| public ReportSection addSection(ReportBlockType sectionType, \[TableId tableId\]) |                                                                    |
| public boolean autoHeader(\[boolean value\])                                      |                                                                    |
| public str footerText(\[str value\])                                              |                                                                    |
| public boolean grandHeader(\[boolean value\])                                     |                                                                    |
| public boolean grandTotal(\[boolean value\])                                      | Determines whether the FooterText property value can be displayed. |
| public str headerText(\[str value\])                                              |                                                                    |
| public boolean view()                                                             |                                                                    |

## Method addProgrammableSection

```xpp
public ReportSection addProgrammableSection(int number)
```

### Parameters - addProgrammableSection

number  

### Return Value - addProgrammableSection

## Method addSection

```xpp
public ReportSection addSection(ReportBlockType sectionType, [TableId tableId])
```

### Parameters - addSection

sectionType  

<!-- -->

tableId  

### Return Value - addSection

## Method autoHeader

```xpp
public boolean autoHeader([boolean value])
```

### Parameters - autoHeader

value  

### Return Value - autoHeader

## Method footerText

```xpp
public str footerText([str value])
```

### Parameters - footerText

value  

### Return Value - footerText

## Method grandHeader

```xpp
public boolean grandHeader([boolean value])
```

### Parameters - grandHeader

value  

### Return Value - grandHeader

## Method grandTotal

Determines whether the FooterText property value can be displayed.

```xpp
public boolean grandTotal([boolean value])
```

### Parameters - grandTotal

value  

### Return Value - grandTotal

true if the FooterText property value is displayed; otherwise, false.

### Remarks - grandTotal

The grandTotal property is available only when a report has untested, multiple data sources.

## Method headerText

```xpp
public str headerText([str value])
```

### Parameters - headerText

value  

### Return Value - headerText

## Method view

```xpp
public boolean view()
```

### Return Value - view

