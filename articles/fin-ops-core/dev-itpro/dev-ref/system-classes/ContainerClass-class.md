---
title: ContainerClass class
description: This topic describes the ContainerClass class.
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

# Class ContainerClass

[!include [banner](../../includes/banner.md)]

```xpp
class ContainerClass extends Object
```

## Remarks

## Examples

## Methods

| Method                                                              | Description                                          |
|---------------------------------------------------------------------|------------------------------------------------------|
| public int length()                                                 |                                                      |
| public container toBlob()                                           |                                                      |
| public str toString()                                               | Returns a string that represents the current object. |
| public container value()                                            |                                                      |
| ::public static container blob2Container(container blob\_container) |                                                      |
| ::public static int containerLength(container container)            |                                                      |
| public void new(container container)                                | Initializes a new instance of the Object class.      |

## Method length

```xpp
public int length()
```

### Return Value - length

## Method toBlob

```xpp
public container toBlob()
```

### Return Value - toBlob

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the SysMethodInfo class returns the method name and type of the method, such as instance or static.

## Method value

```xpp
public container value()
```

### Return Value - value

## Method blob2Container

```xpp
public static container blob2Container(container blob_container)
```

### Parameters - blob2Container

blob\_container  

### Return Value - blob2Container

## Method containerLength

```xpp
public static int containerLength(container container)
```

### Parameters - containerLength

container  

### Return Value - containerLength

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(container container)
```

### Parameters - new

container  

