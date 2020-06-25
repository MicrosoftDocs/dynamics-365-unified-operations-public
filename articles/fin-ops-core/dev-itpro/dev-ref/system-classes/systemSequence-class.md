---
title: systemSequence class
description: This topic describes the systemSequence class.
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

# Class systemSequence

[!include [banner](../../includes/banner.md)]

```xpp
class systemSequence extends Object
```

The systemSequence class takes manual control of the system sequence generator and delivers unique RecIds for all SQL tables.

## Remarks

When records are inserted into SQL tables, a unique RecId is assigned to each record�regardless of the company each record is associated with. Use extreme caution when you use this class�data integrity could be destroyed. This class is typically used for data import or export routines, or for very large jobs. The record ID is an int64 data type value. The range in which record IDs are allocated is from 5637144576 to 2^63 (9223372036854775808). RecIds can be used up prematurely if large, unused ranges of RecIds are created. Reclaiming unused ranges of RecIds that lie between used ranges of RecIds is a very complicated process.

## Examples

The following example reserves the int64max value for the CustTable table.

```xpp
static public void Main(Args _args) 
{ 
    systemSequence seq; 
    seq = new SystemSequence(); 
    if (seq) 
    { 
        // Allocate 20 recordIds for CustTable table. 
        seq.reserveValues(20, tablenum(CustTable)); 
        // Suspend automatic recId allocation. 
        Seq.suspendRecIds(tablenum(CustTable)); 
        // Manually generate recIds in the range allocated. 
        // Remove the recId suspension. 
        Seq.removeRecIdSuspension(); 
      } 
}
```

## Methods

| Method                                                             | Description                                                                                                                     |
|--------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| public Int64 flushValues(TableId tableId)                          | Flushes the reserved recIds from the System Sequence cache for a given table                                                    |
| public Int64 reserveTransids(Int64 nReserved, \[TableId tableId\]) |                                                                                                                                 |
| public Int64 reserveValues(Int64 nReserved, TableId tableId)       | Preallocates a range of recIds that can be allocated to new records when the automatic assignment of recIds has been suspended. |
| public void suspendTransIds(TableId tableId)                       |                                                                                                                                 |
| public void suspendRecIds(TableId tableId)                         |                                                                                                                                 |
| public void removeRecIdSuspension(\[TableId tableId\])             |                                                                                                                                 |
| public void new()                                                  | Initializes a new instance of the systemSequence class.                                                                         |
| public void removeTransIdSuspension(\[TableId tableId\])           |                                                                                                                                 |

## Method flushValues

Flushes the reserved recIds from the System Sequence cache for a given table

```xpp
public Int64 flushValues(TableId tableId)
```

### Parameters - flushValues

tableId  

### Return Value - flushValues

The number of recIds flushed from the cache.

### Remarks - flushValues

Subsequent inserts on the table reserve the recIds for the table and System Sequence cache is populated with the reserved range of recIds for the table.

## Method reserveTransids

```xpp
public Int64 reserveTransids(Int64 nReserved, [TableId tableId])
```

### Parameters - reserveTransids

nReserved  

<!-- -->

tableId  

### Return Value - reserveTransids

## Method reserveValues

Preallocates a range of recIds that can be allocated to new records when the automatic assignment of recIds has been suspended.

```xpp
public Int64 reserveValues(Int64 nReserved, TableId tableId)
```

### Parameters - reserveValues

nReserved  

<!-- -->

tableId  

### Return Value - reserveValues

The first usable reserved recId.

### Remarks - reserveValues

The range of recIds that you reserved are reserved immediately.

## Method suspendTransIds

```xpp
public void suspendTransIds(TableId tableId)
```

### Parameters - suspendTransIds

tableId  

## Method suspendRecIds

```xpp
public void suspendRecIds(TableId tableId)
```

### Parameters - suspendRecIds

tableId  

## Method removeRecIdSuspension

```xpp
public void removeRecIdSuspension([TableId tableId])
```

### Parameters - removeRecIdSuspension

tableId  

## Method new

Initializes a new instance of the systemSequence class.

```xpp
public void new()
```

## Method removeTransIdSuspension

```xpp
public void removeTransIdSuspension([TableId tableId])
```

### Parameters - removeTransIdSuspension

tableId  



