---
title: ReportControl class
description: This topic describes the ReportControl class.
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

# Class ReportControl

[!include [banner](../../includes/banner.md)]

```xpp
class ReportControl extends TreeNode
```

The ReportControl class lets you create, read, update, and delete X++ code and metadata.

## Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

## Examples

## Methods

| Method                                                     | Description |
|------------------------------------------------------------|-------------|
| public int bottomMarginAndFrame()                          |             |
| public ReportFieldType controlType()                       |             |
| public int delete()                                        |             |
| public str effectiveFont()                                 |             |
| public str fontInfoPrinter()                               |             |
| public int fontInfoPrinterAscent()                         |             |
| public int fontInfoPrinterDescent()                        |             |
| public int fontInfoPrinterExtLead()                        |             |
| public int fontInfoPrinterHeight()                         |             |
| public int fontInfoPrinterIntLead()                        |             |
| public str fontInfoScreen()                                |             |
| public int fontInfoScreenAscent()                          |             |
| public int fontInfoScreenDescent()                         |             |
| public int fontInfoScreenExtLead()                         |             |
| public int fontInfoScreenHeight()                          |             |
| public int fontInfoScreenIntLead()                         |             |
| public int height100mm(\[int heightExclBorder\])           |             |
| public int height100mmInclBorder(\[int heightInclBorder\]) |             |
| public int heightOfWordWrappedString100mm(str string)      |             |
| public int left100mm(\[int leftExclBorder\])               |             |
| public int left100mmInclBorder(\[int leftInclBorder\])     |             |
| public int leftMarginAnFrame()                             |             |
| public int numberOfLines(int height100mm)                  |             |
| public int position(\[int value\])                         |             |
| public str previewInfo(str string)                         |             |
| public int previewXCompensation100mm(str string)           |             |
| public int right100mm()                                    |             |
| public int right100mmInclBorder()                          |             |
| public int rightMarginAndFrame()                           |             |
| public str setHeightGetText(int lines, str string)         |             |
| public int top100mm(\[int topExclBorder\])                 |             |
| public int top100mmInclBorder(\[int topInclBorder\])       |             |
| public int topMarginAndFrame()                             |             |
| public int width100mm(\[int widthExclBorder\])             |             |
| public int width100mmInclBorder(\[int widthInclBorder\])   |             |
| public int widthOfString100mm(str string)                  |             |
| public void show()                                         |             |
| public void hide()                                         |             |

## Method bottomMarginAndFrame

```xpp
public int bottomMarginAndFrame()
```

### Return Value - bottomMarginAndFrame

## Method controlType

```xpp
public ReportFieldType controlType()
```

### Return Value - controlType

## Method delete

```xpp
public int delete()
```

### Return Value - delete

## Method effectiveFont

```xpp
public str effectiveFont()
```

### Return Value - effectiveFont

## Method fontInfoPrinter

```xpp
public str fontInfoPrinter()
```

### Return Value - fontInfoPrinter

## Method fontInfoPrinterAscent

```xpp
public int fontInfoPrinterAscent()
```

### Return Value - fontInfoPrinterAscent

## Method fontInfoPrinterDescent

```xpp
public int fontInfoPrinterDescent()
```

### Return Value - fontInfoPrinterDescent

## Method fontInfoPrinterExtLead

```xpp
public int fontInfoPrinterExtLead()
```

### Return Value - fontInfoPrinterExtLead

## Method fontInfoPrinterHeight

```xpp
public int fontInfoPrinterHeight()
```

### Return Value - fontInfoPrinterHeight

## Method fontInfoPrinterIntLead

```xpp
public int fontInfoPrinterIntLead()
```

### Return Value - fontInfoPrinterIntLead

## Method fontInfoScreen

```xpp
public str fontInfoScreen()
```

### Return Value - fontInfoScreen

## Method fontInfoScreenAscent

```xpp
public int fontInfoScreenAscent()
```

