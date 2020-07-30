---
title: FormTreeItem class
description: This topic describes the FormTreeItem class.
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

# Class FormTreeItem

[!include [banner](../../includes/banner.md)]

```xpp
class FormTreeItem extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                           | Description                                                                |
|----------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| public int children(\[int value\])                                               |                                                                            |
| public AnyType data(\[AnyType value\])                                           |                                                                            |
| public int idx()                                                                 |                                                                            |
| public int image(\[int value\])                                                  |                                                                            |
| public int overlayImage(\[int value\])                                           |                                                                            |
| public int selectedImage(\[int value\])                                          |                                                                            |
| public boolean stateBold(\[boolean value\])                                      |                                                                            |
| public FormTreeCheckedState stateChecked(\[FormTreeCheckedState value\])         |                                                                            |
| public boolean stateCut(\[boolean value\])                                       |                                                                            |
| public boolean stateDropHilited(\[boolean value\])                               |                                                                            |
| public boolean stateExpanded(\[boolean value\])                                  |                                                                            |
| public boolean stateExpandedOnce(\[boolean value\])                              |                                                                            |
| public int stateImage(\[int value\])                                             |                                                                            |
| public boolean stateSelected(\[boolean value\])                                  |                                                                            |
| public str text(\[str value\])                                                   | Sets or returns the text for the control.                                  |
| public str toString()                                                            | Returns a string representation of the instance of the FormTreeItem class. |
| public void new(\[str Text\], \[int Image\], \[int children\], \[AnyType Data\]) | Initializes a new instance of the Object class.                            |
| public void finalize()                                                           |                                                                            |

## Method children

```xpp
public int children([int value])
```

### Parameters - children

value  

### Return Value - children

## Method data

```xpp
public AnyType data([AnyType value])
```

### Parameters - data

value  

### Return Value - data

## Method idx

```xpp
public int idx()
```

### Return Value - idx

## Method image

```xpp
public int image([int value])
```

### Parameters - image

value  

### Return Value - image

## Method overlayImage

```xpp
public int overlayImage([int value])
```

### Parameters - overlayImage

value  

### Return Value - overlayImage

## Method selectedImage

```xpp
public int selectedImage([int value])
```

### Parameters - selectedImage

value  

### Return Value - selectedImage

## Method stateBold

```xpp
public boolean stateBold([boolean value])
```

### Parameters - stateBold

value  

### Return Value - stateBold

## Method stateChecked

```xpp
public FormTreeCheckedState stateChecked([FormTreeCheckedState value])
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

## Method stateExpanded

```xpp
public boolean stateExpanded([boolean value])
```

### Parameters - stateExpanded

value  

### Return Value - stateExpanded

## Method stateExpandedOnce

```xpp
public boolean stateExpandedOnce([boolean value])
```

### Parameters - stateExpandedOnce

value  

### Return Value - stateExpandedOnce

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

## Method text

Sets or returns the text for the control.

```xpp
public str text([str value])
```

### Parameters - text

value  
The value to assign as the text for the control; optional.

### Return Value - text

The text for the control; an empty string if no text has been assigned to the control.

## Method toString

Returns a string representation of the instance of the FormTreeItem class.

```xpp
public str toString()
```

### Return Value - toString

A string that contains a description of the instance of the FormTreeItem class.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type.

### Examples - toString

The following example shows how to use the toString method.

```xpp
print objFormTreeItem.toString();
```

## Method new

Initializes a new instance of the Object class.

```xpp
public void new([str Text], [int Image], [int children], [AnyType Data])
```

### Parameters - new

Text  

<!-- -->

Image  

<!-- -->

children  

<!-- -->

Data  

## Method finalize

```xpp
public void finalize()
```

