---
title: FormPart class
description: This topic describes the FormPart class.
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

# Class FormPart

[!include [banner](../../includes/banner.md)]

```xpp
class FormPart extends TreeNode
```

## Remarks

## Examples

## Methods

| Method                                       | Description                                                                                                                               |
|----------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str caption(\[str value\])            | Gets or set the caption of the control.                                                                                                   |
| public str form(\[str value\])               |                                                                                                                                           |
| public str managedContentItem(\[str value\]) |                                                                                                                                           |
| public str name(\[str value\])               | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public Guid origin(\[Guid value\])           |                                                                                                                                           |
| public void new()                            | Initializes a new instance of the FormPart class.                                                                                         |

## Method caption

Gets or set the caption of the control.

```xpp
public str caption([str value])
```

### Parameters - caption

value  

### Return Value - caption

The string that is used as the caption of the control.

## Method form

```xpp
public str form([str value])
```

### Parameters - form

value  

### Return Value - form

## Method managedContentItem

```xpp
public str managedContentItem([str value])
```

### Parameters - managedContentItem

value  

### Return Value - managedContentItem

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

## Method origin

```xpp
public Guid origin([Guid value])
```

### Parameters - origin

value  

### Return Value - origin

## Method new

Initializes a new instance of the FormPart class.

```xpp
public void new()
```

