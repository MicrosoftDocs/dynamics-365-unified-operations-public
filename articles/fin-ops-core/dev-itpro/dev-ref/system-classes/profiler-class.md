---
title: profiler class
description: This topic describes the profiler class.
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

# Class profiler

[!include [banner](../../includes/banner.md)]

```xpp
class profiler extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                                                                                                                                                                                                                                                                                                          | Description                                          |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| public int collected()                                                                                                                                                                                                                                                                                                                                                                                                                                          |                                                      |
| public int flushInterval(\[int interval\])                                                                                                                                                                                                                                                                                                                                                                                                                      |                                                      |
| public AnyType profileOff()                                                                                                                                                                                                                                                                                                                                                                                                                                     |                                                      |
| public AnyType profileOn(str runId, \[int traceDepth\])                                                                                                                                                                                                                                                                                                                                                                                                         |                                                      |
| public str tempPath()                                                                                                                                                                                                                                                                                                                                                                                                                                           |                                                      |
| public str toString()                                                                                                                                                                                                                                                                                                                                                                                                                                           | Returns a string that represents the current object. |
| ::public static AnyType profilerAlreadyOn()                                                                                                                                                                                                                                                                                                                                                                                                                     |                                                      |
| public void flush()                                                                                                                                                                                                                                                                                                                                                                                                                                             |                                                      |
| public void new()                                                                                                                                                                                                                                                                                                                                                                                                                                               | Initializes a new instance of the profiler class.    |
| public void flushData(int lineNumber, str path, int microSecs, int sequenceNumber, int parentSequenceNumber, int selectCalls, int selectBytes, int selectRows, int sqlWaitTime, int aosWaitTime, int sqlInserts, int sqlUpdates, int sqlDeletes, int aosInCalls, int aosOutCalls, int aosInBytes, int aosOutBytes, \[int sqlInsertBytes\], \[int sqlInsertRows\], \[int sqlUpdateBytes\], \[int sqlUpdateRows\], \[int sqlDeleteBytes\], \[int sqlDeleteRows\]) |                                                      |

## Method collected

```xpp
public int collected()
```

### Return Value - collected

## Method flushInterval

```xpp
public int flushInterval([int interval])
```

### Parameters - flushInterval

interval  

### Return Value - flushInterval

## Method profileOff

```xpp
public AnyType profileOff()
```

### Return Value - profileOff

## Method profileOn

```xpp
public AnyType profileOn(str runId, [int traceDepth])
```

### Parameters - profileOn

runId  

<!-- -->

traceDepth  

### Return Value - profileOn

## Method tempPath

```xpp
public str tempPath()
```

### Return Value - tempPath

## Method toString

Returns a string that represents the current object.

```xpp
public str toString()
```

### Return Value - toString

A string that represents the current object.

### Remarks - toString

The default implementation returns the class name of the object. The method can be overridden in a derived class to return values that are meaningful for that type. For example, an instance of the class returns the method name and type of the method, such as instance or static.

## Method profilerAlreadyOn

```xpp
public static AnyType profilerAlreadyOn()
```

### Return Value - profilerAlreadyOn

## Method flush

```xpp
public void flush()
```

## Method new

Initializes a new instance of the profiler class.

```xpp
public void new()
```

## Method flushData

```xpp
public void flushData(int lineNumber, str path, int microSecs, int sequenceNumber, int parentSequenceNumber, int selectCalls, int selectBytes, int selectRows, int sqlWaitTime, int aosWaitTime, int sqlInserts, int sqlUpdates, int sqlDeletes, int aosInCalls, int aosOutCalls, int aosInBytes, int aosOutBytes, [int sqlInsertBytes], [int sqlInsertRows], [int sqlUpdateBytes], [int sqlUpdateRows], [int sqlDeleteBytes], [int sqlDeleteRows])
```

### Parameters - flushData

lineNumber  

<!-- -->

path  

<!-- -->

microSecs  

<!-- -->

sequenceNumber  

<!-- -->

parentSequenceNumber  

<!-- -->

selectCalls  

<!-- -->

selectBytes  

<!-- -->

selectRows  

<!-- -->

sqlWaitTime  

<!-- -->

aosWaitTime  

<!-- -->

sqlInserts  

<!-- -->

sqlUpdates  

<!-- -->

sqlDeletes  

<!-- -->

aosInCalls  

<!-- -->

aosOutCalls  

<!-- -->

aosInBytes  

<!-- -->

aosOutBytes  

<!-- -->

sqlInsertBytes  

<!-- -->

sqlInsertRows  

<!-- -->

sqlUpdateBytes  

<!-- -->

sqlUpdateRows  

<!-- -->

sqlDeleteBytes  

<!-- -->

sqlDeleteRows  

