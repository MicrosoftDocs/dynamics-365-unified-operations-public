---
title: SSRSReportConceptNode class
description: This topic describes the SSRSReportConceptNode class.
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

# Class SSRSReportConceptNode

[!include [banner](../../includes/banner.md)]

```xpp
class SSRSReportConceptNode extends xResourceNode
```

The SSRSReportConceptNode class lets you create, read, update, and delete SSRS reports, data sources, style templates, and images in the  Application Object Tree (AOT).

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before calling this API.

## Examples

## Methods

| Method                                                     | Description                                                                   |
|------------------------------------------------------------|-------------------------------------------------------------------------------|
| public str AOTgetSource()                                  | Returns the source code of this node.                                         |
| public str getCrossReferences()                            | Retrieves the cross-references by the specified SSRSReportConceptNode object. |
| public void allowCaching(\[boolean allow\])                |                                                                               |
| public void setCrossReferences(str crossReferences)        | Sets the cross-references by the specified SSRSReportConceptNode object.      |
| public void AOTsetSource(str source, \[boolean isStatic\]) | Sets the source code of this node.                                            |

## Method AOTgetSource

Returns the source code of this node.

```xpp
public str AOTgetSource()
```

### Return Value - AOTgetSource

The string that contains the source code, if any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

### Remarks - AOTgetSource

This function is overridden by nodes that have source code.

## Method getCrossReferences

Retrieves the cross-references by the specified SSRSReportConceptNode object.

```xpp
public str getCrossReferences()
```

### Return Value - getCrossReferences

The cross-references by the specified SSRSReportConceptNode object in XML format.

## Method allowCaching

```xpp
public void allowCaching([boolean allow])
```

### Parameters - allowCaching

allow  

## Method setCrossReferences

Sets the cross-references by the specified SSRSReportConceptNode object.

```xpp
public void setCrossReferences(str crossReferences)
```

### Parameters - setCrossReferences

crossReferences  
The cross-references by the specified SSRSReportConceptNode object in XML format.

### Remarks - setCrossReferences

This method only updates the cross-reference XML stored on the specified SSRSReportConceptNode object. It does not update the cross-reference system.

## Method AOTsetSource

Sets the source code of this node.

```xpp
public void AOTsetSource(str source, [boolean isStatic])
```

### Parameters - AOTsetSource

source  
The value that specifies whether the method is static; optional.

<!-- -->

isStatic  
The value that specifies whether the method is static; optional.

### Remarks - AOTsetSource

This method is overridden by nodes that have source code.

