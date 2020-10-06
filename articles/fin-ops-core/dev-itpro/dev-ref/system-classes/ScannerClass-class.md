---
title: ScannerClass class
description: This topic describes the ScannerClass class.
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

# Class ScannerClass

[!include [banner](../../includes/banner.md)]


```xpp
class ScannerClass extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                       | Description                                     |
|----------------------------------------------------------------------------------------------|-------------------------------------------------|
| public int col()                                                                             |                                                 |
| public Date dateValue()                                                                      |                                                 |
| public int firstSymbol()                                                                     |                                                 |
| public Int64 int64Value()                                                                    |                                                 |
| public int intValue()                                                                        |                                                 |
| public int line()                                                                            |                                                 |
| public int nextSymbol()                                                                      |                                                 |
| public Real realValue()                                                                      |                                                 |
| public int startColumn()                                                                     |                                                 |
| public str string()                                                                          |                                                 |
| public str strValue()                                                                        |                                                 |
| public void localMacroDefine(str text, int startLine, int startPos, int endLine, int endPos) |                                                 |
| public void lineComment(str text, int startLine, int startPos, int endLine, int endPos)      |                                                 |
| public void macroDefine(str text, int startLine, int startPos, int endLine, int endPos)      |                                                 |
| public void new(str source)                                                                  | Initializes a new instance of the Object class. |
| public void comment(str text, int startLine, int startPos, int endLine, int endPos)          |                                                 |

## Method col

```xpp
public int col()
```

### Return Value - col

## Method dateValue

```xpp
public Date dateValue()
```

### Return Value - dateValue

## Method firstSymbol

```xpp
public int firstSymbol()
```

### Return Value - firstSymbol

## Method int64Value

```xpp
public Int64 int64Value()
```

### Return Value - int64Value

## Method intValue

```xpp
public int intValue()
```

### Return Value - intValue

## Method line

```xpp
public int line()
```

### Return Value - line

## Method nextSymbol

```xpp
public int nextSymbol()
```

### Return Value - nextSymbol

## Method realValue

```xpp
public Real realValue()
```

### Return Value - realValue

## Method startColumn

```xpp
public int startColumn()
```

### Return Value - startColumn

## Method string

```xpp
public str string()
```

### Return Value - string

## Method strValue

```xpp
public str strValue()
```

### Return Value - strValue

## Method localMacroDefine

```xpp
public void localMacroDefine(str text, int startLine, int startPos, int endLine, int endPos)
```

### Parameters - localMacroDefine

text  

<!-- -->

startLine  

<!-- -->

startPos  

<!-- -->

endLine  

<!-- -->

endPos  

## Method lineComment

```xpp
public void lineComment(str text, int startLine, int startPos, int endLine, int endPos)
```

### Parameters - lineComment

text  

<!-- -->

startLine  

<!-- -->

startPos  

<!-- -->

endLine  

<!-- -->

endPos  

## Method macroDefine

```xpp
public void macroDefine(str text, int startLine, int startPos, int endLine, int endPos)
```

### Parameters - macroDefine

text  

<!-- -->

startLine  

<!-- -->

startPos  

<!-- -->

endLine  

<!-- -->

endPos  

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(str source)
```

### Parameters - new

source  

## Method comment

```xpp
public void comment(str text, int startLine, int startPos, int endLine, int endPos)
```

### Parameters - comment

text  

<!-- -->

startLine  

<!-- -->

startPos  

<!-- -->

endLine  

<!-- -->

endPos  

