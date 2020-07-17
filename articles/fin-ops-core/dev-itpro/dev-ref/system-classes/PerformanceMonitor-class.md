---
title: PerformanceMonitor class
description: This topic describes the PerformanceMonitor class.
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

# Class PerformanceMonitor

[!include [banner](../../includes/banner.md)]

```xpp
class PerformanceMonitor extends Object
```

The PerformanceMonitor class fetches data for processes that are running on the system.

## Remarks

You can take a snapshot of the system at any time and traverse the counters for any process that is running on the system.

## Examples

The following example prints the processId and workingset values for all the currently running processes.

```xpp
static void pvPerformanceMonitorTest(args a) 
{ 
    int i, j;  
    PerformanceMonitorInstance instance;  
    PerformanceMonitorCounter counter1, counter2;  
    PerformanceMonitor pm = new PerformanceMonitor();  
    // Take a current snapshot of the system. 
    pm.takeSnapshot ();  
    // Traverse all the running processes. 
    for (i= 1; i <= pm.instanceCount(); i++)  
    {  
        instance = pm.instance(i);  
        counter1 = instance.getCounter("ID Process");  
        counter2 = instance.getCounter("Working Set");  
        print instance.name(), " ",  
        counter1.intData(), " ",  
        counter2.intData();  
    } 
    pause;  
}
```

## Methods

| Method                                                     | Description                                                                                    |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------|
| public PerformanceMonitorInstance instance(int instanceNo) |                                                                                                |
| public int instanceCount()                                 | Returns the instance count, which is the number of processes in the current snapshot.          |
| public int processId()                                     | Returns the processId value of the process that is running this method.                        |
| public str systemName()                                    |                                                                                                |
| public boolean takeSnapshot(\[str processName\])           |                                                                                                |
| public str toString()                                      | Returns a string that contains the class handle and name, and possibly additional information. |
| public void new()                                          | Initializes a new instance of the PerformanceMonitor class.                                    |

## Method instance

```xpp
public PerformanceMonitorInstance instance(int instanceNo)
```

### Parameters - instance

instanceNo  

### Return Value - instance

## Method instanceCount

Returns the instance count, which is the number of processes in the current snapshot.

```xpp
public int instanceCount()
```

### Return Value - instanceCount

The number of processes in the current snapshot.

### Remarks - instanceCount

Use the takeSnapshot method to take a snapshot of the currently running processes.

### Examples - instanceCount

```xpp
static void pvPerformanceMonitorTest(args a) 
{ 
    int i, j; 
    PerformanceMonitorInstance instance; 
    PerformanceMonitorCounter counter1, counter2; 
    PerformanceMonitor pm = new PerformanceMonitor(); 
    // Take a current snapshot of the system. 
    pm.takeSnapshot (); 
    // Traverse all the running processes. 
    for (i= 1; i <= pm.instanceCount(); i++) 
    { 
        instance = pm.instance(i); 
        counter1 = instance.getCounter("ID Process"); 
        counter2 = instance.getCounter("Working Set"); 
        print instance.name(), " ",  
            counter1.intData(), " ",  
            counter2.intData(); 
    } 
    pause; 
}
```

## Method processId

Returns the processId value of the process that is running this method.

```xpp
public int processId()
```

### Return Value - processId

The processId value of the process that is running this method.

### Examples - processId

```xpp
static void processIdDemo(args a) 
{ 
    PerformanceMonitor pm = new PerformanceMonitor(); 
    print pm.processId(); 
    pause; 
}
```

## Method systemName

```xpp
public str systemName()
```

### Return Value - systemName

## Method takeSnapshot

```xpp
public boolean takeSnapshot([str processName])
```

### Parameters - takeSnapshot

processName  

### Return Value - takeSnapshot

## Method toString

Returns a string that contains the class handle and name, and possibly additional information.

```xpp
public str toString()
```

### Return Value - toString

A textual description of the class.

### Remarks - toString

By default, for most classes, the toString method returns a string that contains the class handle and name. However, in some classes, additional information is returned in the string.

## Method new

Initializes a new instance of the PerformanceMonitor class.

```xpp
public void new()
```

