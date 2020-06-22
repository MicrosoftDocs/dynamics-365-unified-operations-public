---
title: RecordSortedList class
description: This topic describes the RecordSortedList class.
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

# Class RecordSortedList

[!include [banner](../../includes/banner.md)]

```xpp
class RecordSortedList extends Object
```

The RecordSortedList class inserts multiple records in a single database trip.

## Remarks

Use RecordSortedList when you want a subset of data from a particular table, and you want it sorted in an order that does not currently exist as an index. A RecordSortedList object holds records from a single table. The list has a unique key that is defined by the fields listed by using the sortOrder method. Records are automatically sorted as they are inserted, they do not have to be inserted in sort sequence. RecordSortedList objects are particularly useful for passing a result-set as a parameter There is no limit to the size of a RecordSortedList object, but they are completely memory-based, so there are potential memory consumption problems. RecordSortedList objects must be server-located before the insertDatabase method can be called. Otherwise, an exception is thrown. Record level security (RLS) cannot be applied by the RecordSortedList class. RLS is applied by the RecordInsertList class). Use a RecordSortedList in preference to a temporary table in the following situations:

-   Only one sort order is needed.
-   The number of records is not too high (to avoid memory problems).

Compared to temporary tables, RecordSortedList objects:

-   Are faster.
-   Are not disk-based.
-   Only have one index.
-   Cannot be used in forms.
-   Require a call between the client and server per (grouped) read.

## Examples

## Methods

| Method                                                        | Description                                                                                                                                                          |
|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean del(Common record)                             | Removes a record that has a key that matches the key fields in the recordBuffer from the recordSortedList.                                                           |
| public boolean find(Common record)                            | Sets the record buffer to the contents of the record that has a key that matches the key fields in the record buffer, and positions the list to the record returned. |
| public boolean first(Common record)                           | Positions the list to the first record in the list, and copies its contents to the record buffer.                                                                    |
| public boolean ins(Common record, \[boolean updateIfExists\]) | Inserts a new record in a RecordSortedList, unless it is a duplicate.                                                                                                |
| public int len()                                              | Returns the current number of records in a RecordSortedList object.                                                                                                  |
| public boolean next(Common record)                            | Sets the record buffer to the contents of the next record in the recordSortedList and positions the list to the record returned.                                     |
| public void new(TableId tableId, \[Common table\])            | Initializes a new instance of the Object class.                                                                                                                      |
| public void sortOrder(FieldId fieldId, VarArg )               | Defines the fields on which the records are sorted.                                                                                                                  |
| public void sortOrderFromContainer(container container)       | Defines the fields on which the records are sorted.                                                                                                                  |
| public void insertDatabase(\[Connection connection\])         | Inserts multiple records on a single trip to the database.                                                                                                           |

## Method del

Removes a record that has a key that matches the key fields in the recordBuffer from the recordSortedList.

```xpp
public boolean del(Common record)
```

### Parameters - del

record  
A record buffer that contains the key values of the record to be deleted.

### Return Value - del

true if a record was removed; otherwise false.

## Method find

Sets the record buffer to the contents of the record that has a key that matches the key fields in the record buffer, and positions the list to the record returned.

```xpp
public boolean find(Common record)
```

### Parameters - find

record  
A record buffer that contains the key values to be searched for. The record found will replace the contents of the record buffer.

### Return Value - find

true if a record is found; otherwise false.

## Method first

Positions the list to the first record in the list, and copies its contents to the record buffer.

```xpp
public boolean first(Common record)
```

### Parameters - first

record  
A record buffer to contain first record in list.

### Return Value - first

true if the method is successful; otherwise false.

## Method ins

Inserts a new record in a RecordSortedList, unless it is a duplicate.

```xpp
public boolean ins(Common record, [boolean updateIfExists])
```

### Parameters - ins

record  
Whether to discard or replace duplicate records; optional. If false, the new record will be discarded if it is a duplicate. If true, the new record will replace an existing record if it is a duplicate.

<!-- -->

updateIfExists  
Whether to discard or replace duplicate records; optional. If false, the new record will be discarded if it is a duplicate. If true, the new record will replace an existing record if it is a duplicate.

### Return Value - ins

true if the record was added or replaced; otherwise false.

## Method len

Returns the current number of records in a RecordSortedList object.

```xpp
public int len()
```

### Return Value - len

The current number of records in the list.

## Method next

