---
title: WinAPINative class
description: This topic describes the WinAPINative class.
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

# Class WinAPINative

[!include [banner](../../includes/banner.md)]

```xpp
class WinAPINative extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                  | Description                                           |
|-------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| ::public static Int64 createFontIndirect(Binary logfont)                                                                |                                                       |
| ::public static boolean deleteObject(Int64 hGDIObject)                                                                  |                                                       |
| ::public static boolean getCharABCWidthsI(Int64 hDC, Int64 firstGlyphIndex, Int64 glyphIndicesCount, Binary charWidths) |                                                       |
| ::public static int getDeviceCaps(Int64 hDC, int index)                                                                 |                                                       |
| ::public static int getFontData(Int64 hDC, int dwTable, int dwOffset, \[Binary pvBuffer\])                              |                                                       |
| ::public static int getFontUnicodeRanges(Int64 hDC, \[Binary lpgs\])                                                    |                                                       |
| ::public static int getGlyphIndices(Int64 hDC, str lpstr, Binary pgi, int fl)                                           |                                                       |
| ::public static Int64 getTextMetrics(Int64 hDC, Binary lpMetrics)                                                       |                                                       |
| ::public static int getUniscribeGlyphIndices(Int64 hDC, Int64 hGDIObject, str lpstr, Binary pgi)                        |                                                       |
| ::public static Int64 selectObject(Int64 hDC, Int64 hGDIObject)                                                         |                                                       |
| private void new()                                                                                                      | Initializes a new instance of the WinAPINative class. |

## Method createFontIndirect

```xpp
public static Int64 createFontIndirect(Binary logfont)
```

### Parameters - createFontIndirect

logfont  

### Return Value - createFontIndirect

## Method deleteObject

```xpp
public static boolean deleteObject(Int64 hGDIObject)
```

### Parameters - deleteObject

hGDIObject  

### Return Value - deleteObject

## Method getCharABCWidthsI

```xpp
public static boolean getCharABCWidthsI(Int64 hDC, Int64 firstGlyphIndex, Int64 glyphIndicesCount, Binary charWidths)
```

### Parameters - getCharABCWidthsI

hDC  

<!-- -->

firstGlyphIndex  

<!-- -->

glyphIndicesCount  

<!-- -->

charWidths  

### Return Value - getCharABCWidthsI

## Method getDeviceCaps

```xpp
public static int getDeviceCaps(Int64 hDC, int index)
```

### Parameters - getDeviceCaps

hDC  

<!-- -->

index  

### Return Value - getDeviceCaps

## Method getFontData

```xpp
public static int getFontData(Int64 hDC, int dwTable, int dwOffset, [Binary pvBuffer])
```

### Parameters - getFontData

hDC  

<!-- -->

dwTable  

<!-- -->

dwOffset  

<!-- -->

pvBuffer  

### Return Value - getFontData

## Method getFontUnicodeRanges

```xpp
public static int getFontUnicodeRanges(Int64 hDC, [Binary lpgs])
```

### Parameters - getFontUnicodeRanges

hDC  

<!-- -->

lpgs  

### Return Value - getFontUnicodeRanges

## Method getGlyphIndices

```xpp
public static int getGlyphIndices(Int64 hDC, str lpstr, Binary pgi, int fl)
```

### Parameters - getGlyphIndices

hDC  

<!-- -->

lpstr  

<!-- -->

pgi  

<!-- -->

fl  

### Return Value - getGlyphIndices

## Method getTextMetrics

```xpp
public static Int64 getTextMetrics(Int64 hDC, Binary lpMetrics)
```

### Parameters - getTextMetrics

hDC  

<!-- -->

lpMetrics  

### Return Value - getTextMetrics

## Method getUniscribeGlyphIndices

```xpp
public static int getUniscribeGlyphIndices(Int64 hDC, Int64 hGDIObject, str lpstr, Binary pgi)
```

### Parameters - getUniscribeGlyphIndices

hDC  

<!-- -->

hGDIObject  

<!-- -->

lpstr  

<!-- -->

pgi  

### Return Value - getUniscribeGlyphIndices

## Method selectObject

```xpp
public static Int64 selectObject(Int64 hDC, Int64 hGDIObject)
```

### Parameters - selectObject

hDC  

<!-- -->

hGDIObject  

### Return Value - selectObject

## Method new

Initializes a new instance of the WinAPINative class.

```xpp
private void new()
```


