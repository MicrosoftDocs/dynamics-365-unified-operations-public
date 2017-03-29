---
# required metadata

title: N Classes
description: System API classes that start with the letter N.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-24 14 - 27 - 25
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 52351
ms.assetid: 4816db3a-defc-4057-ba08-50d85f597eeb
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

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

