---
title: MapiRecipDesc class
description: This topic describes the MapiRecipDesc class.
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

# Class MapiRecipDesc

[!include [banner](../../includes/banner.md)]

```xpp
class MapiRecipDesc extends Object
```

## Remarks

## Examples

## Methods

| Method                                    | Description                                                                                                                                   |
|-------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str address(\[str Address\])       |                                                                                                                                               |
| public str name(\[str Name\])             | Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object. |
| public int recipClass(\[int RecipClass\]) |                                                                                                                                               |
| public void new()                         | Initializes a new instance of the MapiRecipDesc class.                                                                                        |
| public void finalize()                    |                                                                                                                                               |

## Method address

```xpp
public str address([str Address])
```

### Parameters - address

Address  

### Return Value - address

## Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object.

```xpp
public str name([str Name])
```

### Parameters - name

Name  

### Return Value - name

The name that is used in the code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

## Method recipClass

```xpp
public int recipClass([int RecipClass])
```

### Parameters - recipClass

RecipClass  

### Return Value - recipClass

## Method new

Initializes a new instance of the MapiRecipDesc class.

```xpp
public void new()
```

## Method finalize

```xpp
public void finalize()
```

