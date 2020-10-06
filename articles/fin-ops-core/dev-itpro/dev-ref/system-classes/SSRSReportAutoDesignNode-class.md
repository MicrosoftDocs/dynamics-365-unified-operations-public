---
title: SSRSReportAutoDesignNode class
description: This topic describes the SSRSReportAutoDesignNode class.
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

# Class SSRSReportAutoDesignNode

[!include [banner](../../includes/banner.md)]

```xpp
class SSRSReportAutoDesignNode extends SSRSReportDesignNode
```

## Remarks

## Examples

## Methods

| Method                                              | Description                                                                        |
|-----------------------------------------------------|------------------------------------------------------------------------------------|
| public str getCrossReferences()                     | Retrieves the cross-references by using the specified SSRSReportDesignNode object. |
| public void setCrossReferences(str crossReferences) | Sets the cross-references by using the specified SSRSReportDesignNode object.      |

## Method getCrossReferences

Retrieves the cross-references by using the specified SSRSReportDesignNode object.

```xpp
public str getCrossReferences()
```

### Return Value - getCrossReferences

The cross-references in XML format.

## Method setCrossReferences

Sets the cross-references by using the specified SSRSReportDesignNode object.

```xpp
public void setCrossReferences(str crossReferences)
```

### Parameters - setCrossReferences

crossReferences  
The cross-references in XML format.

### Remarks - setCrossReferences

This method only updates the cross-reference XML stored on the specified SSRSReportDesignNode object. It does not update the cross-reference system.