Sets the record buffer to the contents of the next record in the recordSortedList and positions the list to the record returned.

```xpp
public boolean next(Common record)
```

### Parameters - next

record  
A record buffer to receive the result.

### Return Value - next

true if the operation was successful; otherwise false.

## Method new

Initializes a new instance of the Object class.

```xpp
public void new(TableId tableId, [Common table])
```

### Parameters - new

tableId  

<!-- -->

table  

### Remarks - new

The list can contain records of the type that is specified by the tableId parameter.

### Examples - new

The following example uses a RecordInsertList object to insert three records in a single database operation.

```xpp
{ 
    RecordSortedList recordSortedList; 
    CustTable        custTable; 
    recordSortedList = new RecordSortedList(tablenum(CustTable)); 
    recordSortedList.sortOrder(fieldnum(custTable,AccountNum)); 
    ttsbegin; 
    // Prepare record #1 for insertion. 
    custTable.AccountNum = '1000'; 
    custTable.CreditMax = 10000.0; 
    recordSortedList.ins(custTable); 
    // Prepare record #2 for insertion. 
    custTable.AccountNum = '2000'; 
    custTable.CreditMax = 500.0; 
    recordSortedList.ins(custTable); 
    // Prepare record #3 for insertion. 
    custTable.AccountNum = '3000'; 
    custTable.CreditMax = 9999999.9; 
    recordSortedList.ins(custTable); 
    // All 3 records inserted in one database operation. 
    recordSortedList.insertDatabase();   
    ttscommit; 
}
```

## Method sortOrder

Defines the fields on which the records are sorted.

```xpp
public void sortOrder(FieldId fieldId, VarArg )
```

### Parameters - sortOrder

fieldId  

<!-- -->


### Remarks - sortOrder

You can specify one or more fields to sort on. This method can only be called one time on the same instance of the RecordSortedList class. You cannot change the sorting order after it has been set.

### Examples - sortOrder

The following example creates a list of DimensionSetRuleTable table records, and then sorts them by the SetId field, and then by the HierarchyId field.

```xpp
static RecordSortedList initRulesList() 
{ 
    RecordSortedList list; 
    list = new RecordSortedList(tablenum(DimensionSetRuleTable)); 
    list.sortOrder( 
        fieldnum(DimensionSetRuleTable, SetId),  
        fieldnum(DimensionSetRuleTable, HierarchyId)); 
    return list; 
}
```

## Method sortOrderFromContainer

Defines the fields on which the records are sorted.

```xpp
public void sortOrderFromContainer(container container)
```

### Parameters - sortOrderFromContainer

container  
The fields on which the list should be sorted. Each field is specified by a field ID; for example, by using the FieldNum function.

### Remarks - sortOrderFromContainer

If you do not have to supply the field list in a container, use RecordSortedList.sortOrder.

## Method insertDatabase

Inserts multiple records on a single trip to the database.

```xpp
public void insertDatabase([Connection connection])
```

### Parameters - insertDatabase

connection  

### Remarks - insertDatabase

After the call, the list entries remain in the RecordSortedList object. The RecordSortedList class must be located on the server before the insertDatabase method is called; otherwise, an exception is thrown. RecIds and other system-maintained fields are not assigned values until the insertDatabase method call is made. The method reverts to a record by record insert if any of the following conditions are met:

-   The table is not SQL-stored.
-   The insert method for the table is overloaded.
-   The table includes memo or container fields.

### Examples - insertDatabase

The following example shows how to insert three records in a single database operation.

```xpp
{ 
    RecordSortedList recordSortedList; 
    CustTable        custTable; 
    recordSortedList = new RecordSortedList(tablenum(CustTable)); 
    recordSortedList.sortOrder(fieldnum(custTable,AccountNum)); 
    ttsbegin; 
    // Prepare record #1 for insertion. 
    custTable.AccountNum = '1000'; 
    custTable.CreditMax = 10000.0; 
    recordSortedList.ins(custTable); 
    // Prepare record #2 for insertion. 
    custTable.AccountNum = '2000'; 
    custTable.CreditMax = 500.0; 
    recordSortedList.ins(custTable); 
    // Prepare record #3 for insertion. 
    custTable.AccountNum = '3000'; 
    custTable.CreditMax = 9999999.9; 
    recordSortedList.ins(custTable); 
    // All three records inserted in one database operation. 
    recordSortedList.insertDatabase();   
    ttscommit; 
}
```

