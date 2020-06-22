---
title: SystemMonitor class
description: This topic describes the SystemMonitor class.
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

# Class SystemMonitor

[!include [banner](../../includes/banner.md)]

```xpp
class SystemMonitor extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                | Description                                            |
|-----------------------------------------------------------------------|--------------------------------------------------------|
| ::public static container allClientCounters()                         |                                                        |
| ::public static container allServerCounters()                         |                                                        |
| ::public static int getClientCounter(SystemMonitorCounter counter)    |                                                        |
| ::public static container getClientInternals()                        |                                                        |
| ::public static int getCounter(SystemMonitorCounter counter)          |                                                        |
| ::public static int getServerCounter(SystemMonitorCounter counter)    |                                                        |
| ::public static container getServerInternals()                        |                                                        |
| ::public static boolean isRunning()                                   |                                                        |
| ::public static boolean isServerCounter(SystemMonitorCounter counter) |                                                        |
| ::public static container sqlDump()                                   |                                                        |
| ::public static void systemDump(boolean includeSQL)                   |                                                        |
| ::public static void start()                                          |                                                        |
| ::public static void resetServer()                                    |                                                        |
| ::public static void stop()                                           |                                                        |
| public void new()                                                     | Initializes a new instance of the SystemMonitor class. |
| public void finalize()                                                |                                                        |
| ::public static void reset()                                          |                                                        |
| ::public static void resetClient()                                    |                                                        |

## Method allClientCounters

```xpp
public static container allClientCounters()
```

### Return Value - allClientCounters

## Method allServerCounters

```xpp
public static container allServerCounters()
```

### Return Value - allServerCounters

## Method getClientCounter

```xpp
public static int getClientCounter(SystemMonitorCounter counter)
```

### Parameters - getClientCounter

counter  

### Return Value - getClientCounter

## Method getClientInternals

```xpp
public static container getClientInternals()
```

### Return Value - getClientInternals

## Method getCounter

```xpp
public static int getCounter(SystemMonitorCounter counter)
```

### Parameters - getCounter

counter  

### Return Value - getCounter

## Method getServerCounter

```xpp
public static int getServerCounter(SystemMonitorCounter counter)
```

### Parameters - getServerCounter

counter  

### Return Value - getServerCounter

## Method getServerInternals

```xpp
public static container getServerInternals()
```

### Return Value - getServerInternals

## Method isRunning

```xpp
public static boolean isRunning()
```

### Return Value - isRunning

## Method isServerCounter

```xpp
public static boolean isServerCounter(SystemMonitorCounter counter)
```

### Parameters - isServerCounter

counter  

### Return Value - isServerCounter

## Method sqlDump

```xpp
public static container sqlDump()
```

### Return Value - sqlDump

## Method systemDump

```xpp
public static void systemDump(boolean includeSQL)
```

### Parameters - systemDump

includeSQL  

## Method start

```xpp
public static void start()
```

## Method resetServer

```xpp
public static void resetServer()
```

## Method stop

```xpp
public static void stop()
```

## Method new

Initializes a new instance of the SystemMonitor class.

```xpp
public void new()
```

## Method finalize

```xpp
public void finalize()
```

## Method reset

```xpp
public static void reset()
```

## Method resetClient

```xpp
public static void resetClient()
```

