---
title: IISContextObject class
description: This topic describes the IISContextObject class.
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

# Class IISContextObject

[!include [banner](../../includes/banner.md)]

```xpp
class IISContextObject extends Object
```

## Remarks

## Examples

## Methods

| Method                                                 | Description                                               |
|--------------------------------------------------------|-----------------------------------------------------------|
| public ComInterface interface()                        |                                                           |
| public boolean isTraceEnabled()                        |                                                           |
| public IISVariantDictionary items()                    |                                                           |
| public int traceMode(int mode)                         |                                                           |
| public COMVariant value(str value, \[COMVariant var\]) |                                                           |
| public str valueTxt(str value, \[str var\])            |                                                           |
| public void traceWrite(str category, str message)      |                                                           |
| public void finalize()                                 |                                                           |
| public void traceWarn(str category, str message)       |                                                           |
| public void new()                                      | Initializes a new instance of the IISContextObject class. |

## Method interface

```xpp
public ComInterface interface()
```

### Return Value - interface

## Method isTraceEnabled

```xpp
public boolean isTraceEnabled()
```

### Return Value - isTraceEnabled

## Method items

```xpp
public IISVariantDictionary items()
```

### Return Value - items

## Method traceMode

```xpp
public int traceMode(int mode)
```

### Parameters - traceMode

mode  

### Return Value - traceMode

## Method value

```xpp
public COMVariant value(str value, [COMVariant var])
```

### Parameters - value

value  

<!-- -->

var  

### Return Value - value

## Method valueTxt

```xpp
public str valueTxt(str value, [str var])
```

### Parameters - valueTxt

value  

<!-- -->

var  

### Return Value - valueTxt

## Method traceWrite

```xpp
public void traceWrite(str category, str message)
```

### Parameters - traceWrite

category  

<!-- -->

message  

## Method finalize

```xpp
public void finalize()
```

## Method traceWarn

```xpp
public void traceWarn(str category, str message)
```

### Parameters - traceWarn

category  

<!-- -->

message  

## Method new

Initializes a new instance of the IISContextObject class.

```xpp
public void new()
```

