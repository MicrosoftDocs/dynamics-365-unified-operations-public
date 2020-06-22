---
title: FormListItem class
description: This topic describes the FormListItem class.
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

# Class FormListItem

[!include [banner](../../includes/banner.md)]

```xpp
class FormListItem extends Object
```

## Remarks

## Examples

## Methods

| Method                                                         | Description                                          |
|----------------------------------------------------------------|------------------------------------------------------|
| public AnyType data(\[AnyType value\])                         |                                                      |
| public int idx(\[int value\])                                  |                                                      |
| public int image(\[int value\])                                |                                                      |
| public int indent(\[int value\])                               |                                                      |
| public int overlayImage(\[int value\])                         |                                                      |
| public boolean stateChecked(\[boolean value\])                 |                                                      |
| public boolean stateCut(\[boolean value\])                     |                                                      |
| public boolean stateDropHilited(\[boolean value\])             |                                                      |
| public boolean stateFocus(\[boolean value\])                   |                                                      |
| public int stateImage(\[int value\])                           |                                                      |
| public boolean stateSelected(\[boolean value\])                |                                                      |
| public int subItem(\[int value\])                              |                                                      |
| public str text(\[str value\])                                 |                                                      |
| public str toString()                                          | Returns a string that represents the current object. |
| public void finalize()                                         |                                                      |
| public void new(\[str Text\], \[int Image\], \[AnyType Data\]) | Initializes a new instance of the Object class.      |

## Method data

```xpp
public AnyType data([AnyType value])
```

### Parameters - data

value  

### Return Value - data

## Method idx

```xpp
public int idx([int value])
```

### Parameters - idx

value  

### Return Value - idx

## Method image

```xpp
public int image([int value])
```

### Parameters - image

value  

### Return Value - image

## Method indent

```xpp
public int indent([int value])
```

### Parameters - indent

value  

### Return Value - indent

## Method overlayImage

```xpp
public int overlayImage([int value])
```

### Parameters - overlayImage

value  

### Return Value - overlayImage

## Method stateChecked

```xpp
public boolean stateChecked([boolean value])
```

### Parameters - stateChecked

value  

### Return Value - stateChecked

## Method stateCut

```xpp
public boolean stateCut([boolean value])
```

### Parameters - stateCut

value  

### Return Value - stateCut

## Method stateDropHilited

```xpp
public boolean stateDropHilited([boolean value])
```

### Parameters - stateDropHilited

value  

### Return Value - stateDropHilited

## Method stateFocus

```xpp
public boolean stateFocus([boolean value])
```

### Parameters - stateFocus

value  

### Return Value - stateFocus

## Method stateImage

```xpp
public int stateImage([int value])
```

### Parameters - stateImage

value  

### Return Value - stateImage

## Method stateSelected

```xpp
public boolean stateSelected([boolean value])
```

### Parameters - stateSelected

value  

### Return Value - stateSelected

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

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new([str Text], [int Image], [AnyType Data])
```

### Parameters - new

Text  

<!-- -->

Image  

<!-- -->

Data  

