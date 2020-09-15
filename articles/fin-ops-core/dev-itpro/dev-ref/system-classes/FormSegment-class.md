---
title: FormSegment class
description: This topic describes the FormSegment class.
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

# Class FormSegment

[!include [banner](../../includes/banner.md)]

```xpp
class FormSegment extends Object
```

The FormSegment class is used to represent a segment in the SegmentedEntry control.

## Remarks

## Examples

## Methods

| Method                                                          | Description                            |
|-----------------------------------------------------------------|----------------------------------------|
| public str text()                                               | Gets the current text of the segment.  |
| public boolean allowEdit(\[boolean value\])                     |                                        |
| public str description(\[str description\])                     |                                        |
| public boolean enabled(\[boolean value\])                       |                                        |
| public int getIndex()                                           |                                        |
| public str name()                                               |                                        |
| public SegmentedEntryState state(\[SegmentedEntryState state\]) |                                        |
| public str value(\[str value\])                                 | Gets the current value of the segment. |

## Method text

Gets the current text of the segment.

```xpp
public str text()
```

### Return Value - text

The current text of the segment.

### Remarks - text

This method always returns the current text of the segment, even while it is being modified. To retrieve the last value that was persisted for the segment, use the value method.

## Method allowEdit

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  

### Return Value - allowEdit

## Method description

```xpp
public str description([str description])
```

### Parameters - description

description  

### Return Value - description

## Method enabled

```xpp
public boolean enabled([boolean value])
```

### Parameters - enabled

value  

### Return Value - enabled

## Method getIndex

```xpp
public int getIndex()
```

### Return Value - getIndex

## Method name

```xpp
public str name()
```

### Return Value - name

## Method state

```xpp
public SegmentedEntryState state([SegmentedEntryState state])
```

### Parameters - state

state  

### Return Value - state

## Method value

Gets the current value of the segment.

```xpp
public str value([str value])
```

### Parameters - value

value  

### Return Value - value

The current value of the segment.

### Remarks - value

This method always returns the current persisted value of the segment, even while it is being modified. To retrieve the current text of the control while it is being modified, use the text method.

