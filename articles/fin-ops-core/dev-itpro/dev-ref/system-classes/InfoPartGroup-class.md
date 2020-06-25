---
title: InfoPartGroup class
description: This topic describes the InfoPartGroup class.
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

# Class InfoPartGroup

[!include [banner](../../includes/banner.md)]

```xpp
class InfoPartGroup extends TreeNode
```

## Remarks

## Examples

## Methods

| Method                                                         | Description                                                                                                                                   |
|----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public str caption(\[str value\])                              | Gets or sets the caption of the control.                                                                                                      |
| public str dataGroup(\[str value\])                            |                                                                                                                                               |
| public str dataSource(\[str value\])                           | Gets or sets a data source that will be used by the control or the form.                                                                      |
| public int labelPosition(\[int value\])                        |                                                                                                                                               |
| public str name(\[str value\])                                 | Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object. |
| public boolean repeating(\[boolean value\])                    |                                                                                                                                               |
| public int rowCountWhenSmall(\[int value\], \[AutoMode mode\]) |                                                                                                                                               |
| public AutoMode rowCountWhenSmallMode(\[AutoMode mode\])       |                                                                                                                                               |
| public int rowCountWhenSmallValue(\[int value\])               |                                                                                                                                               |
| public boolean showCaption(\[boolean value\])                  |                                                                                                                                               |
| public boolean showLabels(\[boolean value\])                   |                                                                                                                                               |
| public int showWhenPartSize(\[int value\])                     |                                                                                                                                               |
| public boolean verticalSpacing(\[boolean value\])              |                                                                                                                                               |
| public void new()                                              | Initializes a new instance of the InfoPartGroup class.                                                                                        |

## Method caption

Gets or sets the caption of the control.

```xpp
public str caption([str value])
```

### Parameters - caption

value  

### Return Value - caption

The string that is used as the caption of the control.

## Method dataGroup

```xpp
public str dataGroup([str value])
```

### Parameters - dataGroup

value  

### Return Value - dataGroup

## Method dataSource

Gets or sets a data source that will be used by the control or the form.

```xpp
public str dataSource([str value])
```

### Parameters - dataSource

value  

### Return Value - dataSource

The identifier of the data source that will be used.

## Method labelPosition

```xpp
public int labelPosition([int value])
```

### Parameters - labelPosition

value  

### Return Value - labelPosition

## Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  

### Return Value - name

The name that is used in the code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

## Method repeating

```xpp
public boolean repeating([boolean value])
```

### Parameters - repeating

value  

### Return Value - repeating

## Method rowCountWhenSmall

```xpp
public int rowCountWhenSmall([int value], [AutoMode mode])
```

### Parameters - rowCountWhenSmall

value  

<!-- -->

mode  

### Return Value - rowCountWhenSmall

## Method rowCountWhenSmallMode

```xpp
public AutoMode rowCountWhenSmallMode([AutoMode mode])
```

### Parameters - rowCountWhenSmallMode

mode  

### Return Value - rowCountWhenSmallMode

## Method rowCountWhenSmallValue

```xpp
public int rowCountWhenSmallValue([int value])
```

### Parameters - rowCountWhenSmallValue

value  

### Return Value - rowCountWhenSmallValue

## Method showCaption

```xpp
public boolean showCaption([boolean value])
```

### Parameters - showCaption

value  

### Return Value - showCaption

## Method showLabels

```xpp
public boolean showLabels([boolean value])
```

### Parameters - showLabels

value  

### Return Value - showLabels

## Method showWhenPartSize

```xpp
public int showWhenPartSize([int value])
```

### Parameters - showWhenPartSize

value  

### Return Value - showWhenPartSize

## Method verticalSpacing

```xpp
public boolean verticalSpacing([boolean value])
```

### Parameters - verticalSpacing

value  

### Return Value - verticalSpacing

## Method new

Initializes a new instance of the InfoPartGroup class.

```xpp
public void new()
```

