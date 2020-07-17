---
title: RecordInsertList class
description: This topic describes the RecordInsertList class.
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

# Class RecordInsertList

[!include [banner](../../includes/banner.md)]

```xpp
class RecordInsertList extends Object
```

The RecordInsertList class provides array insertion capabilities in the kernel.

## Remarks

This class lets you insert more than one record into the database at a time, which reduces communication between the application and the database. Records are inserted only when the kernel finds the time appropriate, but they are inserted no later than the call to the insertDatabase, add, and insertDatabase methods. The RecordInsertList.add and RecordInsertList.insertDatabase methods return the accumulated number of records that are currently inserted, so that you can keep track of when the records are actually inserted. The array insert operation automatically falls back to classic record-by-record inserts when non-SQL based tables are used (for example, temporary tables) or when the insert method on the table is overridden (unless it is explicitly discarded). The RecordInsertList class resembles the RecordSortedList class, but it has built-in client/server support (it automatically packs data from one tier to another when this is required) and lacks the sort order features that are available in the RecordSortedList class.

## Examples

The following example uses the RecordInsertList class to copy a bill of materials (BOM) from one BOM to another.

```xpp
void copyBOM(BOMId _FromBOM, BOMId _ToBOM) 
{ 
    RecordInsertList BOMList; 
    BOM BOM, newBOM; 
    BOMList = new RecordInsertList(tableNum(BOM)); 
    while select BOM 
    where BOM.BOMId == _FromBOM 
    { 
        newBOM.data(BOM); 
        newBOM.BOMId = _ToBOM; 
        BOMList.add(newBOM); 
    } 
    BOMList.insertDatabase(); 
}
```

## Methods

| Method                                                                                                                                                                                              | Description                                                                                       |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| public int add(Common record)                                                                                                                                                                       | Adds a record to a RecordInsertList object for subsequent insertion into the database.            |
| public int insertDatabase()                                                                                                                                                                         | Inserts all records that have not already been inserted into the current RecordInsertList object. |
| public void new(TableId tableId, \[boolean skipInsertMethod\], \[boolean skipDatabaseLog\], \[boolean skipEvents\], \[boolean skipAosValidation\], \[boolean skipRLSValidation\], \[Common table\]) | Creates a new object to hold records for insertion into the database.                             |

## Method add

Adds a record to a RecordInsertList object for subsequent insertion into the database.

```xpp
public int add(Common record)
```

### Parameters - add

record  
A database buffer of the same type that is used to instantiate the class.

### Return Value - add

An integer that indicates whether the record has been successfully added to the list.

### Remarks - add

The add method can flush records to the database whenever this will speed up performance. However, to guarantee that all records in the list are inserted, use the RecordInsertList.insertDatabase method.

### Examples - add

The following example uses the RecordInsertList class to copy a BOM from one BOM to another. The add method is used to add all the records in the BOM to the RecordInsertList object before a final call is made to the insertDatabase method to insert all remaining records.

```xpp
void copyBOM(BOMId _FromBOM, BOMId _ToBOM) 
{ 
    RecordInsertList BOMList; 
    BOM BOM, newBOM; 
    BOMList = new RecordInsertList(tableNum(BOM)); 
    while select BOM 
    where BOM.BOMId == _FromBOM 
    { 
        newBOM.data(BOM); 
        newBOM.BOMId = _ToBOM; 
        BOMList.add(newBOM); 
    } 
    BOMList.insertDatabase(); 
}
```

## Method insertDatabase

Inserts all records that have not already been inserted into the current RecordInsertList object.

```xpp
public int insertDatabase()
```

### Return Value - insertDatabase

An integer that represents the total number of records that were inserted.

### Remarks - insertDatabase

The RecordInsertList.add method flushes records to the database whenever this will speed up performance.

### Examples - insertDatabase

The following example uses the RecordInsertList class to copy a BOM from one BOM to another. The RecordInsertList.add method is used to add all the records in the BOM to the RecordInsertList class before a final call is made to the insertDatabase method to insert all remaining records.

```xpp
void copyBOM(BOMId _FromBOM, BOMId _ToBOM) 
{ 
    RecordInsertList BOMList; 
    BOM BOM, newBOM; 
    BOMList = new RecordInsertList(tableNum(BOM)); 
    while select BOM 
    where BOM.BOMId == _FromBOM 
    { 
        newBOM.data(BOM); 
        newBOM.BOMId = _ToBOM; 
        BOMList.add(newBOM); 
    } 
    BOMList.insertDatabase(); 
}
```

## Method new

Creates a new object to hold records for insertion into the database.

```xpp
public void new(TableId tableId, [boolean skipInsertMethod], [boolean skipDatabaseLog], [boolean skipEvents], [boolean skipAosValidation], [boolean skipRLSValidation], [Common table])
```

### Parameters - new

tableId  

<!-- -->

skipInsertMethod  

<!-- -->

skipDatabaseLog  

<!-- -->

skipEvents  

<!-- -->

skipAosValidation  

<!-- -->

skipRLSValidation  

<!-- -->

table  

### Examples - new

The following example creates a new RecordInsertList class for the EventRuleField table. The insert method for the table is run when these records are inserted, and the insertion is recorded in the database log. However, CUD events are not generated for the insertion.

```xpp
recordInsertList = new RecordInsertList( 
    tablenum(EventRuleField), 
    false, 
    false, 
    true);
```

