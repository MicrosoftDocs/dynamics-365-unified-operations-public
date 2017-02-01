---
# required metadata

title: N Classes | Microsoft Docs
description: System API classes that start with the letter N.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-24 14:27:25
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 52351
ms.assetid: c8e997a4-9516-4aa1-84b1-8c892bfb0125
ms.region: Global
# ms.industry: 
ms.author: robinr

---

# N Classes

System API classes that start with the letter N.

Class NumberSequence
--------------------

    class NumberSequence extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                | Description                                             |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| ::public static int getNextNumber(Connection connection, Int64 numbersequencerecordid, Int64 globaltransid, str userid, int sessionid, DateTime sessionLoginDateTime) |                                                         |
| public void new()                                                                                                                                                     | Initializes a new instance of the NumberSequence class. |

### Method getNextNumber

    public static int getNextNumber(Connection connection, Int64 numbersequencerecordid, Int64 globaltransid, str userid, int sessionid, DateTime sessionLoginDateTime)

#### Parameters

connection  

<!-- -->

numbersequencerecordid  

<!-- -->

globaltransid  

<!-- -->

userid  

<!-- -->

sessionid  

<!-- -->

sessionLoginDateTime  

#### Return Value

### Method new

Initializes a new instance of the NumberSequence class.

    public void new()

## Class NumberSequenceSessionLessCache
    class NumberSequenceSessionLessCache extends Object

### Remarks

### Examples

### Methods

| Method                                                                         | Description                                                             |
|--------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| public int getNumFromCache(Common numbersequencetable)                         |                                                                         |
| public int valueLastNumFromCache(Int64 numbersequecerecordid)                  |                                                                         |
| public int valueNextNumFromCache(Int64 numbersequecerecordid)                  |                                                                         |
| public void flushCache(Int64 numbersequecerecordid)                            |                                                                         |
| public void fillCache(Int64 numbersequecerecordid, int nextRec, int blockSize) |                                                                         |
| public void new()                                                              | Initializes a new instance of the NumberSequenceSessionLessCache class. |

### Method getNumFromCache

    public int getNumFromCache(Common numbersequencetable)

#### Parameters

numbersequencetable  

#### Return Value

### Method valueLastNumFromCache

    public int valueLastNumFromCache(Int64 numbersequecerecordid)

#### Parameters

numbersequecerecordid  

#### Return Value

### Method valueNextNumFromCache

    public int valueNextNumFromCache(Int64 numbersequecerecordid)

#### Parameters

numbersequecerecordid  

#### Return Value

### Method flushCache

    public void flushCache(Int64 numbersequecerecordid)

#### Parameters

numbersequecerecordid  

### Method fillCache

    public void fillCache(Int64 numbersequecerecordid, int nextRec, int blockSize)

#### Parameters

numbersequecerecordid  

<!-- -->

nextRec  

<!-- -->

blockSize  

### Method new

Initializes a new instance of the NumberSequenceSessionLessCache class.

    public void new()

