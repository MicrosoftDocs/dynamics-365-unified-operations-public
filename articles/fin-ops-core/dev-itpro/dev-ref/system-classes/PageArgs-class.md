---
title: PageArgs class
description: This topic describes the PageArgs class.
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

# Class PageArgs

[!include [banner](../../includes/banner.md)]

```xpp
class PageArgs extends Object
```

The PageArgs class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                         | Description                                                                                                 |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| public int enumParameter(\[int value\])        | Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class. |
| public int enumTypeParameter(\[int value\])    | Gets or sets the enumTypeParameter property for the MenuFunction class.                                     |
| public Common externalRecord(\[Common value\]) |                                                                                                             |
| public str menuItemName(\[str value\])         |                                                                                                             |
| public str parameters(\[str value\])           | Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.      |
| public void new()                              | Initializes a new instance of the PageArgs class.                                                           |

## Method enumParameter

Gets or sets the enumParameter property that is passed to the object that is run by the MenuFunction class.

```xpp
public int enumParameter([int value])
```

### Parameters - enumParameter

value  

### Return Value - enumParameter

The enumParameter property that is passed to the object that is run by the MenuFunction class.

## Method enumTypeParameter

Gets or sets the enumTypeParameter property for the MenuFunction class.

```xpp
public int enumTypeParameter([int value])
```

### Parameters - enumTypeParameter

value  

### Return Value - enumTypeParameter

The enumTypeParameter property for the MenuFunction class.

## Method externalRecord

```xpp
public Common externalRecord([Common value])
```

### Parameters - externalRecord

value  

### Return Value - externalRecord

## Method menuItemName

```xpp
public str menuItemName([str value])
```

### Parameters - menuItemName

value  

### Return Value - menuItemName

## Method parameters

Gets or sets the list of parameters that are passed to objects that are run by the MenuFunction class.

```xpp
public str parameters([str value])
```

### Parameters - parameters

value  

### Return Value - parameters

The list of parameters that are passed to the object.

### Remarks - parameters

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on. Objects ignore passed, unrecognized parameters.

## Method new

Initializes a new instance of the PageArgs class.

```xpp
public void new()
```

