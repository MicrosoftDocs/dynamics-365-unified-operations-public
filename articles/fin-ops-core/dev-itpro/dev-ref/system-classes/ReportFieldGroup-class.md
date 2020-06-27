---
title: ReportFieldGroup class
description: This topic describes the ReportFieldGroup class.
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

# Class ReportFieldGroup

[!include [banner](../../includes/banner.md)]

```xpp
class ReportFieldGroup extends TreeNode
```

The ReportFieldGroup class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                        | Description                                                   |
|-----------------------------------------------|---------------------------------------------------------------|
| public int autoFieldGroupOrder(\[int value\]) |                                                               |
| public str dataGroup(\[str value\])           |                                                               |
| public int fieldCount()                       |                                                               |
| public ReportControl fieldNumber(int number)  |                                                               |
| public TableId table(\[TableId value\])       | Gets or sets the table ID that is associated with the object. |

## Method autoFieldGroupOrder

```xpp
public int autoFieldGroupOrder([int value])
```

### Parameters - autoFieldGroupOrder

value  

### Return Value - autoFieldGroupOrder

## Method dataGroup

```xpp
public str dataGroup([str value])
```

### Parameters - dataGroup

value  

### Return Value - dataGroup

## Method fieldCount

```xpp
public int fieldCount()
```

### Return Value - fieldCount

## Method fieldNumber

```xpp
public ReportControl fieldNumber(int number)
```

### Parameters - fieldNumber

number  

### Return Value - fieldNumber

## Method table

Gets or sets the table ID that is associated with the object.

```xpp
public TableId table([TableId value])
```

### Parameters - table

value  

### Return Value - table

The current value of the table ID that is associated with the object.

