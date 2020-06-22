---
title: xClassTrace class
description: This topic describes the xClassTrace class.
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

# Class xClassTrace

[!include [banner](../../includes/banner.md)]

```xpp
class xClassTrace extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                                                                             | Description                                          |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|
| ::public static boolean isTracingEnabled(\[Int64 keyword\], \[int level\])                                                                                                         |                                                      |
| ::public static boolean isTracingStarted()                                                                                                                                         |                                                      |
| ::public static str kernelCustomerId()                                                                                                                                             |                                                      |
| ::public static Guid kernelRequestId()                                                                                                                                             |                                                      |
| ::public static str kernelSessionId()                                                                                                                                              |                                                      |
| ::public static str kernelUserId()                                                                                                                                                 |                                                      |
| ::public static int start(str logFileName, \[int logBufferSize\], \[int minBuffers\], \[int maxBuffers\], \[Int64 keywords\], \[int maxFileSize\], \[boolean useCircularLogging\]) |                                                      |
| ::public static int stop()                                                                                                                                                         |                                                      |
| ::public static void logMessage(str message)                                                                                                                                       |                                                      |
| public void endMarker(str transactionName)                                                                                                                                         |                                                      |
| public void beginMarker(str transactionName)                                                                                                                                       |                                                      |
| ::public static void logComponentMessage(str component, str message)                                                                                                               |                                                      |
| public void finalize()                                                                                                                                                             |                                                      |
| public void new()                                                                                                                                                                  | Initializes a new instance of the xClassTrace class. |

## Method isTracingEnabled

```xpp
public static boolean isTracingEnabled([Int64 keyword], [int level])
```

### Parameters - isTracingEnabled

keyword  

<!-- -->

level  

### Return Value - isTracingEnabled

## Method isTracingStarted

```xpp
public static boolean isTracingStarted()
```

### Return Value - isTracingStarted

## Method kernelCustomerId

```xpp
public static str kernelCustomerId()
```

### Return Value - kernelCustomerId

## Method kernelRequestId

```xpp
public static Guid kernelRequestId()
```

### Return Value - kernelRequestId

## Method kernelSessionId

```xpp
public static str kernelSessionId()
```

### Return Value - kernelSessionId

## Method kernelUserId

```xpp
public static str kernelUserId()
```

### Return Value - kernelUserId

## Method start

```xpp
public static int start(str logFileName, [int logBufferSize], [int minBuffers], [int maxBuffers], [Int64 keywords], [int maxFileSize], [boolean useCircularLogging])
```

### Parameters - start

logFileName  

<!-- -->

logBufferSize  

<!-- -->

minBuffers  

<!-- -->

maxBuffers  

<!-- -->

keywords  

<!-- -->

maxFileSize  

<!-- -->

useCircularLogging  

### Return Value - start

## Method stop

```xpp
public static int stop()
```

### Return Value - stop

## Method logMessage

```xpp
public static void logMessage(str message)
```

### Parameters - logMessage

message  

## Method endMarker

```xpp
public void endMarker(str transactionName)
```

### Parameters - endMarker

transactionName  

## Method beginMarker

```xpp
public void beginMarker(str transactionName)
```

### Parameters - beginMarker

transactionName  

## Method logComponentMessage

```xpp
public static void logComponentMessage(str component, str message)
```

### Parameters - logComponentMessage

component  

<!-- -->

message  

## Method finalize

```xpp
public void finalize()
```

## Method new

Initializes a new instance of the xClassTrace class.

```xpp
public void new()
```