### Return Value - fontInfoScreenAscent

## Method fontInfoScreenDescent

```xpp
public int fontInfoScreenDescent()
```

### Return Value - fontInfoScreenDescent

## Method fontInfoScreenExtLead

```xpp
public int fontInfoScreenExtLead()
```

### Return Value - fontInfoScreenExtLead

## Method fontInfoScreenHeight

```xpp
public int fontInfoScreenHeight()
```

### Return Value - fontInfoScreenHeight

## Method fontInfoScreenIntLead

```xpp
public int fontInfoScreenIntLead()
```

### Return Value - fontInfoScreenIntLead

## Method height100mm

```xpp
public int height100mm([int heightExclBorder])
```

### Parameters - height100mm

heightExclBorder  

### Return Value - height100mm

## Method height100mmInclBorder

```xpp
public int height100mmInclBorder([int heightInclBorder])
```

### Parameters - height100mmInclBorder

heightInclBorder  

### Return Value - height100mmInclBorder

## Method heightOfWordWrappedString100mm

```xpp
public int heightOfWordWrappedString100mm(str string)
```

### Parameters - heightOfWordWrappedString100mm

string  

### Return Value - heightOfWordWrappedString100mm

## Method left100mm

```xpp
public int left100mm([int leftExclBorder])
```

### Parameters - left100mm

leftExclBorder  

### Return Value - left100mm

## Method left100mmInclBorder

```xpp
public int left100mmInclBorder([int leftInclBorder])
```

### Parameters - left100mmInclBorder

leftInclBorder  

### Return Value - left100mmInclBorder

## Method leftMarginAnFrame

```xpp
public int leftMarginAnFrame()
```

### Return Value - leftMarginAnFrame

## Method numberOfLines

```xpp
public int numberOfLines(int height100mm)
```

### Parameters - numberOfLines

height100mm  

### Return Value - numberOfLines

## Method position

```xpp
public int position([int value])
```

### Parameters - position

value  

### Return Value - position

## Method previewInfo

```xpp
public str previewInfo(str string)
```

### Parameters - previewInfo

string  

### Return Value - previewInfo

## Method previewXCompensation100mm

```xpp
public int previewXCompensation100mm(str string)
```

### Parameters - previewXCompensation100mm

string  

### Return Value - previewXCompensation100mm

## Method right100mm

```xpp
public int right100mm()
```

### Return Value - right100mm

## Method right100mmInclBorder

```xpp
public int right100mmInclBorder()
```

### Return Value - right100mmInclBorder

## Method rightMarginAndFrame

```xpp
public int rightMarginAndFrame()
```

### Return Value - rightMarginAndFrame

## Method setHeightGetText

```xpp
public str setHeightGetText(int lines, str string)
```

### Parameters - setHeightGetText

lines  

<!-- -->

string  

### Return Value - setHeightGetText

## Method top100mm

```xpp
public int top100mm([int topExclBorder])
```

### Parameters - top100mm

topExclBorder  

### Return Value - top100mm

## Method top100mmInclBorder

```xpp
public int top100mmInclBorder([int topInclBorder])
```

### Parameters - top100mmInclBorder

topInclBorder  

### Return Value - top100mmInclBorder

## Method topMarginAndFrame

```xpp
public int topMarginAndFrame()
```

### Return Value - topMarginAndFrame

## Method width100mm

```xpp
public int width100mm([int widthExclBorder])
```

### Parameters - width100mm

widthExclBorder  

### Return Value - width100mm

## Method width100mmInclBorder

```xpp
public int width100mmInclBorder([int widthInclBorder])
```

### Parameters - width100mmInclBorder

widthInclBorder  

### Return Value - width100mmInclBorder

## Method widthOfString100mm

```xpp
public int widthOfString100mm(str string)
```

### Parameters - widthOfString100mm

string  

### Return Value - widthOfString100mm

## Method show

```xpp
public void show()
```

## Method hide

```xpp
public void hide()
```

