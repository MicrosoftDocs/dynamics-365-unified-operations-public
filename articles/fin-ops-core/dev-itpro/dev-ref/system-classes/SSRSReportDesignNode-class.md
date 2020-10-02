---
title: SSRSReportDesignNode class
description: This topic describes the SSRSReportDesignNode class.
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

# Class SSRSReportDesignNode

[!include [banner](../../includes/banner.md)]

```xpp
class SSRSReportDesignNode extends xResourceNode
```

The SSRSReportDesignNode class lets you create, read, update, and delete Microsoft SQL Server Reporting Services reports, data sources, style templates, and images in the  Application Object Tree (AOT).

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before calling this API.

## Examples

## Methods

| Method                                              | Description                                                                  |
|-----------------------------------------------------|------------------------------------------------------------------------------|
| public str getCrossReferences()                     | Retrieves the cross-references by the specified SSRSReportDesignNode object. |
| public void setCrossReferences(str crossReferences) | Sets the cross-references by the specified SSRSReportDesignNode object.      |

## Method getCrossReferences

Retrieves the cross-references by the specified SSRSReportDesignNode object.

```xpp
public str getCrossReferences()
```

### Return Value - getCrossReferences

The cross-references by the specified SSRSReportDesignNode object in XML format.

## Method setCrossReferences

Sets the cross-references by the specified SSRSReportDesignNode object.

```xpp
public void setCrossReferences(str crossReferences)
```

### Parameters - setCrossReferences

crossReferences  
The cross-references by the specified SSRSReportDesignNode object in XML format.

### Remarks - setCrossReferences

This method only updates the cross-reference XML stored on the specified SSRSReportDesignNode object. It does not update the cross-reference system.

