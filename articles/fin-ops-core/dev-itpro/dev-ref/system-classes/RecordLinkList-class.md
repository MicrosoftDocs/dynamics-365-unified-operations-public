---
title: RecordLinkList class
description: This topic describes the RecordLinkList class.
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

# Class RecordLinkList

[!include [banner](../../includes/banner.md)]

```xpp
class RecordLinkList extends Object
```

The RecordLinkList class dynamically creates a cache of record buffers that can hold records of different types, and that is not keyed or sorted.

## Remarks

A recordLinkList object is a double-linked list that can hold records of different types at the same time. It is not keyed or sorted. The recordLinkList object is especially useful for passing records from different tables as a parameter instead of retrieving the same records again. There is no limit to the size of a recordSortedList object. It is the responsibility of the programmer to control its size and therefore its memory consumption.

## Examples

## Methods

| Method                                           | Description                                                                                                                                |
|--------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| public int del()                                 | Deletes the record at the current position in the list.                                                                                    |
| public TableId fileId()                          | Retrieves the table ID of the record at the current position in the list.                                                                  |
| public boolean first(\[Common record\])          | Puts the pointer on the first record in the list and, if it is present, copies the record into the buffer that is provided.                |
| public boolean get(Common record, \[int index\]) | Copies the record at the current position or the specified position to the provided record buffer, without affecting the pointer position. |
| public int ins(Common record)                    | Inserts a record at the end of a list.                                                                                                     |
| public boolean last(\[Common record\])           | Puts the list at the last record and copies the record to the specified record buffer.                                                     |
| public int len()                                 | Returns the current number of records in the list.                                                                                         |
| public boolean next(\[Common record\])           | Puts the pointer on the next record and copies it to the provided buffer.                                                                  |
| public Common peek()                             | Retrieves the record at the current position in the list.                                                                                  |
| public boolean prev(\[Common record\])           | Puts the pointer on the previous record in the list and copies the record to the specified buffer.                                         |
| public void new()                                | Initializes a new instance of the RecordLinkList class.                                                                                    |

## Method del

Deletes the record at the current position in the list.

```xpp
public int del()
```

### Return Value - del

The number of records that remain in the list.

## Method fileId

Retrieves the table ID of the record at the current position in the list.

```xpp
public TableId fileId()
```

### Return Value - fileId

The table ID.

## Method first

Puts the pointer on the first record in the list and, if it is present, copies the record into the buffer that is provided.

```xpp
public boolean first([Common record])
```

### Parameters - first

record  
The record buffer that will contain the result; optional.

### Return Value - first

true if the method succeeds; false if no records exist.

## Method get

Copies the record at the current position or the specified position to the provided record buffer, without affecting the pointer position.

```xpp
public boolean get(Common record, [int index])
```

### Parameters - get

record  
The number of the record in the list to retrieve if the current record is not being retrieved; optional.

<!-- -->

index  
The number of the record in the list to retrieve if the current record is not being retrieved; optional.

### Return Value - get

true if a record could be retrieved; otherwise, false.

## Method ins

Inserts a record at the end of a list.

```xpp
public int ins(Common record)
```

### Parameters - ins

record  
The record buffer that is used to hold the record to insert.

### Return Value - ins

The number of elements in the list.

## Method last

Puts the list at the last record and copies the record to the specified record buffer.

```xpp
public boolean last([Common record])
```

### Parameters - last

record  
A record buffer that is used to hold the record that is retrieved; optional.

### Return Value - last

true if the method succeeds; false if there are no records in the list.

## Method len

Returns the current number of records in the list.

```xpp
public int len()
```

### Return Value - len

The number of records in the list.

## Method next

Puts the pointer on the next record and copies it to the provided buffer.

```xpp
public boolean next([Common record])
```

### Parameters - next

record  
The record buffer of same type as the record at the position; optional.

### Return Value - next

true if the method succeeds; false if there are no more records.

## Method peek

Retrieves the record at the current position in the list.

```xpp
public Common peek()
```

### Return Value - peek

A record buffer if the record is found.

## Method prev

Puts the pointer on the previous record in the list and copies the record to the specified buffer.

```xpp
public boolean prev([Common record])
```

### Parameters - prev

record  
The record buffer of the same type as the record to copy; optional.

### Return Value - prev

true if the pointer is not at the first record; otherwise, false.

## Method new

Initializes a new instance of the RecordLinkList class.

```xpp
public void new()
```

