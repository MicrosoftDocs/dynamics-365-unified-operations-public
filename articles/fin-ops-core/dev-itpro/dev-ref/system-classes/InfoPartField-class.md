---
title: InfoPartField class
description: This topic describes the InfoPartField class.
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

# Class InfoPartField

[!include [banner](../../includes/banner.md)]

```xpp
class InfoPartField extends TreeNode
```

## Remarks

## Examples

## Methods

| Method                                            | Description                                                                                                                               |
|---------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str dataField(\[str value\])               |                                                                                                                                           |
| public str dataMethod(\[str value\])              |                                                                                                                                           |
| public str dataSource(\[str value\])              | Gets or sets a data source that will be used by the control or the form.                                                                  |
| public str label(\[str value\])                   | Gets or sets the label for a control.                                                                                                     |
| public boolean manualRetrieval(\[boolean value\]) |                                                                                                                                           |
| public str name(\[str value\])                    | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object. |
| public int style(\[int value\])                   |                                                                                                                                           |
| public void new()                                 | Initializes a new instance of the InfoPartField class.                                                                                    |

## Method dataField

```xpp
public str dataField([str value])
```

### Parameters - dataField

value  

### Return Value - dataField

## Method dataMethod

```xpp
public str dataMethod([str value])
```

### Parameters - dataMethod

value  

### Return Value - dataMethod

## Method dataSource

Gets or sets a data source that will be used by the control or the form.

```xpp
public str dataSource([str value])
```

### Parameters - dataSource

value  

### Return Value - dataSource

The identifier of the data source that will be used.

## Method label

Gets or sets the label for a control.

```xpp
public str label([str value])
```

### Parameters - label

value  

### Return Value - label

The current value of the label string.

### Remarks - label

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

## Method manualRetrieval

```xpp
public boolean manualRetrieval([boolean value])
```

### Parameters - manualRetrieval

value  

### Return Value - manualRetrieval

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

## Method style

```xpp
public int style([int value])
```

### Parameters - style

value  

### Return Value - style

## Method new

Initializes a new instance of the InfoPartField class.

```xpp
public void new()
```

