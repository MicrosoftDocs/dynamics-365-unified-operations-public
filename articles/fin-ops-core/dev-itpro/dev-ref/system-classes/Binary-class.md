---
title: Binary class
description: This topic describes the Binary class.
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

# Class Binary

[!include [banner](../../includes/banner.md)]


```xpp
class Binary extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                   | Description                                     |
|--------------------------------------------------------------------------|-------------------------------------------------|
| public int byte(int offset, \[int value\])                               |                                                 |
| public Real double(int offset, \[Real value\])                           |                                                 |
| public int dWord(int offset, \[int value\])                              |                                                 |
| public container getContainer()                                          |                                                 |
| public CLRObject getMemoryStream()                                       |                                                 |
| public Int64 qWord(int offset, \[Int64 value\])                          |                                                 |
| public str string(int offset, \[str value\])                             |                                                 |
| public int strLenBytes(int offset)                                       |                                                 |
| public int word(int offset, \[int value\])                               |                                                 |
| public str wString(int offset, \[str value\])                            |                                                 |
| ::public static Binary constructFromContainer(container data)            |                                                 |
| ::public static Binary constructFromMemoryStream(CLRObject memoryStream) |                                                 |
| public void attach(Int64 bufPtr, int bufSize)                            |                                                 |
| public void finalize()                                                   |                                                 |
| public void appendSubString(\[str string\])                              |                                                 |
| public void setBinaryValue(int offset, Binary value)                     |                                                 |
| public void new(AnyType buffersizeOrString, \[boolean wideString\])      | Initializes a new instance of the Object class. |

## Method byte

```xpp
public int byte(int offset, [int value])
```

### Parameters - byte

offset  

<!-- -->

value  

### Return Value - byte

## Method double

```xpp
public Real double(int offset, [Real value])
```

### Parameters - double

offset  

<!-- -->

value  

### Return Value - double

## Method dWord

```xpp
public int dWord(int offset, [int value])
```

### Parameters - dWord

offset  

<!-- -->

value  

### Return Value - dWord

## Method getContainer

```xpp
public container getContainer()
```

### Return Value - getContainer

## Method getMemoryStream

```xpp
public CLRObject getMemoryStream()
```

### Return Value - getMemoryStream

## Method qWord

```xpp
public Int64 qWord(int offset, [Int64 value])
```

### Parameters - qWord

offset  

<!-- -->

value  

### Return Value - qWord

## Method string

```xpp
public str string(int offset, [str value])
```

### Parameters - string

offset  

<!-- -->

value  

### Return Value - string

## Method strLenBytes

```xpp
public int strLenBytes(int offset)
```

### Parameters - strLenBytes

offset  

### Return Value - strLenBytes

## Method word

```xpp
public int word(int offset, [int value])
```

### Parameters - word

offset  

<!-- -->

value  

### Return Value - word

## Method wString

```xpp
public str wString(int offset, [str value])
```

### Parameters - wString

offset  

<!-- -->

value  

### Return Value - wString

## Method constructFromContainer

```xpp
public static Binary constructFromContainer(container data)
```

### Parameters - constructFromContainer

data  

### Return Value - constructFromContainer

## Method constructFromMemoryStream

```xpp
public static Binary constructFromMemoryStream(CLRObject memoryStream)
```

### Parameters - constructFromMemoryStream

memoryStream  

### Return Value - constructFromMemoryStream

## Method attach

```xpp
public void attach(Int64 bufPtr, int bufSize)
```

### Parameters - attach

bufPtr  

<!-- -->

bufSize  

## Method finalize

```xpp
public void finalize()
```

## Method appendSubString

```xpp
public void appendSubString([str string])
```

### Parameters - appendSubString

string  

## Method setBinaryValue

```xpp
public void setBinaryValue(int offset, Binary value)
```

### Parameters - setBinaryValue

offset  

<!-- -->

value  

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(AnyType buffersizeOrString, [boolean wideString])
```

### Parameters - new

buffersizeOrString  

<!-- -->

wideString  

