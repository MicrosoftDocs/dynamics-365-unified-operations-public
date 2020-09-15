---
title: FormListColumn class
description: This topic describes the FormListColumn class.
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

# Class FormListColumn

[!include [banner](../../includes/banner.md)]

```xpp
class FormListColumn extends Object
```

The FormListColumn class provides list column functionality for a form.

## Remarks

## Examples

## Methods

| Method                                                      | Description                                               |
|-------------------------------------------------------------|-----------------------------------------------------------|
| public FormListFormat format(\[FormListFormat value\])      |                                                           |
| public int image(\[int value\])                             |                                                           |
| public int order(\[int value\])                             |                                                           |
| public int subItem(\[int value\])                           |                                                           |
| public str text(\[str value\])                              |                                                           |
| public str toString()                                       | Returns a string that contains the class handle and name. |
| public int width(\[int value\])                             | Gets or sets the width of the control.                    |
| public void new(\[str Text\], \[int ColNo\], \[int Width\]) | Initializes a new instance of the Object class.           |
| public void finalize()                                      |                                                           |

## Method format

```xpp
public FormListFormat format([FormListFormat value])
```

### Parameters - format

value  

### Return Value - format

## Method image

```xpp
public int image([int value])
```

### Parameters - image

value  

### Return Value - image

## Method order

```xpp
public int order([int value])
```

### Parameters - order

value  

### Return Value - order

## Method subItem

```xpp
public int subItem([int value])
```

### Parameters - subItem

value  

### Return Value - subItem

## Method text

```xpp
public str text([str value])
```

### Parameters - text

value  

### Return Value - text

## Method toString

Returns a string that contains the class handle and name.

```xpp
public str toString()
```

### Return Value - toString

A text representation of the class.

## Method width

Gets or sets the width of the control.

```xpp
public int width([int value])
```

### Parameters - width

value  
The value to assign as the width of the list column; optional.

### Return Value - width

The width of the control in pixels.

### Remarks - width

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table.

| Mode             | Width calculation                                                                         |
|------------------|-------------------------------------------------------------------------------------------|
| -1 � Exact       | The exact width of the control in pixels is used.                                         |
| 0 � Auto         | The width of the control is calculated automatically, and the value parameter is ignored. |
| 1 � Column width | The layout of the form determines the width of the control.                               |

The width and the width calculation mode can be set separately.

## Method new

Initializes a new instance of the Object class.

```xpp
public void new([str Text], [int ColNo], [int Width])
```

### Parameters - new

Text  

<!-- -->

ColNo  

<!-- -->

Width  

## Method finalize

```xpp
public void finalize()
```

