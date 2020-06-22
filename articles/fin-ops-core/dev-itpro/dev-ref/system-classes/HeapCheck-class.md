---
title: HeapCheck class
description: This topic describes the HeapCheck class.
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

# Class HeapCheck

[!include [banner](../../includes/banner.md)]


```xpp
class HeapCheck extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                      | Description                                     |
|---------------------------------------------------------------------------------------------|-------------------------------------------------|
| public int accessCnt()                                                                      |                                                 |
| public int addRefCnt()                                                                      |                                                 |
| public Int64 blocksAllocated(\[int pool\])                                                  |                                                 |
| public int breakCount(\[int count\])                                                        |                                                 |
| public Int64 bytesAllocated(\[int pool\])                                                   |                                                 |
| public Int64 ceiling(int pool, \[int ceiling\])                                             |                                                 |
| public int context(\[int context\])                                                         |                                                 |
| public int count(\[int count\])                                                             |                                                 |
| public int countObjects(int classId)                                                        |                                                 |
| public container createAContainer()                                                         |                                                 |
| public int csCallCnt()                                                                      |                                                 |
| public int csSweepCnt()                                                                     |                                                 |
| public container dataByContext(\[int poolNo\], \[int context\])                             |                                                 |
| public int dumpCursors()                                                                    |                                                 |
| public int dumpObjects()                                                                    |                                                 |
| public int filename(\[str filename\])                                                       |                                                 |
| public int fixedBlockSize(int pool, \[int blockSize\])                                      |                                                 |
| public int floor(int pool, \[int floor\])                                                   |                                                 |
| public int freeRefCnt()                                                                     |                                                 |
| public int getRuntimeBugcheckFlags()                                                        |                                                 |
| public Common getUnfreedCursor()                                                            |                                                 |
| public Common getUnfreedObject()                                                            |                                                 |
| public boolean include(int objectNo, \[boolean include\])                                   |                                                 |
| public boolean moreUnfreedCursors()                                                         |                                                 |
| public boolean moreUnfreedObjects()                                                         |                                                 |
| public int objectContext(int objNo, \[int context\])                                        |                                                 |
| public int pageSize(int pool, \[int pageSize\])                                             |                                                 |
| public int poolCount()                                                                      |                                                 |
| public str poolName(int poolNo)                                                             |                                                 |
| public int smallBlockSize(int pool, \[int blockSize\])                                      |                                                 |
| public int sweepCnt()                                                                       |                                                 |
| public int testBlocks(\[int arg1\])                                                         |                                                 |
| public str unfreedObjectClass()                                                             |                                                 |
| public boolean unfreedObjectClient()                                                        |                                                 |
| public boolean unfreedObjectFinalized()                                                     |                                                 |
| public int unfreedObjectHandle()                                                            |                                                 |
| public int unfreedObjectIdent()                                                             |                                                 |
| public int unfreedObjectUseCount()                                                          |                                                 |
| public str version()                                                                        |                                                 |
| public void checkHeap(str Description, \[int context\], \[int pool\], \[boolean detailed\]) |                                                 |
| public void shrinkPool(\[int poolNo\])                                                      |                                                 |
| public void postCompactingMessage()                                                         |                                                 |
| public void checkHeapDif(str Description, \[int context\], \[int pool\])                    |                                                 |
| public void clearHeapContext()                                                              |                                                 |
| public void writeString(str text)                                                           |                                                 |
| public void firstUnfreedCursor()                                                            |                                                 |
| public void dumpDGMLGraph()                                                                 |                                                 |
| public void firstUnfreedObject()                                                            |                                                 |
| public void setHeapContext(str description)                                                 |                                                 |
| public void new(\[str Filename\])                                                           | Initializes a new instance of the Object class. |
| public void nextUnfreedObject()                                                             |                                                 |
| public void checkHeapStop()                                                                 |                                                 |
| public void nextUnfreedCursor()                                                             |                                                 |
| public void setRuntimeBugcheckFlags(int flags)                                              |                                                 |
| public void checkHeapStart()                                                                |                                                 |

## Method accessCnt

```xpp
public int accessCnt()
```

### Return Value - accessCnt

## Method addRefCnt

```xpp
public int addRefCnt()
```

### Return Value - addRefCnt

## Method blocksAllocated

```xpp
public Int64 blocksAllocated([int pool])
```

### Parameters - blocksAllocated

pool  

### Return Value - blocksAllocated

## Method breakCount

```xpp
public int breakCount([int count])
```

### Parameters - breakCount

count  

### Return Value - breakCount

## Method bytesAllocated

```xpp
public Int64 bytesAllocated([int pool])
```

### Parameters - bytesAllocated

pool  

### Return Value - bytesAllocated

## Method ceiling

```xpp
public Int64 ceiling(int pool, [int ceiling])
```

### Parameters - ceiling

pool  

<!-- -->

ceiling  

### Return Value - ceiling

## Method context

```xpp
public int context([int context])
```

### Parameters - context

context  

### Return Value - context

## Method count

```xpp
public int count([int count])
```

### Parameters - count

count  

### Return Value - count

## Method countObjects

```xpp
public int countObjects(int classId)
```

### Parameters - countObjects

classId  

### Return Value - countObjects

## Method createAContainer

```xpp
public container createAContainer()
```

### Return Value - createAContainer

## Method csCallCnt

```xpp
public int csCallCnt()
```

### Return Value - csCallCnt

## Method csSweepCnt

```xpp
public int csSweepCnt()
```

### Return Value - csSweepCnt

## Method dataByContext

```xpp
public container dataByContext([int poolNo], [int context])
```

### Parameters - dataByContext

poolNo  

<!-- -->

context  

### Return Value - dataByContext

## Method dumpCursors

```xpp
public int dumpCursors()
```

### Return Value - dumpCursors

## Method dumpObjects

```xpp
public int dumpObjects()
```

### Return Value - dumpObjects

## Method filename

```xpp
public int filename([str filename])
```

### Parameters - filename

filename  

### Return Value - filename

## Method fixedBlockSize

```xpp
public int fixedBlockSize(int pool, [int blockSize])
```

### Parameters - fixedBlockSize

pool  

<!-- -->

blockSize  

### Return Value - fixedBlockSize

## Method floor

```xpp
public int floor(int pool, [int floor])
```

### Parameters - floor

pool  

<!-- -->

floor  

### Return Value - floor

## Method freeRefCnt

```xpp
public int freeRefCnt()
```

### Return Value - freeRefCnt

## Method getRuntimeBugcheckFlags

```xpp
public int getRuntimeBugcheckFlags()
```

### Return Value - getRuntimeBugcheckFlags

## Method getUnfreedCursor

```xpp
public Common getUnfreedCursor()
```

### Return Value - getUnfreedCursor

## Method getUnfreedObject

```xpp
public Common getUnfreedObject()
```

### Return Value - getUnfreedObject

## Method include

```xpp
public boolean include(int objectNo, [boolean include])
```

### Parameters - include

objectNo  

<!-- -->

include  

### Return Value - include

## Method moreUnfreedCursors

```xpp
public boolean moreUnfreedCursors()
```

### Return Value - moreUnfreedCursors

## Method moreUnfreedObjects

```xpp
public boolean moreUnfreedObjects()
```

### Return Value - moreUnfreedObjects

## Method objectContext

```xpp
public int objectContext(int objNo, [int context])
```

### Parameters - objectContext

objNo  

<!-- -->

context  

### Return Value - objectContext

## Method pageSize

```xpp
public int pageSize(int pool, [int pageSize])
```

### Parameters - pageSize

pool  

<!-- -->

pageSize  

### Return Value - pageSize

## Method poolCount

```xpp
public int poolCount()
```

### Return Value - poolCount

## Method poolName

```xpp
public str poolName(int poolNo)
```

### Parameters - poolName

poolNo  

### Return Value - poolName

## Method smallBlockSize

```xpp
public int smallBlockSize(int pool, [int blockSize])
```

### Parameters - smallBlockSize

pool  

<!-- -->

blockSize  

### Return Value - smallBlockSize

## Method sweepCnt

```xpp
public int sweepCnt()
```

### Return Value - sweepCnt

## Method testBlocks

```xpp
public int testBlocks([int arg1])
```

### Parameters - testBlocks

arg1  

### Return Value - testBlocks

## Method unfreedObjectClass

```xpp
public str unfreedObjectClass()
```

### Return Value - unfreedObjectClass

## Method unfreedObjectClient

```xpp
public boolean unfreedObjectClient()
```

### Return Value - unfreedObjectClient

## Method unfreedObjectFinalized

```xpp
public boolean unfreedObjectFinalized()
```

### Return Value - unfreedObjectFinalized

## Method unfreedObjectHandle

```xpp
public int unfreedObjectHandle()
```

### Return Value - unfreedObjectHandle

## Method unfreedObjectIdent

```xpp
public int unfreedObjectIdent()
```

### Return Value - unfreedObjectIdent

## Method unfreedObjectUseCount

```xpp
public int unfreedObjectUseCount()
```

### Return Value - unfreedObjectUseCount

## Method version

```xpp
public str version()
```

### Return Value - version

## Method checkHeap

```xpp
public void checkHeap(str Description, [int context], [int pool], [boolean detailed])
```

### Parameters - checkHeap

Description  

<!-- -->

context  

<!-- -->

pool  

<!-- -->

detailed  

## Method shrinkPool

```xpp
public void shrinkPool([int poolNo])
```

### Parameters - shrinkPool

poolNo  

## Method postCompactingMessage

```xpp
public void postCompactingMessage()
```

## Method checkHeapDif

```xpp
public void checkHeapDif(str Description, [int context], [int pool])
```

### Parameters - checkHeapDif

Description  

<!-- -->

context  

<!-- -->

pool  

## Method clearHeapContext

```xpp
public void clearHeapContext()
```

## Method writeString

```xpp
public void writeString(str text)
```

### Parameters - writeString

text  

## Method firstUnfreedCursor

```xpp
public void firstUnfreedCursor()
```

## Method dumpDGMLGraph

```xpp
public void dumpDGMLGraph()
```

## Method firstUnfreedObject

```xpp
public void firstUnfreedObject()
```

## Method setHeapContext

```xpp
public void setHeapContext(str description)
```

### Parameters - setHeapContext

description  

## Method new

Initializes a new instance of the Object class.

```xpp
public void new([str Filename])
```

### Parameters - new

Filename  

## Method nextUnfreedObject

```xpp
public void nextUnfreedObject()
```

## Method checkHeapStop

```xpp
public void checkHeapStop()
```

## Method nextUnfreedCursor

```xpp
public void nextUnfreedCursor()
```

## Method setRuntimeBugcheckFlags

```xpp
public void setRuntimeBugcheckFlags(int flags)
```

### Parameters - setRuntimeBugcheckFlags

flags  

## Method checkHeapStart

```xpp
public void checkHeapStart()
```

