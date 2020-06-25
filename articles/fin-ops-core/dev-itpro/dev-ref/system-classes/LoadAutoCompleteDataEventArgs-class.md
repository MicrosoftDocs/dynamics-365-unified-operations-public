---
title: LoadAutoCompleteDataEventArgs class
description: This topic describes the LoadAutoCompleteDataEventArgs class.
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

# Class LoadAutoCompleteDataEventArgs

[!include [banner](../../includes/banner.md)]

```xpp
class LoadAutoCompleteDataEventArgs extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                          | Description |
|-------------------------------------------------------------------------------------------------|-------------|
| public AutoCompleteDataMode autoCompleteDataMode(\[AutoCompleteDataMode autoCompleteDataMode\]) |             |
| public boolean canPage(\[boolean canPage\])                                                     |             |
| public str filterValue()                                                                        |             |
| public AnyType lastPagedTag()                                                                   |             |
| public FormSegment segment()                                                                    |             |
| public void addAutoCompleteData(str value, str description, AnyType tag)                        |             |

## Method autoCompleteDataMode

```xpp
public AutoCompleteDataMode autoCompleteDataMode([AutoCompleteDataMode autoCompleteDataMode])
```

### Parameters - autoCompleteDataMode

autoCompleteDataMode  

### Return Value - autoCompleteDataMode

## Method canPage

```xpp
public boolean canPage([boolean canPage])
```

### Parameters - canPage

canPage  

### Return Value - canPage

## Method filterValue

```xpp
public str filterValue()
```

### Return Value - filterValue

## Method lastPagedTag

```xpp
public AnyType lastPagedTag()
```

### Return Value - lastPagedTag

## Method segment

```xpp
public FormSegment segment()
```

### Return Value - segment

## Method addAutoCompleteData

```xpp
public void addAutoCompleteData(str value, str description, AnyType tag)
```

### Parameters - addAutoCompleteData

value  

<!-- -->

description  

<!-- -->

tag  

