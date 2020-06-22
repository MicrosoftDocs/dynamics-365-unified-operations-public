---
title: Editor class
description: This topic describes the Editor class.
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

# Class Editor

[!include [banner](../../includes/banner.md)]


```xpp
class Editor extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                          | Description                                     |
|---------------------------------------------------------------------------------|-------------------------------------------------|
| public int columnNo()                                                           |                                                 |
| public str currentLine()                                                        |                                                 |
| public int currentLineNo()                                                      |                                                 |
| public str getLine()                                                            |                                                 |
| public int gotoCol(int ColumnNo)                                                |                                                 |
| public int lineNo()                                                             |                                                 |
| public MarkMode markMode()                                                      |                                                 |
| public boolean matchCase(\[boolean UseMatchCase\])                              |                                                 |
| public boolean moreLines()                                                      |                                                 |
| public boolean moreSelectedLines()                                              |                                                 |
| public str path()                                                               |                                                 |
| public boolean regexp(\[boolean UseRegExp\])                                    |                                                 |
| public boolean replace(str SearchString, str ReplaceString, boolean ReplaceAll) |                                                 |
| public boolean search(str SearchString)                                         |                                                 |
| public str searchString()                                                       |                                                 |
| public int selectionEndCol()                                                    |                                                 |
| public int selectionEndLine()                                                   |                                                 |
| public int selectionStartCol()                                                  |                                                 |
| public int selectionStartLine()                                                 |                                                 |
| ::public static Editor open(str documentPath)                                   |                                                 |
| public void gotoLine(int LineNo)                                                |                                                 |
| public void closeApplicationObjectDialog()                                      |                                                 |
| public void mark(int line, int col)                                             |                                                 |
| public void executeScript(str scriptName)                                       |                                                 |
| public void nextLine()                                                          |                                                 |
| public void firstSelectedLine()                                                 |                                                 |
| private void new()                                                              | Initializes a new instance of the Editor class. |
| public void unmark()                                                            |                                                 |
| public void insertString(str InsString)                                         |                                                 |
| public void close()                                                             |                                                 |
| public void nextSelectedLine()                                                  |                                                 |
| public void closeSearchDialog()                                                 |                                                 |
| public void deleteLines(\[int noOfLines\])                                      |                                                 |
| public void insertLines(str InsString)                                          |                                                 |
| public void firstLine()                                                         |                                                 |
| public void deleteChars(\[int noOfChars\])                                      |                                                 |

## Method columnNo

```xpp
public int columnNo()
```

### Return Value - columnNo

## Method currentLine

```xpp
public str currentLine()
```

### Return Value - currentLine

## Method currentLineNo

```xpp
public int currentLineNo()
```

### Return Value - currentLineNo

## Method getLine

```xpp
public str getLine()
```

### Return Value - getLine

## Method gotoCol

```xpp
public int gotoCol(int ColumnNo)
```

### Parameters - gotoCol

ColumnNo  

### Return Value - gotoCol

## Method lineNo

```xpp
public int lineNo()
```

### Return Value - lineNo

## Method markMode

```xpp
public MarkMode markMode()
```

### Return Value - markMode

## Method matchCase

```xpp
public boolean matchCase([boolean UseMatchCase])
```

### Parameters - matchCase

UseMatchCase  

### Return Value - matchCase

## Method moreLines

```xpp
public boolean moreLines()
```

### Return Value - moreLines

## Method moreSelectedLines

```xpp
public boolean moreSelectedLines()
```

### Return Value - moreSelectedLines

## Method path

```xpp
public str path()
```

### Return Value - path

## Method regexp

```xpp
public boolean regexp([boolean UseRegExp])
```

### Parameters - regexp

UseRegExp  

### Return Value - regexp

## Method replace

```xpp
public boolean replace(str SearchString, str ReplaceString, boolean ReplaceAll)
```

### Parameters - replace

SearchString  

<!-- -->

ReplaceString  

<!-- -->

ReplaceAll  

### Return Value - replace

## Method search

```xpp
public boolean search(str SearchString)
```

### Parameters - search

SearchString  

### Return Value - search

## Method searchString

```xpp
public str searchString()
```

### Return Value - searchString

## Method selectionEndCol

```xpp
public int selectionEndCol()
```

### Return Value - selectionEndCol

## Method selectionEndLine

```xpp
public int selectionEndLine()
```

### Return Value - selectionEndLine

## Method selectionStartCol

```xpp
public int selectionStartCol()
```

### Return Value - selectionStartCol

## Method selectionStartLine

```xpp
public int selectionStartLine()
```

### Return Value - selectionStartLine

## Method open

```xpp
public static Editor open(str documentPath)
```

### Parameters - open

documentPath  

### Return Value - open

## Method gotoLine

```xpp
public void gotoLine(int LineNo)
```

### Parameters - gotoLine

LineNo  

## Method closeApplicationObjectDialog

```xpp
public void closeApplicationObjectDialog()
```

## Method mark

```xpp
public void mark(int line, int col)
```

### Parameters - mark

line  

<!-- -->

col  

## Method executeScript

```xpp
public void executeScript(str scriptName)
```

### Parameters - executeScript

scriptName  

## Method nextLine

```xpp
public void nextLine()
```

## Method firstSelectedLine

```xpp
public void firstSelectedLine()
```

## Method new

Initializes a new instance of the Editor class.

```xpp
private void new()
```

## Method unmark

```xpp
public void unmark()
```

## Method insertString

```xpp
public void insertString(str InsString)
```

### Parameters - insertString

InsString  

## Method close

```xpp
public void close()
```

## Method nextSelectedLine

```xpp
public void nextSelectedLine()
```

## Method closeSearchDialog

```xpp
public void closeSearchDialog()
```

## Method deleteLines

```xpp
public void deleteLines([int noOfLines])
```

### Parameters - deleteLines

noOfLines  

## Method insertLines

```xpp
public void insertLines(str InsString)
```

### Parameters - insertLines

InsString  

## Method firstLine

```xpp
public void firstLine()
```

## Method deleteChars

```xpp
public void deleteChars([int noOfChars])
```

### Parameters - deleteChars

noOfChars  

