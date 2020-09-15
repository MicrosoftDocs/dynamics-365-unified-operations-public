---
title: CueReference class
description: This topic describes the CueReference class.
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

# Class CueReference

[!include [banner](../../includes/banner.md)]

```xpp
class CueReference extends TreeNode
```

## Remarks

## Examples

## Methods

| Method                                | Description                                                                                                                       |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| public str cue(\[str value\])         |                                                                                                                                   |
| public str name(\[str value\])        | Gets or sets the name used in code to identify a form, report, table, query, or other application object. |
| public void new(str cueReferenceName) | Initializes a new instance of the TreeNode class.                                                                                 |

## Method cue

```xpp
public str cue([str value])
```

### Parameters - cue

value  

### Return Value - cue

## Method name

Gets or sets the name used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

The name used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Does not exceed 250 characters.
-   Can include numbers and underscore characters.
-   Does not include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enumerations, classes, and other public objects.

## Method new

Initializes a new instance of the TreeNode class.

```xpp
public void new(str cueReferenceName)
```

### Parameters - new

cueReferenceName  
The name to use to identify this form, report, table, query, or other application object.



