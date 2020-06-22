---
title: ProgressWindow class
description: This topic describes the ProgressWindow class.
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

# Class ProgressWindow

[!include [banner](../../includes/banner.md)]

```xpp
class ProgressWindow extends Object
```

## Remarks

## Examples

## Methods

| Method                                                      | Description                                             |
|-------------------------------------------------------------|---------------------------------------------------------|
| public int addProgressControl(\[int progressControlCount\]) |                                                         |
| public void ProgressBarVisible(int index, int visible)      |                                                         |
| public void ProgressValue(int index, int progressValue)     |                                                         |
| public void ControlMinMax(int index, int min, int max)      |                                                         |
| public void ProgressTextVisible(int index, int visible)     |                                                         |
| public void Animation(str animation)                        |                                                         |
| public void ControlText(int index, str text)                |                                                         |
| public void FormCaption(str text)                           |                                                         |
| public void ControlTime(str text)                           |                                                         |
| public void finalize()                                      |                                                         |
| public void new()                                           | Initializes a new instance of the ProgressWindow class. |

## Method addProgressControl

```xpp
public int addProgressControl([int progressControlCount])
```

### Parameters - addProgressControl

progressControlCount  

### Return Value - addProgressControl

## Method ProgressBarVisible

```xpp
public void ProgressBarVisible(int index, int visible)
```

### Parameters - ProgressBarVisible

index  

<!-- -->

visible  

## Method ProgressValue

```xpp
public void ProgressValue(int index, int progressValue)
```

### Parameters - ProgressValue

index  

<!-- -->

progressValue  

## Method ControlMinMax

```xpp
public void ControlMinMax(int index, int min, int max)
```

### Parameters - ControlMinMax

index  

<!-- -->

min  

<!-- -->

max  

## Method ProgressTextVisible

```xpp
public void ProgressTextVisible(int index, int visible)
```

### Parameters - ProgressTextVisible

index  

<!-- -->

visible  

## Method Animation

```xpp
public void Animation(str animation)
```

### Parameters - Animation

animation  

## Method ControlText

```xpp
public void ControlText(int index, str text)
```

### Parameters - ControlText

index  

<!-- -->

text  

## Method FormCaption

```xpp
public void FormCaption(str text)
```

### Parameters - FormCaption

text  

## Method ControlTime

```xpp
public void ControlTime(str text)
```

### Parameters - ControlTime

text  

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the ProgressWindow class.

```xpp
public void new()
```

