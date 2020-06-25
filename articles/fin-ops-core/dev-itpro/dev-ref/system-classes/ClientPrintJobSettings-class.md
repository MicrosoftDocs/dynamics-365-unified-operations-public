---
title: ClientPrintJobSettings class
description: This topic describes the ClientPrintJobSettings class.
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

# Class ClientPrintJobSettings

[!include [banner](../../includes/banner.md)]

```xpp
class ClientPrintJobSettings extends PrintJobSettings
```

## Remarks

## Examples

## Methods

| Method                                                                                                                  | Description                                     |
|-------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| public container getFontDimension(container container)                                                                  |                                                 |
| public container getInfoStrings()                                                                                       |                                                 |
| public int getNextLineOffset(container container)                                                                       |                                                 |
| public container getPageInfo()                                                                                          |                                                 |
| public container getPrinterNames()                                                                                      |                                                 |
| public int getTextWidth(str text, str fontName, int charSet, int fontHeight, int style, int weight)                     |                                                 |
| public container getTextWidthExt(container container)                                                                   |                                                 |
| public container getWordWrapInfo(str text, int width, str fontName, int charSet, int fontHeight, int style, int weight) |                                                 |
| public container getWordWrapInfoExt(container container)                                                                |                                                 |
| public container printerSettingsExt(str formName, \[xArgs args\], \[ReportRun reportRun\], \[int showWhat\])            |                                                 |
| public container setOrientationGetPageInfo(PrinterOrientation orientation)                                              |                                                 |
| public void new(\[container Settings\], \[boolean infoOnly\])                                                           | Initializes a new instance of the Object class. |

## Method getFontDimension

```xpp
public container getFontDimension(container container)
```

### Parameters - getFontDimension

container  

### Return Value - getFontDimension

## Method getInfoStrings

```xpp
public container getInfoStrings()
```

### Return Value - getInfoStrings

## Method getNextLineOffset

```xpp
public int getNextLineOffset(container container)
```

### Parameters - getNextLineOffset

container  

### Return Value - getNextLineOffset

## Method getPageInfo

```xpp
public container getPageInfo()
```

### Return Value - getPageInfo

## Method getPrinterNames

```xpp
public container getPrinterNames()
```

### Return Value - getPrinterNames

## Method getTextWidth

```xpp
public int getTextWidth(str text, str fontName, int charSet, int fontHeight, int style, int weight)
```

### Parameters - getTextWidth

text  

<!-- -->

fontName  

<!-- -->

charSet  

<!-- -->

fontHeight  

<!-- -->

style  

<!-- -->

weight  

### Return Value - getTextWidth

## Method getTextWidthExt

```xpp
public container getTextWidthExt(container container)
```

### Parameters - getTextWidthExt

container  

### Return Value - getTextWidthExt

## Method getWordWrapInfo

```xpp
public container getWordWrapInfo(str text, int width, str fontName, int charSet, int fontHeight, int style, int weight)
```

### Parameters - getWordWrapInfo

text  

<!-- -->

width  

<!-- -->

fontName  

<!-- -->

charSet  

<!-- -->

fontHeight  

<!-- -->

style  

<!-- -->

weight  

### Return Value - getWordWrapInfo

## Method getWordWrapInfoExt

```xpp
public container getWordWrapInfoExt(container container)
```

### Parameters - getWordWrapInfoExt

container  

### Return Value - getWordWrapInfoExt

## Method printerSettingsExt

```xpp
public container printerSettingsExt(str formName, [xArgs args], [ReportRun reportRun], [int showWhat])
```

### Parameters - printerSettingsExt

formName  

<!-- -->

args  

<!-- -->

reportRun  

<!-- -->

showWhat  

### Return Value - printerSettingsExt

## Method setOrientationGetPageInfo

```xpp
public container setOrientationGetPageInfo(PrinterOrientation orientation)
```

### Parameters - setOrientationGetPageInfo

orientation  

### Return Value - setOrientationGetPageInfo

## Method new

Initializes a new instance of the Object class.

```xpp
public void new([container Settings], [boolean infoOnly])
```

### Parameters - new

Settings  

<!-- -->

infoOnly  

