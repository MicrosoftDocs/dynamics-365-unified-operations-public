---
# required metadata

title: R Classes
description: 
author: RobinARH
manager: AnnBe
ms.date: 2016-02-24 00 - 59 - 11
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
ms.custom: 51721
ms.assetid: 156e93a0-58a6-4963-bd47-6fe33df353e8
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# R Classes



Class Random
------------

    class Random extends Object

The Random class generates random numbers.

### Remarks

Because this class operates on a global random generator, the individual random objects will interfere with each other. Therefore, it is not possible to predict the sequence of numbers for a specific random object.

### Examples

The following example prints 100 random numbers.

    static void example() 
    { 
        Random myRand = new Random(); 
        int i; 
        for(i=0;i<100;i++) 
        { 
            print myRand.nextInt(); 
        } 
    }

### Methods

| Method               | Description                                               |
|----------------------|-----------------------------------------------------------|
| public int nextInt() | Returns the next random number from the random generator. |
| public void new()    | Initializes a new instance of the Random class.           |

### Method nextInt

Returns the next random number from the random generator.

    public int nextInt()

#### Return Value

The next random integer number from the random generator.

#### Remarks

The value will be in the range from 0 to 32767 (0x7FFF).

### Method new

Initializes a new instance of the Random class.

    public void new()

## Class RecordInsertList
    class RecordInsertList extends Object

The RecordInsertList class provides array insertion capabilities in the kernel.

### Remarks

This class lets you insert more than one record into the database at a time, which reduces communication between the application and the database. Records are inserted only when the kernel finds the time appropriate, but they are inserted no later than the call to the insertDatabase, add, and insertDatabase methods. The RecordInsertList.add and RecordInsertList.insertDatabase methods return the accumulated number of records that are currently inserted, so that you can keep track of when the records are actually inserted. The array insert operation automatically falls back to classic record-by-record inserts when non-SQL based tables are used (for example, temporary tables) or when the insert method on the table is overridden (unless it is explicitly discarded). The RecordInsertList class resembles the RecordSortedList class, but it has built-in client/server support (it automatically packs data from one tier to another when this is required) and lacks the sort order features that are available in the RecordSortedList class.

### Examples

The following example uses the RecordInsertList class to copy a bill of materials (BOM) from one BOM to another.

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

### Methods

| Method                                                                                                                                                                                              | Description                                                                                       |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| public int add(Common record)                                                                                                                                                                       | Adds a record to a RecordInsertList object for subsequent insertion into the database.            |
| public int insertDatabase()                                                                                                                                                                         | Inserts all records that have not already been inserted into the current RecordInsertList object. |
| public void new(TableId tableId, \[boolean skipInsertMethod\], \[boolean skipDatabaseLog\], \[boolean skipEvents\], \[boolean skipAosValidation\], \[boolean skipRLSValidation\], \[Common table\]) | Creates a new object to hold records for insertion into the database.                             |

### Method add

Adds a record to a RecordInsertList object for subsequent insertion into the database.

    public int add(Common record)

#### Parameters

record  
A database buffer of the same type that is used to instantiate the class.

#### Return Value

An integer that indicates whether the record has been successfully added to the list.

#### Remarks

The add method can flush records to the database whenever this will speed up performance. However, to guarantee that all records in the list are inserted, use the RecordInsertList.insertDatabase method.

#### Examples

The following example uses the RecordInsertList class to copy a BOM from one BOM to another. The add method is used to add all the records in the BOM to the RecordInsertList object before a final call is made to the insertDatabase method to insert all remaining records.

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

### Method insertDatabase

Inserts all records that have not already been inserted into the current RecordInsertList object.

    public int insertDatabase()

#### Return Value

An integer that represents the total number of records that were inserted.

#### Remarks

The RecordInsertList.add method flushes records to the database whenever this will speed up performance.

#### Examples

The following example uses the RecordInsertList class to copy a BOM from one BOM to another. The RecordInsertList.add method is used to add all the records in the BOM to the RecordInsertList class before a final call is made to the insertDatabase method to insert all remaining records.

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

### Method new

Creates a new object to hold records for insertion into the database.

    public void new(TableId tableId, [boolean skipInsertMethod], [boolean skipDatabaseLog], [boolean skipEvents], [boolean skipAosValidation], [boolean skipRLSValidation], [Common table])

#### Parameters

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

#### Examples

The following example creates a new RecordInsertList class for the EventRuleField table. The insert method for the table is run when these records are inserted, and the insertion is recorded in the database log. However, CUD events are not generated for the insertion.

    recordInsertList = new RecordInsertList( 
        tablenum(EventRuleField), 
        false, 
        false, 
        true);

## Class RecordLinkList
    class RecordLinkList extends Object

The RecordLinkList class dynamically creates a cache of record buffers that can hold records of different types, and that is not keyed or sorted.

### Remarks

A recordLinkList object is a double-linked list that can hold records of different types at the same time. It is not keyed or sorted. The recordLinkList object is especially useful for passing records from different tables as a parameter instead of retrieving the same records again. There is no limit to the size of a recordSortedList object. It is the responsibility of the programmer to control its size and therefore its memory consumption.

### Examples

### Methods

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

### Method del

Deletes the record at the current position in the list.

    public int del()

#### Return Value

The number of records that remain in the list.

### Method fileId

Retrieves the table ID of the record at the current position in the list.

    public TableId fileId()

#### Return Value

The table ID.

### Method first

Puts the pointer on the first record in the list and, if it is present, copies the record into the buffer that is provided.

    public boolean first([Common record])

#### Parameters

record  
The record buffer that will contain the result; optional.

#### Return Value

true if the method succeeds; false if no records exist.

### Method get

Copies the record at the current position or the specified position to the provided record buffer, without affecting the pointer position.

    public boolean get(Common record, [int index])

#### Parameters

record  
The number of the record in the list to retrieve if the current record is not being retrieved; optional.

<!-- -->

index  
The number of the record in the list to retrieve if the current record is not being retrieved; optional.

#### Return Value

true if a record could be retrieved; otherwise, false.

### Method ins

Inserts a record at the end of a list.

    public int ins(Common record)

#### Parameters

record  
The record buffer that is used to hold the record to insert.

#### Return Value

The number of elements in the list.

### Method last

Puts the list at the last record and copies the record to the specified record buffer.

    public boolean last([Common record])

#### Parameters

record  
A record buffer that is used to hold the record that is retrieved; optional.

#### Return Value

true if the method succeeds; false if there are no records in the list.

### Method len

Returns the current number of records in the list.

    public int len()

#### Return Value

The number of records in the list.

### Method next

Puts the pointer on the next record and copies it to the provided buffer.

    public boolean next([Common record])

#### Parameters

record  
The record buffer of same type as the record at the position; optional.

#### Return Value

true if the method succeeds; false if there are no more records.

### Method peek

Retrieves the record at the current position in the list.

    public Common peek()

#### Return Value

A record buffer if the record is found.

### Method prev

Puts the pointer on the previous record in the list and copies the record to the specified buffer.

    public boolean prev([Common record])

#### Parameters

record  
The record buffer of the same type as the record to copy; optional.

#### Return Value

true if the pointer is not at the first record; otherwise, false.

### Method new

Initializes a new instance of the RecordLinkList class.

    public void new()

## Class RecordSortedList
    class RecordSortedList extends Object

The RecordSortedList class inserts multiple records in a single database trip.

### Remarks

Use RecordSortedList when you want a subset of data from a particular table, and you want it sorted in an order that does not currently exist as an index. A RecordSortedList object holds records from a single table. The list has a unique key that is defined by the fields listed by using the sortOrder method. Records are automatically sorted as they are inserted, they do not have to be inserted in sort sequence. RecordSortedList objects are particularly useful for passing a result-set as a parameter There is no limit to the size of a RecordSortedList object, but they are completely memory-based, so there are potential memory consumption problems. RecordSortedList objects must be server-located before the insertDatabase method can be called. Otherwise, an exception is thrown. Record level security (RLS) cannot be applied by the RecordSortedList class. RLS is applied by the RecordInsertList class). Use a RecordSortedList in preference to a temporary table in the following situations:

-   Only one sort order is needed.
-   The number of records is not too high (to avoid memory problems).

Compared to temporary tables, RecordSortedList objects:

-   Are faster.
-   Are not disk-based.
-   Only have one index.
-   Cannot be used in forms.
-   Require a call between the client and server per (grouped) read.

### Examples

### Methods

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

### Method del

Removes a record that has a key that matches the key fields in the recordBuffer from the recordSortedList.

    public boolean del(Common record)

#### Parameters

record  
A record buffer that contains the key values of the record to be deleted.

#### Return Value

true if a record was removed; otherwise false.

### Method find

Sets the record buffer to the contents of the record that has a key that matches the key fields in the record buffer, and positions the list to the record returned.

    public boolean find(Common record)

#### Parameters

record  
A record buffer that contains the key values to be searched for. The record found will replace the contents of the record buffer.

#### Return Value

true if a record is found; otherwise false.

### Method first

Positions the list to the first record in the list, and copies its contents to the record buffer.

    public boolean first(Common record)

#### Parameters

record  
A record buffer to contain first record in list.

#### Return Value

true if the method is successful; otherwise false.

### Method ins

Inserts a new record in a RecordSortedList, unless it is a duplicate.

    public boolean ins(Common record, [boolean updateIfExists])

#### Parameters

record  
Whether to discard or replace duplicate records; optional. If false, the new record will be discarded if it is a duplicate. If true, the new record will replace an existing record if it is a duplicate.

<!-- -->

updateIfExists  
Whether to discard or replace duplicate records; optional. If false, the new record will be discarded if it is a duplicate. If true, the new record will replace an existing record if it is a duplicate.

#### Return Value

true if the record was added or replaced; otherwise false.

### Method len

Returns the current number of records in a RecordSortedList object.

    public int len()

#### Return Value

The current number of records in the list.

### Method next

Sets the record buffer to the contents of the next record in the recordSortedList and positions the list to the record returned.

    public boolean next(Common record)

#### Parameters

record  
A record buffer to receive the result.

#### Return Value

true if the operation was successful; otherwise false.

### Method new

Initializes a new instance of the Object class.

    public void new(TableId tableId, [Common table])

#### Parameters

tableId  

<!-- -->

table  

#### Remarks

The list can contain records of the type that is specified by the tableId parameter.

#### Examples

The following example uses a RecordInsertList object to insert three records in a single database operation.

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

### Method sortOrder

Defines the fields on which the records are sorted.

    public void sortOrder(FieldId fieldId, VarArg )

#### Parameters

fieldId  

<!-- -->

  

#### Remarks

You can specify one or more fields to sort on. This method can only be called one time on the same instance of the RecordSortedList class. You cannot change the sorting order after it has been set.

#### Examples

The following example creates a list of DimensionSetRuleTable table records, and then sorts them by the SetId field, and then by the HierarchyId field.

    static RecordSortedList initRulesList() 
    { 
        RecordSortedList list; 
        list = new RecordSortedList(tablenum(DimensionSetRuleTable)); 
        list.sortOrder( 
            fieldnum(DimensionSetRuleTable, SetId),  
            fieldnum(DimensionSetRuleTable, HierarchyId)); 
        return list; 
    }

### Method sortOrderFromContainer

Defines the fields on which the records are sorted.

    public void sortOrderFromContainer(container container)

#### Parameters

container  
The fields on which the list should be sorted. Each field is specified by a field ID; for example, by using the FieldNum function.

#### Remarks

If you do not have to supply the field list in a container, use RecordSortedList.sortOrder.

### Method insertDatabase

Inserts multiple records on a single trip to the database.

    public void insertDatabase([Connection connection])

#### Parameters

connection  

#### Remarks

After the call, the list entries remain in the RecordSortedList object. The RecordSortedList class must be located on the server before the insertDatabase method is called; otherwise, an exception is thrown. RecIds and other system-maintained fields are not assigned values until the insertDatabase method call is made. The method reverts to a record by record insert if any of the following conditions are met:

-   The table is not SQL-stored.
-   The insert method for the table is overloaded.
-   The table includes memo or container fields.

#### Examples

The following example shows how to insert three records in a single database operation.

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

## Class RecordViewCache
    class RecordViewCache extends Object

### Remarks

### Examples

### Methods

| Method                       | Description                                     |
|------------------------------|-------------------------------------------------|
| public void new(Common view) | Initializes a new instance of the Object class. |

### Method new

Initializes a new instance of the Object class.

    public void new(Common view)

#### Parameters

view  

## Class ReferenceNode
    class ReferenceNode extends TreeNode

The ReferenceNode class represents a reference AOT node, exposing the kernel class to X++.

### Remarks

This class represents a node under the AOT References node. This class describes a managed assembly that is referenced from X++ code.

### Examples

### Methods

| Method | Description |
|--------|-------------|

## Class RelationPath
    class RelationPath extends Object

### Remarks

### Examples

### Methods

| Method                                                                                        | Description                                           |
|-----------------------------------------------------------------------------------------------|-------------------------------------------------------|
| public boolean isEqualTo(RelationPath otherRelationPath)                                      |                                                       |
| public boolean isPathCyclical(boolean excludePathRootTable)                                   |                                                       |
| public boolean isPathValid()                                                                  |                                                       |
| public List pathAsList()                                                                      |                                                       |
| public str pathAsString(\[str delimiter\])                                                    |                                                       |
| public str pathRelativeTable()                                                                |                                                       |
| public str pathRootTable()                                                                    |                                                       |
| ::public static RelationPath construct(RelationPath sourceRelationPath)                       |                                                       |
| ::public static RelationPath constructFromPathList(str pathRootTableName, List relationPath)  |                                                       |
| ::public static RelationPath constructFromPathString(str pathRootTableName, str relationPath) |                                                       |
| private void new()                                                                            | Initializes a new instance of the RelationPath class. |
| public void trimPathAtFront()                                                                 |                                                       |
| public void trimPathAtEnd()                                                                   |                                                       |

### Method isEqualTo

    public boolean isEqualTo(RelationPath otherRelationPath)

#### Parameters

otherRelationPath  

#### Return Value

### Method isPathCyclical

    public boolean isPathCyclical(boolean excludePathRootTable)

#### Parameters

excludePathRootTable  

#### Return Value

### Method isPathValid

    public boolean isPathValid()

#### Return Value

### Method pathAsList

    public List pathAsList()

#### Return Value

### Method pathAsString

    public str pathAsString([str delimiter])

#### Parameters

delimiter  

#### Return Value

### Method pathRelativeTable

    public str pathRelativeTable()

#### Return Value

### Method pathRootTable

    public str pathRootTable()

#### Return Value

### Method construct

    public static RelationPath construct(RelationPath sourceRelationPath)

#### Parameters

sourceRelationPath  

#### Return Value

### Method constructFromPathList

    public static RelationPath constructFromPathList(str pathRootTableName, List relationPath)

#### Parameters

pathRootTableName  

<!-- -->

relationPath  

#### Return Value

### Method constructFromPathString

    public static RelationPath constructFromPathString(str pathRootTableName, str relationPath)

#### Parameters

pathRootTableName  

<!-- -->

relationPath  

#### Return Value

### Method new

Initializes a new instance of the RelationPath class.

    private void new()

### Method trimPathAtFront

    public void trimPathAtFront()

### Method trimPathAtEnd

    public void trimPathAtEnd()

## Class RelativeFieldBinding
    class RelativeFieldBinding extends FieldBinding

### Remarks

### Examples

### Methods

| Method                                                                                   | Description                                                   |
|------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| public RelationPath relationPath()                                                       |                                                               |
| ::public static RelativeFieldBinding construct(str fieldName, RelationPath relationPath) |                                                               |
| ::public static RelativeFieldBinding create(container packedRelativeFieldBinding)        |                                                               |
| private void new()                                                                       | Initializes a new instance of the RelativeFieldBinding class. |

### Method relationPath

    public RelationPath relationPath()

#### Return Value

### Method construct

    public static RelativeFieldBinding construct(str fieldName, RelationPath relationPath)

#### Parameters

fieldName  

<!-- -->

relationPath  

#### Return Value

### Method create

    public static RelativeFieldBinding create(container packedRelativeFieldBinding)

#### Parameters

packedRelativeFieldBinding  

#### Return Value

### Method new

Initializes a new instance of the RelativeFieldBinding class.

    private void new()

## Class Report
    class Report extends TreeNode

The Report class lets users use reports that are present in the Microsoft Dynamics AX Application Object Tree (AOT) and report creation by using code instead of the AOT.

### Remarks

A Report object contains a query and zero or more designs. Each design is a definition of the layout of a report that can be displayed on screen or printed. A Report object also has ReportRun methods that can be overridden. This class enables you to create, read, update, and delete X++ code and metadata.

### Examples

The following code example creates and runs a report that is not present in the AOT.

    static void test(args a) 
    { 
        report r; 
        reportDesign rd; 
        reportSection rs; 
        reportRun rr; 
        // Creates a simple report that is not present in  
        // the AOT. 
        r = new report(); 
        rd = r.addDesign("myDesign"); 
        // Adds a section that is triggered by execute(1). 
        rs = rd.addProgrammableSection(1);
        rs.addTextControl("Hello world"); 
        // Runs the report. 
        rr = new reportRun(r); 
        // Runs the SysPrintForm form. 
        if (rr.prompt())  
        { 
            // Executes the programmable section. 
            rr.execute(1);  
            // Prints the report to the target selected 
            // during the previous prompt call. 
            rr.print();    
        } 
    }

### Methods

| Method                                                              | Description                                                                                                                               |
|---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public ReportDesign addDesign(\[str name\], \[container buffer\])   | Creates a reportDesign that belongs to a report.                                                                                          |
| public boolean allowCheck(\[boolean value\])                        |                                                                                                                                           |
| public boolean autoJoin(\[boolean value\])                          |                                                                                                                                           |
| public str changedBy(\[str value\])                                 | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])                             | Gets or sets the date an application object was last changed.                                                                             |
| public str changedTime(\[str value\])                               | Gets or sets the time an application object was last changed.                                                                             |
| public str createdBy(\[str value\])                                 | Gets or sets the name of the user who created the application object.                                                                     |
| public Date creationDate(\[Date value\])                            | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])                              |                                                                                                                                           |
| public ReportDesign design(\[str name\])                            | Retrieves an existing design.                                                                                                             |
| public int designCount()                                            | Retrieves the number of designs in a given report.                                                                                        |
| public ReportDesign designNumber(\[int number\])                    | Gets an existing design.                                                                                                                  |
| public boolean interactive(\[boolean value\])                       |                                                                                                                                           |
| public str name(\[str value\])                                      | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])                                  |                                                                                                                                           |
| public container pack()                                             | Serializes the current instance of the Report class.                                                                                      |
| public Query query(\[Query query\])                                 |                                                                                                                                           |
| public boolean saved()                                              | Indicates whether the report has been saved to disk.                                                                                      |
| public void new(\[AnyType nameOrContainer\], \[AnyType container\]) | Initializes a new instance of the TreeNode class.                                                                                         |
| public void dump()                                                  | Writes an overview of the report's contents to the Infolog.                                                                               |

### Method addDesign

Creates a reportDesign that belongs to a report.

    public ReportDesign addDesign([str name], [container buffer])

#### Parameters

name  
Lets the design have the contents given by buffer.

<!-- -->

buffer  
Lets the design have the contents given by buffer.

#### Return Value

The created reportDesign.

#### Remarks

The buffer argument can be a container created by the pack method.

#### Examples

This job demonstrates how addDesign can be used to generate a design that is a copy of another design.

    static void demoAddDesign(args a) 
    {  
        report r1; 
        report r2; 
        reportDesign rd; 
        reportSection rs; 
        reportRun rr; 
        container c; 
        // Create a simple report r1. 
        r1 = new report(); 
        rd = r1.addDesign("Design1"); 
        rs = rd.addProgrammableSection(1); 
        rs.addTextControl("Hello world"); 
        c = rd.Pack(); // make a container containing r1's design 
        // Create a report r2 having a design that is a copy of r1's design. 
        r2 = new report(); 
        r2.AddDesign("design2", c); 
        // Run the report. 
        rr = new reportRun(r2, "design2"); 
        // Run the sysPrintForm form. 
        if (rr.prompt()) 
        { 
            // Execute the programableSection. 
            rr.execute(1);  
            // Print report to the target, such as printer or screen. 
            rr.print();    
        } 
    }

### Method allowCheck

    public boolean allowCheck([boolean value])

#### Parameters

value  

#### Return Value

### Method autoJoin

    public boolean autoJoin([boolean value])

#### Parameters

value  

#### Return Value

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method design

Retrieves an existing design.

    public ReportDesign design([str name])

#### Parameters

name  
The name of the report to be returned; optional.

#### Return Value

The design that has the specified name, or nullNothingnullptrunita null reference (Nothing in Visual Basic) if it was not found.

#### Remarks

If no argument is supplied and the report only contains one design, the method returns the one design.

#### Examples

    static void testDesign(args a) 
    { 
        report r; 
        reportDesign rd; 
        r = new report("Cust"); 
        rd = r.Design(); 
        if (rd) 
            print "a) r.design() : ", rd.Name(); 
        rd = r.Design(""); 
        if (rd) 
            print "b) r.design(emptyString) : ", rd.Name(); 
        rd = r.Design('customer'); 
        if (rd) 
            print "c) r.design(customer) : ", rd.Name(); 
        pause; 
    }

### Method designCount

Retrieves the number of designs in a given report.

    public int designCount()

#### Return Value

The number of designs.

#### Examples

    static void testDesign(args a) 
    { 
        report r = new report(); 
        print "A newly created report has ", r.DesignCount(), " designs"; 
        pause; 
    }

### Method designNumber

Gets an existing design.

    public ReportDesign designNumber([int number])

#### Parameters

number  
An integer that specifies the desired design; optional.

#### Return Value

The specified reportDesign, or nullNothingnullptrunita null reference (Nothing in Visual Basic) if the design did not exist.

#### Remarks

If number is &lt; 1, design 1 is returned.

#### Examples

    void testDesign(args a) 
    { 
        report r; 
        reportDesign rd; 
        int i; 
        r = new report("myReport"); 
        if (r.DesignCount() == 0) 
        { 
            print "The report has no designs"; pause; 
        } 
        for (i=1; i<=r.DesignCount();i++) 
        { 
            rd = r.DesignNumber(i); 
            print "Design No. ", i, " has name ", rd.Name(); 
        } 
        pause; 
    }

### Method interactive

    public boolean interactive([boolean value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method pack

Serializes the current instance of the Report class.

    public container pack()

#### Return Value

A container that contains the current instance of the Report class.

#### Remarks

The returned container can be used as first argument to the report constructor.

#### Examples

The following example stores a report named "cust" in a container and runs the report in the container (not the container in the AOT).

    static void testReportPack(args a) 
    { 
        report r1; 
        report r2; 
        reportRun rr; 
        container c; 
        r1 = new report("cust"); 
        c = r1.Pack(); 
        r2 = new report(c); 
        rr = new reportrun(r2); 
        rr.Run(); 
    }

### Method query

    public Query query([Query query])

#### Parameters

query  

#### Return Value

### Method saved

Indicates whether the report has been saved to disk.

    public boolean saved()

#### Return Value

true if the report has been saved to disc; otherwise false.

#### Remarks

A report in the AOT can only be run if it has been saved to disk.

#### Examples

    static void testReportSaved(args a) 
    { 
        report r; 
        reportRun rr; 
        r = new report(); 
        r.AddDesign(); 
        print "before save, saved : ", r.Saved(); pause; 
        r.saved(); 
        print "after save, saved : ", r.Saved(); pause; 
        rr = new reportrun(r); 
        rr.Run(); 
    }

### Method new

Initializes a new instance of the TreeNode class.

    public void new([AnyType nameOrContainer], [AnyType container])

#### Parameters

nameOrContainer  

<!-- -->

container  

#### Remarks

The parameter format is as follows:

-   () – Creates a report object that is not present in the AOT.
-   (c) – Creates a report object that is not present in the AOT, the contents of which are given by the container c.
-   ("existingReportName") – Retrieves a report object that is found in the AOT.
-   ("nonExistingReportName") – Creates a report object in the AOT.
-   ("nonExistingReportName", c) – Creates a report object in the AOT, the contents of which are given by the container c.

The container c should be created by the pack method.

### Method dump

Writes an overview of the report's contents to the Infolog.

    public void dump()

#### Remarks

The lines written to the Infolog are identical to the information shown when you expand the report in the AOT.

#### Examples

    static void testReportDump(args a) 
    { 
        report r = new report("cust"); 
        r.Dump(); 
    }

## Class ReportAutoDesignSpecs
    class ReportAutoDesignSpecs extends TreeNode

The ReportAutoDesignSpecs class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                            | Description                                                        |
|-----------------------------------------------------------------------------------|--------------------------------------------------------------------|
| public ReportSection addProgrammableSection(int number)                           |                                                                    |
| public ReportSection addSection(ReportBlockType sectionType, \[TableId tableId\]) |                                                                    |
| public boolean autoHeader(\[boolean value\])                                      |                                                                    |
| public str footerText(\[str value\])                                              |                                                                    |
| public boolean grandHeader(\[boolean value\])                                     |                                                                    |
| public boolean grandTotal(\[boolean value\])                                      | Determines whether the FooterText property value can be displayed. |
| public str headerText(\[str value\])                                              |                                                                    |
| public boolean view()                                                             |                                                                    |

### Method addProgrammableSection

    public ReportSection addProgrammableSection(int number)

#### Parameters

number  

#### Return Value

### Method addSection

    public ReportSection addSection(ReportBlockType sectionType, [TableId tableId])

#### Parameters

sectionType  

<!-- -->

tableId  

#### Return Value

### Method autoHeader

    public boolean autoHeader([boolean value])

#### Parameters

value  

#### Return Value

### Method footerText

    public str footerText([str value])

#### Parameters

value  

#### Return Value

### Method grandHeader

    public boolean grandHeader([boolean value])

#### Parameters

value  

#### Return Value

### Method grandTotal

Determines whether the FooterText property value can be displayed.

    public boolean grandTotal([boolean value])

#### Parameters

value  

#### Return Value

true if the FooterText property value is displayed; otherwise, false.

#### Remarks

The grandTotal property is available only when a report has untested, multiple data sources.

### Method headerText

    public str headerText([str value])

#### Parameters

value  

#### Return Value

### Method view

    public boolean view()

#### Return Value

## Class ReportBitmapControl
    class ReportBitmapControl extends ReportControl

The ReportBitmapControl class creates, reads, updates, and deletes X++ code and metadata.

### Remarks

You must have access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                   | Description                                                                                                                               |
|--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                           |
| public int arrayIndex(\[int value\])                                     |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public int backStyle(\[int value\])                                      | Determiness whether the control background can be transparent.                                                                            |
| public int bottomMarginAndFrame()                                        |                                                                                                                                           |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                           |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                           |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                           |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                           |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                           |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                       |
| public ReportFieldType controlType()                                     |                                                                                                                                           |
| public str cssClass(\[str value\])                                       |                                                                                                                                           |
| public FieldId dataField(\[FieldId value\])                              |                                                                                                                                           |
| public str dataMethod(\[str value\])                                     |                                                                                                                                           |
| public int delete()                                                      |                                                                                                                                           |
| public str effectiveFont()                                               |                                                                                                                                           |
| public str fontInfoPrinter()                                             |                                                                                                                                           |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                           |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                           |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                           |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                           |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                           |
| public str fontInfoScreen()                                              |                                                                                                                                           |
| public int fontInfoScreenAscent()                                        |                                                                                                                                           |
| public int fontInfoScreenDescent()                                       |                                                                                                                                           |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                           |
| public int fontInfoScreenHeight()                                        |                                                                                                                                           |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                           |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                                       |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                           |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                           |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                            |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                           |
| public str heightStr(\[str value\])                                      |                                                                                                                                           |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                           |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                                   |
| public str imageName(\[str value\])                                      |                                                                                                                                           |
| public int imageResource(\[int value\])                                  |                                                                                                                                           |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                     |
| public int labelBold(\[int value\])                                      |                                                                                                                                           |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                                           |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                           |
| public str labelFont(\[str value\])                                      |                                                                                                                                           |
| public int labelFontSize(\[int value\])                                  |                                                                                                                                           |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                                           |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                           |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                           |
| public int labelPosition(\[int value\])                                  |                                                                                                                                           |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                                           |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                                           |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                                           |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                                           |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                                           |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                                           |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                           |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                           |
| public int leftMarginAnFrame()                                           |                                                                                                                                           |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                           |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                           |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                           |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                           |
| public int leftMode(\[int value\])                                       |                                                                                                                                           |
| public str leftStr(\[str value\])                                        |                                                                                                                                           |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                           |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                           |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                               |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                           |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                           |
| public str menuItemName(\[str value\])                                   |                                                                                                                                           |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                           |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                           |
| public str name(\[str value\])                                           | Gets or sets the name that is used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object. |
| public int numberOfLines(int height100mm)                                |                                                                                                                                           |
| public int position(\[int value\])                                       |                                                                                                                                           |
| public str previewInfo(str string)                                       |                                                                                                                                           |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                           |
| public boolean resizeBitmap(\[boolean value\])                           |                                                                                                                                           |
| public int right100mm()                                                  |                                                                                                                                           |
| public int right100mmInclBorder()                                        |                                                                                                                                           |
| public int rightMarginAndFrame()                                         |                                                                                                                                           |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                           |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                           |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                           |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                           |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                           |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                           |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                                           |
| public boolean showPicAsText(\[boolean value\])                          |                                                                                                                                           |
| public TableId table(\[TableId value\])                                  | Gets or sets the table ID associated with the object.                                                                                     |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                           |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                           |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                           |
| public int topMarginAndFrame()                                           |                                                                                                                                           |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                           |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                           |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                           |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                           |
| public int topMode(\[int value\])                                        |                                                                                                                                           |
| public str topStr(\[str value\])                                         |                                                                                                                                           |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                           |
| public Real topValue(\[Real value\])                                     |                                                                                                                                           |
| public boolean visible(\[boolean value\])                                |                                                                                                                                           |
| public boolean warnIfMissing(\[boolean value\])                          |                                                                                                                                           |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                           |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                           |
| public str webTarget(\[str value\])                                      |                                                                                                                                           |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                           |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                           |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                            |
| public int widthOfString100mm(str string)                                |                                                                                                                                           |
| public str widthStr(\[str value\])                                       |                                                                                                                                           |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                           |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                                    |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                                           |
| public void top(Real value, Units unit)                                  |                                                                                                                                           |
| public void show()                                                       |                                                                                                                                           |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                           |
| public void left(Real value, Units unit)                                 |                                                                                                                                           |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                           |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                                   |
| public void hide()                                                       |                                                                                                                                           |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                           |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                           |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                                    |

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                        |
|--------|-------------------------------|
| 0      | Default.                      |
| 1      | The MicrosoftWindows palette. |
| 2      | The true-color scheme.        |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method imageName

    public str imageName([str value])

#### Parameters

value  

#### Return Value

### Method imageResource

    public int imageResource([int value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelTabLeader

    public int labelTabLeader([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthStr

    public str labelWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method labelWidthUnit

    public Units labelWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public Real labelWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method resizeBitmap

    public boolean resizeBitmap([boolean value])

#### Parameters

value  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method showPicAsText

    public boolean showPicAsText([boolean value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method warnIfMissing

    public boolean warnIfMissing([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method labelWidth

    public void labelWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method show

    public void show()

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method hide

    public void hide()

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

## Class ReportControl
    class ReportControl extends TreeNode

The ReportControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                     | Description |
|------------------------------------------------------------|-------------|
| public int bottomMarginAndFrame()                          |             |
| public ReportFieldType controlType()                       |             |
| public int delete()                                        |             |
| public str effectiveFont()                                 |             |
| public str fontInfoPrinter()                               |             |
| public int fontInfoPrinterAscent()                         |             |
| public int fontInfoPrinterDescent()                        |             |
| public int fontInfoPrinterExtLead()                        |             |
| public int fontInfoPrinterHeight()                         |             |
| public int fontInfoPrinterIntLead()                        |             |
| public str fontInfoScreen()                                |             |
| public int fontInfoScreenAscent()                          |             |
| public int fontInfoScreenDescent()                         |             |
| public int fontInfoScreenExtLead()                         |             |
| public int fontInfoScreenHeight()                          |             |
| public int fontInfoScreenIntLead()                         |             |
| public int height100mm(\[int heightExclBorder\])           |             |
| public int height100mmInclBorder(\[int heightInclBorder\]) |             |
| public int heightOfWordWrappedString100mm(str string)      |             |
| public int left100mm(\[int leftExclBorder\])               |             |
| public int left100mmInclBorder(\[int leftInclBorder\])     |             |
| public int leftMarginAnFrame()                             |             |
| public int numberOfLines(int height100mm)                  |             |
| public int position(\[int value\])                         |             |
| public str previewInfo(str string)                         |             |
| public int previewXCompensation100mm(str string)           |             |
| public int right100mm()                                    |             |
| public int right100mmInclBorder()                          |             |
| public int rightMarginAndFrame()                           |             |
| public str setHeightGetText(int lines, str string)         |             |
| public int top100mm(\[int topExclBorder\])                 |             |
| public int top100mmInclBorder(\[int topInclBorder\])       |             |
| public int topMarginAndFrame()                             |             |
| public int width100mm(\[int widthExclBorder\])             |             |
| public int width100mmInclBorder(\[int widthInclBorder\])   |             |
| public int widthOfString100mm(str string)                  |             |
| public void show()                                         |             |
| public void hide()                                         |             |

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method show

    public void show()

### Method hide

    public void hide()

## Class ReportDateControl
    class ReportDateControl extends ReportControl

The ReportDateControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                   | Description                                                                                                                               |
|--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                           |
| public int arrayIndex(\[int value\])                                     |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public int backgroundColor(\[int value\])                                | Gets or sets the background color of the control.                                                                                         |
| public int backStyle(\[int value\])                                      | Determiness whether the control background can be transparent.                                                                            |
| public int bold(\[int value\])                                           | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int bottomMarginAndFrame()                                        |                                                                                                                                           |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                           |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                           |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                           |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                           |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                           |
| public int characterSet(\[int value\])                                   | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                       |
| public ReportFieldType controlType()                                     |                                                                                                                                           |
| public str cssClass(\[str value\])                                       |                                                                                                                                           |
| public FieldId dataField(\[FieldId value\])                              |                                                                                                                                           |
| public str dataMethod(\[str value\])                                     |                                                                                                                                           |
| public int dateDay(\[int value\])                                        |                                                                                                                                           |
| public int dateFormat(\[int value\])                                     |                                                                                                                                           |
| public int dateMonth(\[int value\])                                      |                                                                                                                                           |
| public int dateSeparator(\[int value\])                                  |                                                                                                                                           |
| public int dateYear(\[int value\])                                       |                                                                                                                                           |
| public int delete()                                                      |                                                                                                                                           |
| public str effectiveFont()                                               |                                                                                                                                           |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])         |                                                                                                                                           |
| public str font(\[str value\])                                           | Gets or sets the name of the font for the control to use.                                                                                 |
| public str fontInfoPrinter()                                             |                                                                                                                                           |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                           |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                           |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                           |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                           |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                           |
| public str fontInfoScreen()                                              |                                                                                                                                           |
| public int fontInfoScreenAscent()                                        |                                                                                                                                           |
| public int fontInfoScreenDescent()                                       |                                                                                                                                           |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                           |
| public int fontInfoScreenHeight()                                        |                                                                                                                                           |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                           |
| public int fontSize(\[int value\])                                       | Gets or sets the size of the font for the control to use.                                                                                 |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                                       |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                           |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                           |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                            |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                           |
| public str heightStr(\[str value\])                                      |                                                                                                                                           |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                           |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                                   |
| public boolean italic(\[boolean value\])                                 |                                                                                                                                           |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                     |
| public int labelBold(\[int value\])                                      |                                                                                                                                           |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                                           |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                           |
| public str labelFont(\[str value\])                                      |                                                                                                                                           |
| public int labelFontSize(\[int value\])                                  |                                                                                                                                           |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                                           |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                           |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                           |
| public int labelPosition(\[int value\])                                  |                                                                                                                                           |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                                           |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                                           |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                                           |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                                           |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                                           |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                                           |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                           |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                           |
| public int leftMarginAnFrame()                                           |                                                                                                                                           |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                           |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                           |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                           |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                           |
| public int leftMode(\[int value\])                                       |                                                                                                                                           |
| public str leftStr(\[str value\])                                        |                                                                                                                                           |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                           |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                           |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                               |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                           |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                           |
| public str menuItemName(\[str value\])                                   |                                                                                                                                           |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                           |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                           |
| public str name(\[str value\])                                           | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public int numberOfLines(int height100mm)                                |                                                                                                                                           |
| public int position(\[int value\])                                       |                                                                                                                                           |
| public str previewInfo(str string)                                       |                                                                                                                                           |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                           |
| public int right100mm()                                                  |                                                                                                                                           |
| public int right100mmInclBorder()                                        |                                                                                                                                           |
| public int rightMarginAndFrame()                                         |                                                                                                                                           |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                           |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                           |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                           |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                           |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                           |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                           |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                                           |
| public TableId table(\[TableId value\])                                  | Gets or sets the table ID associated with the object.                                                                                     |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                           |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                           |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                           |
| public int topMarginAndFrame()                                           |                                                                                                                                           |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                           |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                           |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                           |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                           |
| public int topMode(\[int value\])                                        |                                                                                                                                           |
| public str topStr(\[str value\])                                         |                                                                                                                                           |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                           |
| public Real topValue(\[Real value\])                                     |                                                                                                                                           |
| public boolean underline(\[boolean value\])                              |                                                                                                                                           |
| public boolean visible(\[boolean value\])                                |                                                                                                                                           |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                           |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                           |
| public str webTarget(\[str value\])                                      |                                                                                                                                           |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                           |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                           |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                            |
| public int widthOfString100mm(str string)                                |                                                                                                                                           |
| public str widthStr(\[str value\])                                       |                                                                                                                                           |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                           |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                                    |
| public void left(Real value, Units unit)                                 |                                                                                                                                           |
| public void top(Real value, Units unit)                                  |                                                                                                                                           |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                           |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                           |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                                           |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                                    |
| public void hide()                                                       |                                                                                                                                           |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                                   |
| public void show()                                                       |                                                                                                                                           |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                           |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                           |

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method dateDay

    public int dateDay([int value])

#### Parameters

value  

#### Return Value

### Method dateFormat

    public int dateFormat([int value])

#### Parameters

value  

#### Return Value

### Method dateMonth

    public int dateMonth([int value])

#### Parameters

value  

#### Return Value

### Method dateSeparator

    public int dateSeparator([int value])

#### Parameters

value  

#### Return Value

### Method dateYear

    public int dateYear([int value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelTabLeader

    public int labelTabLeader([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthStr

    public str labelWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method labelWidthUnit

    public Units labelWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public Real labelWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method labelWidth

    public void labelWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method hide

    public void hide()

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method show

    public void show()

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

## Class ReportDateTimeControl
    class ReportDateTimeControl extends ReportControl

### Remarks

### Examples

### Methods

| Method                                                                   | Description                                                                                                                                |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                            |
| public int arrayIndex(\[int value\])                                     |                                                                                                                                            |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                         |
| public int backgroundColor(\[int value\])                                | Gets or sets the background color of the control.                                                                                          |
| public int backStyle(\[int value\])                                      | Determiness whether the control background can be transparent.                                                                             |
| public int bold(\[int value\])                                           | Gets or sets the weight of font that is used to output text in the control.                                                                |
| public int bottomMarginAndFrame()                                        |                                                                                                                                            |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                            |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                            |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                            |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                            |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                            |
| public int characterSet(\[int value\])                                   | Gets or sets the character set of the font.                                                                                                |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                              |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                        |
| public ReportFieldType controlType()                                     |                                                                                                                                            |
| public str cssClass(\[str value\])                                       |                                                                                                                                            |
| public FieldId dataField(\[FieldId value\])                              |                                                                                                                                            |
| public str dataMethod(\[str value\])                                     |                                                                                                                                            |
| public int dateDay(\[int value\])                                        |                                                                                                                                            |
| public int dateFormat(\[int value\])                                     |                                                                                                                                            |
| public int dateMonth(\[int value\])                                      |                                                                                                                                            |
| public int dateSeparator(\[int value\])                                  |                                                                                                                                            |
| public int dateYear(\[int value\])                                       |                                                                                                                                            |
| public int delete()                                                      |                                                                                                                                            |
| public str effectiveFont()                                               |                                                                                                                                            |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])         |                                                                                                                                            |
| public str font(\[str value\])                                           | Gets or sets the name of the font for the control to use.                                                                                  |
| public str fontInfoPrinter()                                             |                                                                                                                                            |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                            |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                            |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                            |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                            |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                            |
| public str fontInfoScreen()                                              |                                                                                                                                            |
| public int fontInfoScreenAscent()                                        |                                                                                                                                            |
| public int fontInfoScreenDescent()                                       |                                                                                                                                            |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                            |
| public int fontInfoScreenHeight()                                        |                                                                                                                                            |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                            |
| public int fontSize(\[int value\])                                       | Gets or sets the size of the font for the control to use.                                                                                  |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                                        |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                            |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                            |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                             |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                            |
| public str heightStr(\[str value\])                                      |                                                                                                                                            |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                            |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                                    |
| public boolean italic(\[boolean value\])                                 |                                                                                                                                            |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                      |
| public int labelBold(\[int value\])                                      |                                                                                                                                            |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                                            |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                            |
| public str labelFont(\[str value\])                                      |                                                                                                                                            |
| public int labelFontSize(\[int value\])                                  |                                                                                                                                            |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                                            |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                            |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                            |
| public int labelPosition(\[int value\])                                  |                                                                                                                                            |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                                            |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                                            |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                                            |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                                            |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                                            |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                                            |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                            |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                            |
| public int leftMarginAnFrame()                                           |                                                                                                                                            |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                            |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                            |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                            |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                            |
| public int leftMode(\[int value\])                                       |                                                                                                                                            |
| public str leftStr(\[str value\])                                        |                                                                                                                                            |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                            |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                            |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                            |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                            |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                                |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                            |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                            |
| public str menuItemName(\[str value\])                                   |                                                                                                                                            |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                            |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                            |
| public str name(\[str value\])                                           | Gets or sets the name that used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public int numberOfLines(int height100mm)                                |                                                                                                                                            |
| public int position(\[int value\])                                       |                                                                                                                                            |
| public str previewInfo(str string)                                       |                                                                                                                                            |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                            |
| public int right100mm()                                                  |                                                                                                                                            |
| public int right100mmInclBorder()                                        |                                                                                                                                            |
| public int rightMarginAndFrame()                                         |                                                                                                                                            |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                            |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                            |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                            |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                            |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                            |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                            |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                                            |
| public TableId table(\[TableId value\])                                  | Gets or sets the table ID associated with the object.                                                                                      |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                            |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                            |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                            |
| public int topMarginAndFrame()                                           |                                                                                                                                            |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                            |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                            |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                            |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                            |
| public int topMode(\[int value\])                                        |                                                                                                                                            |
| public str topStr(\[str value\])                                         |                                                                                                                                            |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                            |
| public Real topValue(\[Real value\])                                     |                                                                                                                                            |
| public boolean underline(\[boolean value\])                              |                                                                                                                                            |
| public boolean visible(\[boolean value\])                                |                                                                                                                                            |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                            |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                            |
| public str webTarget(\[str value\])                                      |                                                                                                                                            |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                            |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                            |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                             |
| public int widthOfString100mm(str string)                                |                                                                                                                                            |
| public str widthStr(\[str value\])                                       |                                                                                                                                            |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                            |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                                     |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                                    |
| public void left(Real value, Units unit)                                 |                                                                                                                                            |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                            |
| public void hide()                                                       |                                                                                                                                            |
| public void top(Real value, Units unit)                                  |                                                                                                                                            |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                            |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                                            |
| public void show()                                                       |                                                                                                                                            |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                            |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                                     |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                            |

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of MicrosoftWindows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of MicrosoftWindows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                        |
|--------|-------------------------------|
| 0      | Default.                      |
| 1      | The MicrosoftWindows palette. |
| 2      | The true-color scheme.        |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method dateDay

    public int dateDay([int value])

#### Parameters

value  

#### Return Value

### Method dateFormat

    public int dateFormat([int value])

#### Parameters

value  

#### Return Value

### Method dateMonth

    public int dateMonth([int value])

#### Parameters

value  

#### Return Value

### Method dateSeparator

    public int dateSeparator([int value])

#### Parameters

value  

#### Return Value

### Method dateYear

    public int dateYear([int value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelTabLeader

    public int labelTabLeader([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthStr

    public str labelWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method labelWidthUnit

    public Units labelWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public Real labelWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method hide

    public void hide()

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method labelWidth

    public void labelWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method show

    public void show()

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

## Class ReportDesign
    class ReportDesign extends TreeNode

The ReportDesign class determines the contents of a report.

### Remarks

A ReportDesign object is a collection of ReportSection objects or SectionTemplate objects that determines the contents of a report. Each report contains a ReportDesign node in the Microsoft Dynamics AX Application Object Tree (AOT), below the Designs node. The ReportDesign node always contains a node that is named AutoDesignSpecs, and it can contain a node that is named Design, which is referred to as the generated design. A ReportDesign node should contain either one or more SectionTemplate nodes (below the AutoDesignSpecs node) or a generated design. If it contains both, only the generated design is used. This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. A report that does not have a generated design offers more flexibility to the end user than a report that has a generated design. For example, a user who is running a report that does not have a generated design can decide in the query which sums to include in the report. A generated design is then created during the execution of the report, and it will contain footer sections that correspond to the user's choice. If a report has a generated design, the existence of footer sections in the generated design controls which sums are printed in the report.

### Examples

The following example creates a simple report that is not present in the AOT.

    static void test(args a) 
    {  
        report r; 
        reportDesign rd; 
        reportSection rs; 
        reportRun rr; 
        r = new report(); 
        rd = r.addDesign("myDesign"); 
        // Add a section triggered by execute(1). 
        rs = rd.addProgrammableSection(1);  
        rs.addTextControl("Hello world"); 
        // Run the report. 
        rr = new reportRun(r); 
        // Run the sysPrintForm form. 
        if (rr.prompt())  
        { 
            // Execute the programmableSection. 
            rr.execute(1);  
            // Print the report to the target, such as printer or screen. 
            rr.print();    
        } 
    }

### Methods

| Method                                                                                                 | Description                                                                                                                               |
|--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public ReportSection addProgrammableSection(int number)                                                |                                                                                                                                           |
| public ReportSection addSection(ReportBlockType sectionType, \[TableId tableId\], \[FieldId fieldId\]) | Adds a report section to a design.                                                                                                        |
| public ReportSectionGroup addSectionGroup(TableId tableId, \[FieldId fieldId\])                        | Adds a section group to a design.                                                                                                         |
| public int arrange()                                                                                   |                                                                                                                                           |
| public int arrangeWhen(\[int value\])                                                                  |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                                                      | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public ReportAutoDesignSpecs autoDesignSpecs()                                                         |                                                                                                                                           |
| public ReportSection autoSection(TableId tableId, \[int number\])                                      |                                                                                                                                           |
| public int autoSectionControlCount()                                                                   |                                                                                                                                           |
| public ReportControl autoSectionControlNumber(int number)                                              |                                                                                                                                           |
| public int autoSectionCount()                                                                          |                                                                                                                                           |
| public ReportSection autoSectionNumber(int number)                                                     |                                                                                                                                           |
| public int bold(\[int value\])                                                                         | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int bottomMarginMode(\[int value\])                                                             |                                                                                                                                           |
| public str bottomMarginStr(\[str value\])                                                              |                                                                                                                                           |
| public Units bottomMarginUnit(\[Units value\])                                                         |                                                                                                                                           |
| public Real bottomMarginValue(\[Real value\])                                                          |                                                                                                                                           |
| public str caption(\[str value\])                                                                      | Gets or set the caption of the control.                                                                                                   |
| public int characterSet(\[int value\])                                                                 | Gets or sets the character set of the font.                                                                                               |
| public boolean collate(\[boolean collate\])                                                            |                                                                                                                                           |
| public int colorScheme(\[int value\])                                                                  | Gets or sets the color scheme of the control.                                                                                             |
| public ReportControl control(TableId tableId, FieldId fieldId)                                         | Finds a control in the generated design, based on the control's table and dataField properties.                                           |
| public int controlCount()                                                                              |                                                                                                                                           |
| public ReportControl controlName(str name)                                                             | Finds a control in the generated design, based on the control's Name property.                                                            |
| public ReportControl controlNumber(int number)                                                         |                                                                                                                                           |
| public int copies(\[int numberOfCopies\])                                                              |                                                                                                                                           |
| public int delete()                                                                                    | Deletes the node from the AOT.                                                                                                            |
| public str description(\[str value\])                                                                  |                                                                                                                                           |
| public str deviceName(\[str device\])                                                                  |                                                                                                                                           |
| public str driverName()                                                                                |                                                                                                                                           |
| public boolean edit()                                                                                  |                                                                                                                                           |
| public str emptyReportPrompt(\[str value\])                                                            |                                                                                                                                           |
| public int fitToPage(\[int value\])                                                                    |                                                                                                                                           |
| public str font(\[str value\])                                                                         | Gets or sets the name of the font for the control to use.                                                                                 |
| public int fontSize(\[int value\])                                                                     | Gets or sets the size of the font for the control to use.                                                                                 |
| public int foregroundColor(\[int value\])                                                              | Gets or sets the text color for the control to use.                                                                                       |
| public int from(\[int fromPage\])                                                                      |                                                                                                                                           |
| public int generateDesign()                                                                            |                                                                                                                                           |
| public int getNumberOfPrinters()                                                                       |                                                                                                                                           |
| public str getPrinter(int number)                                                                      |                                                                                                                                           |
| public PrintMedium getTarget()                                                                         | Returns the print medium target for the report.                                                                                           |
| public boolean hideBorder(\[boolean value\])                                                           |                                                                                                                                           |
| public boolean italic(\[boolean value\])                                                               |                                                                                                                                           |
| public str jobType(\[str value\])                                                                      |                                                                                                                                           |
| public int language(\[int value\])                                                                     |                                                                                                                                           |
| public str languageID(\[str lan\])                                                                     |                                                                                                                                           |
| public int leftMarginMode(\[int value\])                                                               |                                                                                                                                           |
| public str leftMarginStr(\[str value\])                                                                |                                                                                                                                           |
| public Units leftMarginUnit(\[Units value\])                                                           |                                                                                                                                           |
| public Real leftMarginValue(\[Real value\])                                                            |                                                                                                                                           |
| public container loadDiskSettings()                                                                    |                                                                                                                                           |
| public str localWebMenu(\[str value\])                                                                 |                                                                                                                                           |
| public str lookupCaption(\[str lan\])                                                                  |                                                                                                                                           |
| public str lookupLabel(str label, \[str lan\])                                                         |                                                                                                                                           |
| public int makeAutoSection(\[Query query\])                                                            |                                                                                                                                           |
| public str name(\[str value\])                                                                         | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public int orientation(\[int value\])                                                                  |                                                                                                                                           |
| public container pack()                                                                                | Serializes the current instance of the ReportDesign class.                                                                                |
| public container packPageSettings()                                                                    |                                                                                                                                           |
| public container packPrinterSettings()                                                                 |                                                                                                                                           |
| public container packPrintJobSettings()                                                                |                                                                                                                                           |
| public boolean pageFormatting()                                                                        |                                                                                                                                           |
| public PrinterOrientation paperOrientation(\[PrinterOrientation orientation\])                         |                                                                                                                                           |
| public int paperTray(\[int tray\])                                                                     |                                                                                                                                           |
| public int printerAttributes()                                                                         |                                                                                                                                           |
| public int printerAveragePPM()                                                                         |                                                                                                                                           |
| public str printerComment()                                                                            |                                                                                                                                           |
| public str printerDatatype()                                                                           |                                                                                                                                           |
| public int printerDefaultPriority()                                                                    |                                                                                                                                           |
| public str printerDriverName()                                                                         |                                                                                                                                           |
| public str printerLocation()                                                                           |                                                                                                                                           |
| public int printerPageHeight()                                                                         |                                                                                                                                           |
| public int printerPageWidth()                                                                          |                                                                                                                                           |
| public int printerPaper()                                                                              |                                                                                                                                           |
| public str printerParameters()                                                                         |                                                                                                                                           |
| public str printerPortName()                                                                           |                                                                                                                                           |
| public str printerPrinterName()                                                                        |                                                                                                                                           |
| public str printerPrintProcessor()                                                                     |                                                                                                                                           |
| public int printerPriority()                                                                           |                                                                                                                                           |
| public int printerQueuedJobs()                                                                         |                                                                                                                                           |
| public str printerSepFile()                                                                            |                                                                                                                                           |
| public str printerServerName()                                                                         |                                                                                                                                           |
| public boolean printerSettings(\[ReportRun reportRun\], \[int showWhat\])                              |                                                                                                                                           |
| public str printerShareName()                                                                          |                                                                                                                                           |
| public int printerStartTime()                                                                          |                                                                                                                                           |
| public int printerStatus()                                                                             |                                                                                                                                           |
| public int printerUntilTime()                                                                          |                                                                                                                                           |
| public str printFormName(\[str value\])                                                                |                                                                                                                                           |
| public PrintJobSettings printJobSettings()                                                             |                                                                                                                                           |
| public boolean removeRedundantFooters(\[boolean value\])                                               |                                                                                                                                           |
| public boolean removeRepeatedFooters(\[boolean value\])                                                |                                                                                                                                           |
| public boolean removeRepeatedHeaders(\[boolean value\])                                                |                                                                                                                                           |
| public str reportTemplate(\[str value\])                                                               |                                                                                                                                           |
| public str resolutionX(\[str value\])                                                                  |                                                                                                                                           |
| public int resolutionXStr(str value)                                                                   |                                                                                                                                           |
| public Units resolutionXUnit(\[Units value\])                                                          |                                                                                                                                           |
| public str resolutionY(\[str value\])                                                                  |                                                                                                                                           |
| public int resolutionYStr(str value)                                                                   |                                                                                                                                           |
| public Units resolutionYUnit(\[Units value\])                                                          |                                                                                                                                           |
| public int rightMarginMode(\[int value\])                                                              |                                                                                                                                           |
| public str rightMarginStr(\[str value\])                                                               |                                                                                                                                           |
| public Units rightMarginUnit(\[Units value\])                                                          |                                                                                                                                           |
| public Real rightMarginValue(\[Real value\])                                                           |                                                                                                                                           |
| public int ruler(\[int value\])                                                                        |                                                                                                                                           |
| public boolean saveDiskSettings(container buffer)                                                      |                                                                                                                                           |
| public ReportSection section(int number)                                                               | Finds a section below the generated design node.                                                                                          |
| public int sectionCount()                                                                              |                                                                                                                                           |
| public ReportSectionGroup sectionGroup(TableId tableId, \[FieldId fieldId\])                           | Finds a reportSectionGroup object below a reportDesign object.                                                                            |
| public ReportSection sectionName(str name)                                                             |                                                                                                                                           |
| public ReportSection sectionNumber(int number)                                                         |                                                                                                                                           |
| public PrintMedium setTarget(PrintMedium target)                                                       | Sets the print medium target for the report.                                                                                              |
| public int to(\[int toPage\])                                                                          |                                                                                                                                           |
| public int topMarginMode(\[int value\])                                                                |                                                                                                                                           |
| public str topMarginStr(\[str value\])                                                                 |                                                                                                                                           |
| public Units topMarginUnit(\[Units value\])                                                            |                                                                                                                                           |
| public Real topMarginValue(\[Real value\])                                                             |                                                                                                                                           |
| public str toString()                                                                                  | Returns a string that contains the class handle and name.                                                                                 |
| public boolean underline(\[boolean value\])                                                            |                                                                                                                                           |
| public boolean unpackPageSettings(container packedPageSetup)                                           |                                                                                                                                           |
| public boolean unpackPrinterSettings(container packedPrintSetup)                                       |                                                                                                                                           |
| public boolean unpackPrintJobSettings(container packedPrintJobSettings)                                |                                                                                                                                           |
| public void leftMargin(Real value, Units unit)                                                         |                                                                                                                                           |
| public void bottomMargin(Real value, Units unit)                                                       |                                                                                                                                           |
| public void rightMargin(Real value, Units unit)                                                        |                                                                                                                                           |
| public void topMargin(Real value, Units unit)                                                          |                                                                                                                                           |
| public void deleteDiskSettings(\[boolean allUsers\])                                                   |                                                                                                                                           |

### Method addProgrammableSection

    public ReportSection addProgrammableSection(int number)

#### Parameters

number  

#### Return Value

### Method addSection

Adds a report section to a design.

    public ReportSection addSection(ReportBlockType sectionType, [TableId tableId], [FieldId fieldId])

#### Parameters

sectionType  
If the sectionType parameter is set to Header, Body, or Footer, the dataField property of the section group that the section belongs to; optional.

<!-- -->

tableId  
If the sectionType parameter is set to Header, Body, or Footer, the dataField property of the section group that the section belongs to; optional.

<!-- -->

fieldId  
If the sectionType parameter is set to Header, Body, or Footer, the dataField property of the section group that the section belongs to; optional.

#### Return Value

The section that is created.

#### Remarks

This method creates a generated design if it does not already exist. If the sectionType parameter is set to Header, Body, or Footer, this method creates a section group if it does not already exist.

### Method addSectionGroup

Adds a section group to a design.

    public ReportSectionGroup addSectionGroup(TableId tableId, [FieldId fieldId])

#### Parameters

tableId  
The dataField property of the section group; optional.

<!-- -->

fieldId  
The dataField property of the section group; optional.

#### Return Value

The section group that is created.

#### Remarks

This method creates a generated design (if it does not already exist).

### Method arrange

    public int arrange()

#### Return Value

### Method arrangeWhen

    public int arrangeWhen([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method autoDesignSpecs

    public ReportAutoDesignSpecs autoDesignSpecs()

#### Return Value

### Method autoSection

    public ReportSection autoSection(TableId tableId, [int number])

#### Parameters

tableId  

<!-- -->

number  

#### Return Value

### Method autoSectionControlCount

    public int autoSectionControlCount()

#### Return Value

### Method autoSectionControlNumber

    public ReportControl autoSectionControlNumber(int number)

#### Parameters

number  

#### Return Value

### Method autoSectionCount

    public int autoSectionCount()

#### Return Value

### Method autoSectionNumber

    public ReportSection autoSectionNumber(int number)

#### Parameters

number  

#### Return Value

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method collate

    public boolean collate([boolean collate])

#### Parameters

collate  

#### Return Value

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

### Method control

Finds a control in the generated design, based on the control's table and dataField properties.

    public ReportControl control(TableId tableId, FieldId fieldId)

#### Parameters

tableId  
The dataField property of the control.

<!-- -->

fieldId  
The dataField property of the control.

#### Return Value

The control that is found.

#### Examples

    reportDesign rd = ...; 
    reportControl rc = rd.control(tablenum(CustGroup), 
        fieldnum(CustGroup, Name));

### Method controlCount

    public int controlCount()

#### Return Value

### Method controlName

Finds a control in the generated design, based on the control's Name property.

    public ReportControl controlName(str name)

#### Parameters

name  
The Name property of the control, expressed as a string.

#### Return Value

The control that is found.

### Method controlNumber

    public ReportControl controlNumber(int number)

#### Parameters

number  

#### Return Value

### Method copies

    public int copies([int numberOfCopies])

#### Parameters

numberOfCopies  

#### Return Value

### Method delete

Deletes the node from the AOT.

    public int delete()

#### Return Value

An integer.

### Method description

    public str description([str value])

#### Parameters

value  

#### Return Value

### Method deviceName

    public str deviceName([str device])

#### Parameters

device  

#### Return Value

### Method driverName

    public str driverName()

#### Return Value

### Method edit

    public boolean edit()

#### Return Value

### Method emptyReportPrompt

    public str emptyReportPrompt([str value])

#### Parameters

value  

#### Return Value

### Method fitToPage

    public int fitToPage([int value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method from

    public int from([int fromPage])

#### Parameters

fromPage  

#### Return Value

### Method generateDesign

    public int generateDesign()

#### Return Value

### Method getNumberOfPrinters

    public int getNumberOfPrinters()

#### Return Value

### Method getPrinter

    public str getPrinter(int number)

#### Parameters

number  

#### Return Value

### Method getTarget

Returns the print medium target for the report.

    public PrintMedium getTarget()

#### Return Value

The target for the report.

### Method hideBorder

    public boolean hideBorder([boolean value])

#### Parameters

value  

#### Return Value

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method jobType

    public str jobType([str value])

#### Parameters

value  

#### Return Value

### Method language

    public int language([int value])

#### Parameters

value  

#### Return Value

### Method languageID

    public str languageID([str lan])

#### Parameters

lan  

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method loadDiskSettings

    public container loadDiskSettings()

#### Return Value

### Method localWebMenu

    public str localWebMenu([str value])

#### Parameters

value  

#### Return Value

### Method lookupCaption

    public str lookupCaption([str lan])

#### Parameters

lan  

#### Return Value

### Method lookupLabel

    public str lookupLabel(str label, [str lan])

#### Parameters

label  

<!-- -->

lan  

#### Return Value

### Method makeAutoSection

    public int makeAutoSection([Query query])

#### Parameters

query  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method orientation

    public int orientation([int value])

#### Parameters

value  

#### Return Value

### Method pack

Serializes the current instance of the ReportDesign class.

    public container pack()

#### Return Value

A container that contains the current instance of the ReportDesign class.

### Method packPageSettings

    public container packPageSettings()

#### Return Value

### Method packPrinterSettings

    public container packPrinterSettings()

#### Return Value

### Method packPrintJobSettings

    public container packPrintJobSettings()

#### Return Value

### Method pageFormatting

    public boolean pageFormatting()

#### Return Value

### Method paperOrientation

    public PrinterOrientation paperOrientation([PrinterOrientation orientation])

#### Parameters

orientation  

#### Return Value

### Method paperTray

    public int paperTray([int tray])

#### Parameters

tray  

#### Return Value

### Method printerAttributes

    public int printerAttributes()

#### Return Value

### Method printerAveragePPM

    public int printerAveragePPM()

#### Return Value

### Method printerComment

    public str printerComment()

#### Return Value

### Method printerDatatype

    public str printerDatatype()

#### Return Value

### Method printerDefaultPriority

    public int printerDefaultPriority()

#### Return Value

### Method printerDriverName

    public str printerDriverName()

#### Return Value

### Method printerLocation

    public str printerLocation()

#### Return Value

### Method printerPageHeight

    public int printerPageHeight()

#### Return Value

### Method printerPageWidth

    public int printerPageWidth()

#### Return Value

### Method printerPaper

    public int printerPaper()

#### Return Value

### Method printerParameters

    public str printerParameters()

#### Return Value

### Method printerPortName

    public str printerPortName()

#### Return Value

### Method printerPrinterName

    public str printerPrinterName()

#### Return Value

### Method printerPrintProcessor

    public str printerPrintProcessor()

#### Return Value

### Method printerPriority

    public int printerPriority()

#### Return Value

### Method printerQueuedJobs

    public int printerQueuedJobs()

#### Return Value

### Method printerSepFile

    public str printerSepFile()

#### Return Value

### Method printerServerName

    public str printerServerName()

#### Return Value

### Method printerSettings

    public boolean printerSettings([ReportRun reportRun], [int showWhat])

#### Parameters

reportRun  

<!-- -->

showWhat  

#### Return Value

### Method printerShareName

    public str printerShareName()

#### Return Value

### Method printerStartTime

    public int printerStartTime()

#### Return Value

### Method printerStatus

    public int printerStatus()

#### Return Value

### Method printerUntilTime

    public int printerUntilTime()

#### Return Value

### Method printFormName

    public str printFormName([str value])

#### Parameters

value  

#### Return Value

### Method printJobSettings

    public PrintJobSettings printJobSettings()

#### Return Value

### Method removeRedundantFooters

    public boolean removeRedundantFooters([boolean value])

#### Parameters

value  

#### Return Value

### Method removeRepeatedFooters

    public boolean removeRepeatedFooters([boolean value])

#### Parameters

value  

#### Return Value

### Method removeRepeatedHeaders

    public boolean removeRepeatedHeaders([boolean value])

#### Parameters

value  

#### Return Value

### Method reportTemplate

    public str reportTemplate([str value])

#### Parameters

value  

#### Return Value

### Method resolutionX

    public str resolutionX([str value])

#### Parameters

value  

#### Return Value

### Method resolutionXStr

    public int resolutionXStr(str value)

#### Parameters

value  

#### Return Value

### Method resolutionXUnit

    public Units resolutionXUnit([Units value])

#### Parameters

value  

#### Return Value

### Method resolutionY

    public str resolutionY([str value])

#### Parameters

value  

#### Return Value

### Method resolutionYStr

    public int resolutionYStr(str value)

#### Parameters

value  

#### Return Value

### Method resolutionYUnit

    public Units resolutionYUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method ruler

    public int ruler([int value])

#### Parameters

value  

#### Return Value

### Method saveDiskSettings

    public boolean saveDiskSettings(container buffer)

#### Parameters

buffer  

#### Return Value

### Method section

Finds a section below the generated design node.

    public ReportSection section(int number)

#### Parameters

number  
The section number.

#### Return Value

The report section that is found.

### Method sectionCount

    public int sectionCount()

#### Return Value

### Method sectionGroup

Finds a reportSectionGroup object below a reportDesign object.

    public ReportSectionGroup sectionGroup(TableId tableId, [FieldId fieldId])

#### Parameters

tableId  
The field of the section group; optional.

<!-- -->

fieldId  
The field of the section group; optional.

#### Return Value

The section group that matches the arguments.

#### Examples

The following example finds the section group that is created by the addSection method:

    static void test(args a) 
    { 
        reportRun rr; 
        inventTrans rec; 
        int i; 
        int t = tablenum(inventTrans); 
        int f = fieldnum(inventTrans, datePhysical); 
        // Create a simple report that is not present in 
        // the Application Object Tree. 
        report r = new report(); 
        reportDesign rd = r.addDesign("myDesign"); 
        reportSectionGroup rsg; 
        reportSection rs = rd.AddSection(reportBlockType::body, t); 
        rs.addControl(t,f); 
        rsg = rd.SectionGroup(t); 
        if (rsg) 
        { 
            rs = rsg.AddSection(ReportBlockType::Header); 
            rs.AddTextControl("This is the groupHeader"); 
        } 
        // Run the report. 
        rr = new reportRun(r); 
        // Run the sysPrintForm form 
        if (rr.prompt()) 
        { 
            select rec; 
            rr.send(rec); 
            // Print the report to the target, such as printer or screen, that  
            // was selected during the prompt call above. 
            rr.print();  
        } 
    }

### Method sectionName

    public ReportSection sectionName(str name)

#### Parameters

name  

#### Return Value

### Method sectionNumber

    public ReportSection sectionNumber(int number)

#### Parameters

number  

#### Return Value

### Method setTarget

Sets the print medium target for the report.

    public PrintMedium setTarget(PrintMedium target)

#### Parameters

target  
The print medium for the report.

#### Return Value

The print medium for the report.

#### Remarks

To select a specific printer as the target for the report, call the PrintJobSettings.deviceName method on the object that is returned by the ReportDesign.printJobSettings method.

### Method to

    public int to([int toPage])

#### Parameters

toPage  

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method toString

Returns a string that contains the class handle and name.

    public str toString()

#### Return Value

A textual description of the class.

#### Remarks

In some classes, additional information is returned in the string.

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method unpackPageSettings

    public boolean unpackPageSettings(container packedPageSetup)

#### Parameters

packedPageSetup  

#### Return Value

### Method unpackPrinterSettings

    public boolean unpackPrinterSettings(container packedPrintSetup)

#### Parameters

packedPrintSetup  

#### Return Value

### Method unpackPrintJobSettings

    public boolean unpackPrintJobSettings(container packedPrintJobSettings)

#### Parameters

packedPrintJobSettings  

#### Return Value

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method deleteDiskSettings

    public void deleteDiskSettings([boolean allUsers])

#### Parameters

allUsers  

## Class ReportEnumControl
    class ReportEnumControl extends ReportControl

The ReportEnumControl class lets you to create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                   | Description                                                                                                                               |
|--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                           |
| public int arrayIndex(\[int value\])                                     |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public int backgroundColor(\[int value\])                                | Gets or sets the background color of the control.                                                                                         |
| public int backStyle(\[int value\])                                      | Determiness whether the control background can be transparent.                                                                            |
| public int bold(\[int value\])                                           | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int bottomMarginAndFrame()                                        |                                                                                                                                           |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                           |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                           |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                           |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                           |
| public int changeCase(\[int value\])                                     |                                                                                                                                           |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                           |
| public int characterSet(\[int value\])                                   | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                       |
| public ReportFieldType controlType()                                     |                                                                                                                                           |
| public str cssClass(\[str value\])                                       |                                                                                                                                           |
| public FieldId dataField(\[FieldId value\])                              |                                                                                                                                           |
| public str dataMethod(\[str value\])                                     |                                                                                                                                           |
| public int delete()                                                      |                                                                                                                                           |
| public str effectiveFont()                                               |                                                                                                                                           |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])         |                                                                                                                                           |
| public str font(\[str value\])                                           | Gets or sets the name of the font for the control to use.                                                                                 |
| public str fontInfoPrinter()                                             |                                                                                                                                           |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                           |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                           |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                           |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                           |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                           |
| public str fontInfoScreen()                                              |                                                                                                                                           |
| public int fontInfoScreenAscent()                                        |                                                                                                                                           |
| public int fontInfoScreenDescent()                                       |                                                                                                                                           |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                           |
| public int fontInfoScreenHeight()                                        |                                                                                                                                           |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                           |
| public int fontSize(\[int value\])                                       | Gets or sets the size of the font for the control to use.                                                                                 |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                                       |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                           |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                           |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                            |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                           |
| public str heightStr(\[str value\])                                      |                                                                                                                                           |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                           |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                                   |
| public boolean italic(\[boolean value\])                                 |                                                                                                                                           |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                     |
| public int labelBold(\[int value\])                                      |                                                                                                                                           |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                                           |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                           |
| public str labelFont(\[str value\])                                      |                                                                                                                                           |
| public int labelFontSize(\[int value\])                                  |                                                                                                                                           |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                                           |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                           |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                           |
| public int labelPosition(\[int value\])                                  |                                                                                                                                           |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                                           |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                                           |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                                           |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                                           |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                                           |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                                           |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                           |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                           |
| public int leftMarginAnFrame()                                           |                                                                                                                                           |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                           |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                           |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                           |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                           |
| public int leftMode(\[int value\])                                       |                                                                                                                                           |
| public str leftStr(\[str value\])                                        |                                                                                                                                           |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                           |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                           |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                               |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                           |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                           |
| public str menuItemName(\[str value\])                                   |                                                                                                                                           |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                           |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                           |
| public str name(\[str value\])                                           | Gets or sets the name that is used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object. |
| public int numberOfLines(int height100mm)                                |                                                                                                                                           |
| public int position(\[int value\])                                       |                                                                                                                                           |
| public str previewInfo(str string)                                       |                                                                                                                                           |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                           |
| public int right100mm()                                                  |                                                                                                                                           |
| public int right100mmInclBorder()                                        |                                                                                                                                           |
| public int rightMarginAndFrame()                                         |                                                                                                                                           |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                           |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                           |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                           |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                           |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                           |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                           |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                                           |
| public TableId table(\[TableId value\])                                  | Gets or sets the table ID associated with the object.                                                                                     |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                           |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                           |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                           |
| public int topMarginAndFrame()                                           |                                                                                                                                           |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                           |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                           |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                           |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                           |
| public int topMode(\[int value\])                                        |                                                                                                                                           |
| public str topStr(\[str value\])                                         |                                                                                                                                           |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                           |
| public Real topValue(\[Real value\])                                     |                                                                                                                                           |
| public boolean underline(\[boolean value\])                              |                                                                                                                                           |
| public boolean visible(\[boolean value\])                                |                                                                                                                                           |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                           |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                           |
| public str webTarget(\[str value\])                                      |                                                                                                                                           |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                           |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                           |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                            |
| public int widthOfString100mm(str string)                                |                                                                                                                                           |
| public str widthStr(\[str value\])                                       |                                                                                                                                           |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                           |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                                    |
| public void top(Real value, Units unit)                                  |                                                                                                                                           |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                           |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                                   |
| public void show()                                                       |                                                                                                                                           |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                                           |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                           |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                           |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                                    |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                           |
| public void left(Real value, Units unit)                                 |                                                                                                                                           |
| public void hide()                                                       |                                                                                                                                           |

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeCase

    public int changeCase([int value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelTabLeader

    public int labelTabLeader([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthStr

    public str labelWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method labelWidthUnit

    public Units labelWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public Real labelWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method show

    public void show()

### Method labelWidth

    public void labelWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method hide

    public void hide()

## Class ReportFieldGroup
    class ReportFieldGroup extends TreeNode

The ReportFieldGroup class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                        | Description                                                   |
|-----------------------------------------------|---------------------------------------------------------------|
| public int autoFieldGroupOrder(\[int value\]) |                                                               |
| public str dataGroup(\[str value\])           |                                                               |
| public int fieldCount()                       |                                                               |
| public ReportControl fieldNumber(int number)  |                                                               |
| public TableId table(\[TableId value\])       | Gets or sets the table ID that is associated with the object. |

### Method autoFieldGroupOrder

    public int autoFieldGroupOrder([int value])

#### Parameters

value  

#### Return Value

### Method dataGroup

    public str dataGroup([str value])

#### Parameters

value  

#### Return Value

### Method fieldCount

    public int fieldCount()

#### Return Value

### Method fieldNumber

    public ReportControl fieldNumber(int number)

#### Parameters

number  

#### Return Value

### Method table

Gets or sets the table ID that is associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID that is associated with the object.

## Class ReportGuidControl
    class ReportGuidControl extends ReportControl

The ReportGuidControl class enables you to create, read, update, and delete X++ code and metadata.

### Remarks

### Examples

### Methods

| Method                                                                   | Description                                                                                                                                   |
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                               |
| public int arrayIndex(\[int value\])                                     |                                                                                                                                               |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                            |
| public int backgroundColor(\[int value\])                                | Gets or sets the background color of the control.                                                                                             |
| public int backStyle(\[int value\])                                      | Determiness whether the control background can be transparent.                                                                                |
| public int bold(\[int value\])                                           | Gets or sets the weight of font that is used to output text in the control.                                                                   |
| public int bottomMarginAndFrame()                                        |                                                                                                                                               |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                               |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                               |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                               |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                               |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                               |
| public int characterSet(\[int value\])                                   | Gets or sets the character set of the font.                                                                                                   |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                                 |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                           |
| public ReportFieldType controlType()                                     |                                                                                                                                               |
| public str cssClass(\[str value\])                                       |                                                                                                                                               |
| public FieldId dataField(\[FieldId value\])                              |                                                                                                                                               |
| public str dataMethod(\[str value\])                                     |                                                                                                                                               |
| public int delete()                                                      |                                                                                                                                               |
| public str effectiveFont()                                               |                                                                                                                                               |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])         |                                                                                                                                               |
| public str font(\[str value\])                                           | Gets or sets the name of the font for the control to use.                                                                                     |
| public str fontInfoPrinter()                                             |                                                                                                                                               |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                               |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                               |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                               |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                               |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                               |
| public str fontInfoScreen()                                              |                                                                                                                                               |
| public int fontInfoScreenAscent()                                        |                                                                                                                                               |
| public int fontInfoScreenDescent()                                       |                                                                                                                                               |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                               |
| public int fontInfoScreenHeight()                                        |                                                                                                                                               |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                               |
| public int fontSize(\[int value\])                                       | Gets or sets the size of the font for the control to use.                                                                                     |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                                           |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                               |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                               |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                                |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                               |
| public str heightStr(\[str value\])                                      |                                                                                                                                               |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                               |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                                       |
| public boolean italic(\[boolean value\])                                 |                                                                                                                                               |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                         |
| public int labelBold(\[int value\])                                      |                                                                                                                                               |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                                               |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                               |
| public str labelFont(\[str value\])                                      |                                                                                                                                               |
| public int labelFontSize(\[int value\])                                  |                                                                                                                                               |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                                               |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                               |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                               |
| public int labelPosition(\[int value\])                                  |                                                                                                                                               |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                                               |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                                               |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                                               |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                                               |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                                               |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                                               |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                               |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                               |
| public int leftMarginAnFrame()                                           |                                                                                                                                               |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                               |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                               |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                               |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                               |
| public int leftMode(\[int value\])                                       |                                                                                                                                               |
| public str leftStr(\[str value\])                                        |                                                                                                                                               |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                               |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                               |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                               |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                               |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                                   |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                               |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                               |
| public str menuItemName(\[str value\])                                   |                                                                                                                                               |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                               |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                               |
| public str name(\[str value\])                                           | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public int numberOfLines(int height100mm)                                |                                                                                                                                               |
| public int position(\[int value\])                                       |                                                                                                                                               |
| public str previewInfo(str string)                                       |                                                                                                                                               |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                               |
| public int right100mm()                                                  |                                                                                                                                               |
| public int right100mmInclBorder()                                        |                                                                                                                                               |
| public int rightMarginAndFrame()                                         |                                                                                                                                               |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                               |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                               |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                               |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                               |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                               |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                               |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                                               |
| public TableId table(\[TableId value\])                                  | Gets or sets the table ID associated with the object.                                                                                         |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                               |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                               |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                               |
| public int topMarginAndFrame()                                           |                                                                                                                                               |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                               |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                               |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                               |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                               |
| public int topMode(\[int value\])                                        |                                                                                                                                               |
| public str topStr(\[str value\])                                         |                                                                                                                                               |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                               |
| public Real topValue(\[Real value\])                                     |                                                                                                                                               |
| public boolean underline(\[boolean value\])                              |                                                                                                                                               |
| public boolean visible(\[boolean value\])                                |                                                                                                                                               |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                               |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                               |
| public str webTarget(\[str value\])                                      |                                                                                                                                               |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                               |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                               |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                                |
| public int widthOfString100mm(str string)                                |                                                                                                                                               |
| public str widthStr(\[str value\])                                       |                                                                                                                                               |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                               |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                                        |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                                        |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                               |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                               |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                               |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                               |
| public void show()                                                       |                                                                                                                                               |
| public void hide()                                                       |                                                                                                                                               |
| public void top(Real value, Units unit)                                  |                                                                                                                                               |
| public void left(Real value, Units unit)                                 |                                                                                                                                               |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                                               |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                                       |

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of MicrosoftWindows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of MicrosoftWindows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                        |
|--------|-------------------------------|
| 0      | Default.                      |
| 1      | The MicrosoftWindows palette. |
| 2      | The true-color scheme.        |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelTabLeader

    public int labelTabLeader([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthStr

    public str labelWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method labelWidthUnit

    public Units labelWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public Real labelWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method show

    public void show()

### Method hide

    public void hide()

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method labelWidth

    public void labelWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

## Class ReportIntegerControl
    class ReportIntegerControl extends ReportControl

The ReportIntegerControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                   | Description                                                                                                                               |
|--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                           |
| public int allowNegative(\[int value\])                                  |                                                                                                                                           |
| public int arrayIndex(\[int value\])                                     |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public int backgroundColor(\[int value\])                                | Gets or sets the background color of the control.                                                                                         |
| public int backStyle(\[int value\])                                      | Determiness whether the control background can be transparent.                                                                            |
| public int bold(\[int value\])                                           | Gets or sets the weight of font that was used to output text in the control.                                                              |
| public int bottomMarginAndFrame()                                        |                                                                                                                                           |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                           |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                           |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                           |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                           |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                           |
| public int characterSet(\[int value\])                                   | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                       |
| public ReportFieldType controlType()                                     |                                                                                                                                           |
| public str cssClass(\[str value\])                                       |                                                                                                                                           |
| public FieldId dataField(\[FieldId value\])                              |                                                                                                                                           |
| public str dataMethod(\[str value\])                                     |                                                                                                                                           |
| public int delete()                                                      |                                                                                                                                           |
| public int displaceNegative(\[int value\], \[AutoMode mode\])            |                                                                                                                                           |
| public AutoMode displaceNegativeMode(\[AutoMode mode\])                  |                                                                                                                                           |
| public int displaceNegativeValue(\[int value\])                          |                                                                                                                                           |
| public str effectiveFont()                                               |                                                                                                                                           |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])         |                                                                                                                                           |
| public int extraSumWidthMode(\[int value\])                              |                                                                                                                                           |
| public str extraSumWidthStr(\[str value\])                               |                                                                                                                                           |
| public Units extraSumWidthUnit(\[Units value\])                          |                                                                                                                                           |
| public Real extraSumWidthValue(\[Real value\])                           |                                                                                                                                           |
| public str font(\[str value\])                                           | Gets or sets the name of the font for the control to use.                                                                                 |
| public str fontInfoPrinter()                                             |                                                                                                                                           |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                           |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                           |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                           |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                           |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                           |
| public str fontInfoScreen()                                              |                                                                                                                                           |
| public int fontInfoScreenAscent()                                        |                                                                                                                                           |
| public int fontInfoScreenDescent()                                       |                                                                                                                                           |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                           |
| public int fontInfoScreenHeight()                                        |                                                                                                                                           |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                           |
| public int fontSize(\[int value\])                                       | Gets or sets the size of the font for the control to use.                                                                                 |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                                       |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                           |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                           |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                            |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                           |
| public str heightStr(\[str value\])                                      |                                                                                                                                           |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                           |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                                   |
| public boolean italic(\[boolean value\])                                 |                                                                                                                                           |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                     |
| public int labelBold(\[int value\])                                      |                                                                                                                                           |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                                           |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                           |
| public str labelFont(\[str value\])                                      |                                                                                                                                           |
| public int labelFontSize(\[int value\])                                  |                                                                                                                                           |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                                           |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                           |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                           |
| public int labelPosition(\[int value\])                                  |                                                                                                                                           |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                                           |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                                           |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                                           |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                                           |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                                           |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                                           |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                           |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                           |
| public int leftMarginAnFrame()                                           |                                                                                                                                           |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                           |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                           |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                           |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                           |
| public int leftMode(\[int value\])                                       |                                                                                                                                           |
| public str leftStr(\[str value\])                                        |                                                                                                                                           |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                           |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                           |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                               |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                           |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                           |
| public str menuItemName(\[str value\])                                   |                                                                                                                                           |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                           |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                           |
| public str name(\[str value\])                                           | Gets or sets the name that is used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object. |
| public int numberOfLines(int height100mm)                                |                                                                                                                                           |
| public int position(\[int value\])                                       |                                                                                                                                           |
| public str previewInfo(str string)                                       |                                                                                                                                           |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                           |
| public int right100mm()                                                  |                                                                                                                                           |
| public int right100mmInclBorder()                                        |                                                                                                                                           |
| public int rightMarginAndFrame()                                         |                                                                                                                                           |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                           |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                           |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                           |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                           |
| public int rotateSign(\[int value\])                                     |                                                                                                                                           |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                           |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                           |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                                           |
| public int showZero(\[int value\])                                       |                                                                                                                                           |
| public int signDisplay(\[int value\])                                    |                                                                                                                                           |
| public boolean sumAll(\[boolean value\])                                 |                                                                                                                                           |
| public boolean sumNeg(\[boolean value\])                                 |                                                                                                                                           |
| public boolean sumPos(\[boolean value\])                                 |                                                                                                                                           |
| public TableId table(\[TableId value\])                                  | Gets or sets the table ID associated with the object.                                                                                     |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                           |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                           |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                           |
| public int topMarginAndFrame()                                           |                                                                                                                                           |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                           |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                           |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                           |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                           |
| public int topMode(\[int value\])                                        |                                                                                                                                           |
| public str topStr(\[str value\])                                         |                                                                                                                                           |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                           |
| public Real topValue(\[Real value\])                                     |                                                                                                                                           |
| public boolean underline(\[boolean value\])                              |                                                                                                                                           |
| public boolean visible(\[boolean value\])                                |                                                                                                                                           |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                           |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                           |
| public str webTarget(\[str value\])                                      |                                                                                                                                           |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                           |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                           |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                            |
| public int widthOfString100mm(str string)                                |                                                                                                                                           |
| public str widthStr(\[str value\])                                       |                                                                                                                                           |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                           |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                                    |
| public void show()                                                       |                                                                                                                                           |
| public void left(Real value, Units unit)                                 |                                                                                                                                           |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                                    |
| public void extraSumWidth(Real value, Units unit)                        |                                                                                                                                           |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                           |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                           |
| public void hide()                                                       |                                                                                                                                           |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                           |
| public void top(Real value, Units unit)                                  |                                                                                                                                           |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                                           |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                           |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                                   |

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method allowNegative

    public int allowNegative([int value])

#### Parameters

value  

#### Return Value

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that was used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method displaceNegative

    public int displaceNegative([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displaceNegativeMode

    public AutoMode displaceNegativeMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displaceNegativeValue

    public int displaceNegativeValue([int value])

#### Parameters

value  

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method extraSumWidthMode

    public int extraSumWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method extraSumWidthStr

    public str extraSumWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method extraSumWidthUnit

    public Units extraSumWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method extraSumWidthValue

    public Real extraSumWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelTabLeader

    public int labelTabLeader([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthStr

    public str labelWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method labelWidthUnit

    public Units labelWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public Real labelWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method rotateSign

    public int rotateSign([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method showZero

    public int showZero([int value])

#### Parameters

value  

#### Return Value

### Method signDisplay

    public int signDisplay([int value])

#### Parameters

value  

#### Return Value

### Method sumAll

    public boolean sumAll([boolean value])

#### Parameters

value  

#### Return Value

### Method sumNeg

    public boolean sumNeg([boolean value])

#### Parameters

value  

#### Return Value

### Method sumPos

    public boolean sumPos([boolean value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method show

    public void show()

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method extraSumWidth

    public void extraSumWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method hide

    public void hide()

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method labelWidth

    public void labelWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

## Class ReportLibraryNode
    class ReportLibraryNode extends xresourceNode

### Remarks

### Examples

### Methods

| Method                                       | Description                                                                                                                               |
|----------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str changedBy(\[str value\])          | Gets or sets the name of the user who last changed the application object.                                                                |
| public Date changedDate(\[Date value\])      | Gets or sets the date an application object was last changed.                                                                             |
| public str changedTime(\[str value\])        | Gets or sets the time an application object was last changed.                                                                             |
| public str createdBy(\[str value\])          | Gets or sets the name of the user who created the application object.                                                                     |
| public Date creationDate(\[Date value\])     | Gets or sets the date an application object was created.                                                                                  |
| public str creationTime(\[str value\])       |                                                                                                                                           |
| public str designs(\[str value\])            |                                                                                                                                           |
| public str name(\[str value\])               | Gets or sets the name that is used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])           |                                                                                                                                           |
| public str projectGuid(\[str value\])        |                                                                                                                                           |
| public str referencedProjects(\[str value\]) |                                                                                                                                           |

### Method changedBy

Gets or sets the name of the user who last changed the application object.

    public str changedBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method changedDate

Gets or sets the date an application object was last changed.

    public Date changedDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was last changed.

### Method changedTime

Gets or sets the time an application object was last changed.

    public str changedTime([str value])

#### Parameters

value  

#### Return Value

The time an application object was last changed.

### Method createdBy

Gets or sets the name of the user who created the application object.

    public str createdBy([str value])

#### Parameters

value  

#### Return Value

The name of the user.

### Method creationDate

Gets or sets the date an application object was created.

    public Date creationDate([Date value])

#### Parameters

value  

#### Return Value

The date an application object was created.

### Method creationTime

    public str creationTime([str value])

#### Parameters

value  

#### Return Value

### Method designs

    public str designs([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method projectGuid

    public str projectGuid([str value])

#### Parameters

value  

#### Return Value

### Method referencedProjects

    public str referencedProjects([str value])

#### Parameters

value  

#### Return Value

## Class ReportOutput
    class ReportOutput extends Object

The ReportOutput class handles the output of a report to a printer or file.

### Remarks

This class serves as the base class for the ReportViewer class, which handles preview of reports, and for the ReportOutputUser class, which handles output of reports to a user-defined target in a user-defined format. In general, if a report is printed to the printer, the print method creates a ReportOutput object and calls its print method. If the call printJobSettings::outputToClient(TRUE) has been made, a ReportViewer object is created instead. The call to the print method prints the report on a printer that is set up on the client, because a ReportViewer object can only exist on the client, not on the server.

### Examples

The following example prints the job descriptions and page numbers of jobs that have been inserted into the printArchive table on the current date, and prints page 1 on the default printer.

    static void aaaReportOutputExample(args a) 
    { 
        printJobHeader printJobHeader; 
        printJobPages printJobPages; 
        int myrecId; 
        reportViewer reportViewer; 
        while select printJobHeader where printJobHeader.createdDateTime >=
            str2datetime("01/01/2011 12:00:00", 123) 
        { 
            myrecId = printJobHeader.recId; 
            print printJobHeader.jobDescription; 
            while select printJobPages  
                where printJobPages.pagesHeaderRecId == myRecId 
            print printJobPages.PageNo; 
            reportViewer = new reportOutput(printJobHeader); 
            reportViewer.print(); 
        } 
    }

### Methods

| Method                                                                    | Description                                     |
|---------------------------------------------------------------------------|-------------------------------------------------|
| public str description(\[str description\])                               |                                                 |
| public int getCopyNo()                                                    |                                                 |
| public boolean getDeclineOverwrite()                                      |                                                 |
| public int getLastCopyNo()                                                |                                                 |
| public int getLastPageNo()                                                |                                                 |
| public int getPageNo()                                                    |                                                 |
| public str getTempFileName(str prefix)                                    |                                                 |
| public PrintJobStatus jobStatus()                                         |                                                 |
| public PrintJobSettings printJobSettings()                                |                                                 |
| public boolean setNumberOfPages(int pageNo)                               |                                                 |
| public str type(\[str type\])                                             |                                                 |
| public void new(PrintJobHeader jobsCursor, \[PrintJobPages pagesCursor\]) | Initializes a new instance of the Object class. |
| public void printAscii(str filename)                                      |                                                 |
| public void printTextUTF8(str filename)                                   | Prints a report to a UTF-8 format.              |
| public void printRTF(str filename)                                        |                                                 |
| public void print()                                                       |                                                 |
| public void printPDF(str filename, \[boolean embedFonts\])                |                                                 |
| public void printHTML(str filename)                                       |                                                 |
| public void abort()                                                       |                                                 |
| public void dialogAndPrint()                                              |                                                 |
| public void printToTarget()                                               |                                                 |

### Method description

    public str description([str description])

#### Parameters

description  

#### Return Value

### Method getCopyNo

    public int getCopyNo()

#### Return Value

### Method getDeclineOverwrite

    public boolean getDeclineOverwrite()

#### Return Value

### Method getLastCopyNo

    public int getLastCopyNo()

#### Return Value

### Method getLastPageNo

    public int getLastPageNo()

#### Return Value

### Method getPageNo

    public int getPageNo()

#### Return Value

### Method getTempFileName

    public str getTempFileName(str prefix)

#### Parameters

prefix  

#### Return Value

### Method jobStatus

    public PrintJobStatus jobStatus()

#### Return Value

### Method printJobSettings

    public PrintJobSettings printJobSettings()

#### Return Value

### Method setNumberOfPages

    public boolean setNumberOfPages(int pageNo)

#### Parameters

pageNo  

#### Return Value

### Method type

    public str type([str type])

#### Parameters

type  

#### Return Value

### Method new

Initializes a new instance of the Object class.

    public void new(PrintJobHeader jobsCursor, [PrintJobPages pagesCursor])

#### Parameters

jobsCursor  

<!-- -->

pagesCursor  

### Method printAscii

    public void printAscii(str filename)

#### Parameters

filename  

### Method printTextUTF8

Prints a report to a UTF-8 format.

    public void printTextUTF8(str filename)

#### Parameters

filename  
A string that specifies the name of the file that the report is printed to.

#### Remarks

UTF-8 is a method of character encoding that allows for both single and multibyte characters in one string.

#### Examples

The following example shows a call to the printTextUTF8 method.

    void printTextUTF8() 
    { 
        ReportOutput reportOutput; 
        printJobHeader printJobHeader; 
        while select printJobHeader where printJobHeader.createdDateTime >= 
            str2datetime("01/01/2011 12:00:00", 123)
        { 
            print printJobHeader.jobDescription; 
            reportOutput = new ReportOutput(printJobHeader); 
            reportOutput.printTextUTF8("c:\\report.txt"); 
        } 
    }

### Method printRTF

    public void printRTF(str filename)

#### Parameters

filename  

### Method print

    public void print()

### Method printPDF

    public void printPDF(str filename, [boolean embedFonts])

#### Parameters

filename  

<!-- -->

embedFonts  

### Method printHTML

    public void printHTML(str filename)

#### Parameters

filename  

### Method abort

    public void abort()

### Method dialogAndPrint

    public void dialogAndPrint()

### Method printToTarget

    public void printToTarget()

## Class ReportOutputUser
    class ReportOutputUser extends ReportOutput

The ReportOutputUser class implements a user-defined target for report formatting.

### Remarks

By default, Microsoft Dynamics AX prints reports to a screen, printer, file, or email address. The following API items support a user-defined target:

-   ReportOutputUserType system enumeration
-   ViewerClass value for the PrintMedium system enumeration
-   ClassFactory::createViewer method

When a report is run, the print method creates a reportOutputUser object if the target is PrintMedium::Viewer class. This object will be created by calling the createViewer method and giving reportOutputUserType as one of the arguments. The report will then be printed by calling methods on the object: startReport, startPage, startSection, writeField, and so on. In general, if the target is, for example, a printer, the reportRun::print method will create a reportOutput object and call its print method to print the report to a printer. If the target is viewerClass, it will instead call the createViewer method to get a ReportOutputUser object. Then it will call methods on the object: startReport, startPage, startSection, startField, outputStringField, and so on. When the report is run, the Text property of the text controls of the report will be written to the print window.

### Examples

### Methods

| Method                                                                                            | Description                                     |
|---------------------------------------------------------------------------------------------------|-------------------------------------------------|
| public boolean pageCreated(int page)                                                              |                                                 |
| public str result()                                                                               |                                                 |
| public void writeAutoLabel(OutputAutoLabelField field, OuputSection section)                      |                                                 |
| public void endHeaderSection(OutputHeaderSection section)                                         |                                                 |
| public void writeString(OutputStringField field, OuputSection section)                            |                                                 |
| public void endPageHeaderSection(OutputPageHeaderSection section)                                 |                                                 |
| public void writeBitmap(OutputBitmapField field, OuputSection section)                            |                                                 |
| public void endBodySection(OutputBodySection section)                                             |                                                 |
| public void startPageHeaderSection(OutputPageHeaderSection section)                               |                                                 |
| public void printViaClass()                                                                       |                                                 |
| public void endPageFooterSection(OutputPageFooterSection section)                                 |                                                 |
| public void writeReal(OutputRealField field, OuputSection section)                                |                                                 |
| public void startColumnHeadingsSection(OutputColumnHeadingsSection section)                       |                                                 |
| public void writeShape(OutputShapeField field, OuputSection section)                              |                                                 |
| public void writeDateTime(OutputDateTimeField field, OuputSection section)                        |                                                 |
| public void writeStaticText(OutputStaticTextField field, OuputSection section)                    |                                                 |
| public void new(PrintJobHeader jobsCursor, \[PrintJobPages pagesCursor\], \[container settings\]) | Initializes a new instance of the Object class. |
| public void writeInteger(OutputIntegerField field, OuputSection section)                          |                                                 |
| public void startColumnSection()                                                                  |                                                 |
| public void startSection(OuputSection section)                                                    |                                                 |
| public void writeDate(OutputDateField field, OuputSection section)                                |                                                 |
| public void pagesTotal(int pagesTotal)                                                            |                                                 |
| public void writeInt64(OutputInt64Field field, OuputSection section)                              |                                                 |
| public void endReport(PrintJobStatus printJobStatus)                                              |                                                 |
| public void endColumnSection()                                                                    |                                                 |
| public void startReport(PrintJobSettings printJobSettings)                                        |                                                 |
| public void printPageViaClass(int page)                                                           |                                                 |
| public void endEpilogSection(OutputEpilogSection section)                                         |                                                 |
| public void endPrologSection(OutputPrologSection section)                                         |                                                 |
| public void endPage()                                                                             |                                                 |
| public void startFooterSection(OutputFooterSection section)                                       |                                                 |
| public void endProgrammableSection(OutputProgrammableSection section)                             |                                                 |
| public void startBodySection(OutputBodySection section)                                           |                                                 |
| public void endSection(OuputSection section)                                                      |                                                 |
| public void startProgrammableSection(OutputProgrammableSection section)                           |                                                 |
| public void startEpilogSection(OutputEpilogSection section)                                       |                                                 |
| public void startHeaderSection(OutputHeaderSection section)                                       |                                                 |
| public void endColumnHeadingsSection(OutputColumnHeadingsSection section)                         |                                                 |
| public void writeLabel(OutputLabelField field, OuputSection section)                              |                                                 |
| public void endFooterSection(OutputFooterSection section)                                         |                                                 |
| public void writeField(OutputField field, OuputSection section)                                   |                                                 |
| public void writeEnum(OutputEnumField field, OuputSection section)                                |                                                 |
| public void startPageFooterSection(OutputPageFooterSection section)                               |                                                 |
| public void writeSum(OutputSumField field, OuputSection section)                                  |                                                 |
| public void writeTime(OutputTimeField field, OuputSection section)                                |                                                 |
| public void startPage(OutputPage page)                                                            |                                                 |
| public void startPrologSection(OutputPrologSection section)                                       |                                                 |

### Method pageCreated

    public boolean pageCreated(int page)

#### Parameters

page  

#### Return Value

### Method result

    public str result()

#### Return Value

### Method writeAutoLabel

    public void writeAutoLabel(OutputAutoLabelField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method endHeaderSection

    public void endHeaderSection(OutputHeaderSection section)

#### Parameters

section  

### Method writeString

    public void writeString(OutputStringField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method endPageHeaderSection

    public void endPageHeaderSection(OutputPageHeaderSection section)

#### Parameters

section  

### Method writeBitmap

    public void writeBitmap(OutputBitmapField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method endBodySection

    public void endBodySection(OutputBodySection section)

#### Parameters

section  

### Method startPageHeaderSection

    public void startPageHeaderSection(OutputPageHeaderSection section)

#### Parameters

section  

### Method printViaClass

    public void printViaClass()

### Method endPageFooterSection

    public void endPageFooterSection(OutputPageFooterSection section)

#### Parameters

section  

### Method writeReal

    public void writeReal(OutputRealField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method startColumnHeadingsSection

    public void startColumnHeadingsSection(OutputColumnHeadingsSection section)

#### Parameters

section  

### Method writeShape

    public void writeShape(OutputShapeField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method writeDateTime

    public void writeDateTime(OutputDateTimeField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method writeStaticText

    public void writeStaticText(OutputStaticTextField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method new

Initializes a new instance of the Object class.

    public void new(PrintJobHeader jobsCursor, [PrintJobPages pagesCursor], [container settings])

#### Parameters

jobsCursor  

<!-- -->

pagesCursor  

<!-- -->

settings  

### Method writeInteger

    public void writeInteger(OutputIntegerField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method startColumnSection

    public void startColumnSection()

### Method startSection

    public void startSection(OuputSection section)

#### Parameters

section  

### Method writeDate

    public void writeDate(OutputDateField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method pagesTotal

    public void pagesTotal(int pagesTotal)

#### Parameters

pagesTotal  

### Method writeInt64

    public void writeInt64(OutputInt64Field field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method endReport

    public void endReport(PrintJobStatus printJobStatus)

#### Parameters

printJobStatus  

### Method endColumnSection

    public void endColumnSection()

### Method startReport

    public void startReport(PrintJobSettings printJobSettings)

#### Parameters

printJobSettings  

### Method printPageViaClass

    public void printPageViaClass(int page)

#### Parameters

page  

### Method endEpilogSection

    public void endEpilogSection(OutputEpilogSection section)

#### Parameters

section  

### Method endPrologSection

    public void endPrologSection(OutputPrologSection section)

#### Parameters

section  

### Method endPage

    public void endPage()

### Method startFooterSection

    public void startFooterSection(OutputFooterSection section)

#### Parameters

section  

### Method endProgrammableSection

    public void endProgrammableSection(OutputProgrammableSection section)

#### Parameters

section  

### Method startBodySection

    public void startBodySection(OutputBodySection section)

#### Parameters

section  

### Method endSection

    public void endSection(OuputSection section)

#### Parameters

section  

### Method startProgrammableSection

    public void startProgrammableSection(OutputProgrammableSection section)

#### Parameters

section  

### Method startEpilogSection

    public void startEpilogSection(OutputEpilogSection section)

#### Parameters

section  

### Method startHeaderSection

    public void startHeaderSection(OutputHeaderSection section)

#### Parameters

section  

### Method endColumnHeadingsSection

    public void endColumnHeadingsSection(OutputColumnHeadingsSection section)

#### Parameters

section  

### Method writeLabel

    public void writeLabel(OutputLabelField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method endFooterSection

    public void endFooterSection(OutputFooterSection section)

#### Parameters

section  

### Method writeField

    public void writeField(OutputField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method writeEnum

    public void writeEnum(OutputEnumField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method startPageFooterSection

    public void startPageFooterSection(OutputPageFooterSection section)

#### Parameters

section  

### Method writeSum

    public void writeSum(OutputSumField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method writeTime

    public void writeTime(OutputTimeField field, OuputSection section)

#### Parameters

field  

<!-- -->

section  

### Method startPage

    public void startPage(OutputPage page)

#### Parameters

page  

### Method startPrologSection

    public void startPrologSection(OutputPrologSection section)

#### Parameters

section  

## Class ReportPrinter
    class ReportPrinter extends ReportOutput

### Remarks

### Examples

### Methods

| Method | Description |
|--------|-------------|

## Class ReportPromptControl
    class ReportPromptControl extends ReportControl

The ReportPromptControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                   | Description                                                                                                                               |
|--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                           |
| public int arrayIndex(\[int value\])                                     |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public int backgroundColor(\[int value\])                                | Gets or sets the background color of the control.                                                                                         |
| public int backStyle(\[int value\])                                      | Determiness whether the control background can be transparent.                                                                            |
| public int bold(\[int value\])                                           | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int bottomMarginAndFrame()                                        |                                                                                                                                           |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                           |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                           |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                           |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                           |
| public int changeCase(\[int value\])                                     |                                                                                                                                           |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                           |
| public int characterSet(\[int value\])                                   | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                       |
| public ReportFieldType controlType()                                     |                                                                                                                                           |
| public str cssClass(\[str value\])                                       |                                                                                                                                           |
| public FieldId dataField(\[FieldId value\])                              |                                                                                                                                           |
| public int delete()                                                      |                                                                                                                                           |
| public str effectiveFont()                                               |                                                                                                                                           |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])         |                                                                                                                                           |
| public str font(\[str value\])                                           | Gets or sets the name of the font for the control to use.                                                                                 |
| public str fontInfoPrinter()                                             |                                                                                                                                           |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                           |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                           |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                           |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                           |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                           |
| public str fontInfoScreen()                                              |                                                                                                                                           |
| public int fontInfoScreenAscent()                                        |                                                                                                                                           |
| public int fontInfoScreenDescent()                                       |                                                                                                                                           |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                           |
| public int fontInfoScreenHeight()                                        |                                                                                                                                           |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                           |
| public int fontSize(\[int value\])                                       | Gets or sets the size of the font for the control to use.                                                                                 |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                                       |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                           |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                           |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                            |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                           |
| public str heightStr(\[str value\])                                      |                                                                                                                                           |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                           |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                                   |
| public boolean italic(\[boolean value\])                                 |                                                                                                                                           |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                     |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                           |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                           |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                           |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                           |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                           |
| public int leftMarginAnFrame()                                           |                                                                                                                                           |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                           |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                           |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                           |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                           |
| public int leftMode(\[int value\])                                       |                                                                                                                                           |
| public str leftStr(\[str value\])                                        |                                                                                                                                           |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                           |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                           |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                               |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                           |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                           |
| public str menuItemName(\[str value\])                                   |                                                                                                                                           |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                           |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                           |
| public str name(\[str value\])                                           | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public int numberOfLines(int height100mm)                                |                                                                                                                                           |
| public int position(\[int value\])                                       |                                                                                                                                           |
| public str previewInfo(str string)                                       |                                                                                                                                           |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                           |
| public int right100mm()                                                  |                                                                                                                                           |
| public int right100mmInclBorder()                                        |                                                                                                                                           |
| public int rightMarginAndFrame()                                         |                                                                                                                                           |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                           |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                           |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                           |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                           |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                           |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                           |
| public TableId table(\[TableId value\])                                  | Gets or sets the table ID associated with the object.                                                                                     |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                           |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                           |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                           |
| public int topMarginAndFrame()                                           |                                                                                                                                           |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                           |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                           |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                           |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                           |
| public int topMode(\[int value\])                                        |                                                                                                                                           |
| public str topStr(\[str value\])                                         |                                                                                                                                           |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                           |
| public Real topValue(\[Real value\])                                     |                                                                                                                                           |
| public int typeHeaderPrompt(\[int value\])                               |                                                                                                                                           |
| public boolean underline(\[boolean value\])                              |                                                                                                                                           |
| public boolean visible(\[boolean value\])                                |                                                                                                                                           |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                           |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                           |
| public str webTarget(\[str value\])                                      |                                                                                                                                           |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                           |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                           |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                            |
| public int widthOfString100mm(str string)                                |                                                                                                                                           |
| public str widthStr(\[str value\])                                       |                                                                                                                                           |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                           |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                                    |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                                    |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                           |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                           |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                           |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                           |
| public void top(Real value, Units unit)                                  |                                                                                                                                           |
| public void left(Real value, Units unit)                                 |                                                                                                                                           |
| public void show()                                                       |                                                                                                                                           |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                                   |
| public void hide()                                                       |                                                                                                                                           |

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeCase

    public int changeCase([int value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value that is based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method typeHeaderPrompt

    public int typeHeaderPrompt([int value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method show

    public void show()

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method hide

    public void hide()

## Class ReportRealControl
    class ReportRealControl extends ReportControl

The ReportRealControl class enables you to create, read, update, and delete X++ code and metadata.

### Remarks

### Examples

### Methods

| Method                                                                   | Description                                                                                                                                   |
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                               |
| public int allowNegative(\[int value\])                                  |                                                                                                                                               |
| public int arrayIndex(\[int value\])                                     |                                                                                                                                               |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                            |
| public int autoInsSeparator(\[int value\])                               |                                                                                                                                               |
| public int backgroundColor(\[int value\])                                | Gets or sets the background color of the control.                                                                                             |
| public int backStyle(\[int value\])                                      | Determiness whether the control background can be transparent.                                                                                |
| public int bold(\[int value\])                                           | Gets or sets the weight of font that is used to output text in the control.                                                                   |
| public int bottomMarginAndFrame()                                        |                                                                                                                                               |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                               |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                               |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                               |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                               |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                               |
| public int characterSet(\[int value\])                                   | Gets or sets the character set of the font.                                                                                                   |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                                 |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                           |
| public ReportFieldType controlType()                                     |                                                                                                                                               |
| public str cssClass(\[str value\])                                       |                                                                                                                                               |
| public FieldId dataField(\[FieldId value\])                              |                                                                                                                                               |
| public str dataMethod(\[str value\])                                     |                                                                                                                                               |
| public int decimalSeparator(\[int value\])                               |                                                                                                                                               |
| public int delete()                                                      |                                                                                                                                               |
| public int displaceNegative(\[int value\], \[AutoMode mode\])            |                                                                                                                                               |
| public AutoMode displaceNegativeMode(\[AutoMode mode\])                  |                                                                                                                                               |
| public int displaceNegativeValue(\[int value\])                          |                                                                                                                                               |
| public str effectiveFont()                                               |                                                                                                                                               |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])         |                                                                                                                                               |
| public int extraSumWidthMode(\[int value\])                              |                                                                                                                                               |
| public str extraSumWidthStr(\[str value\])                               |                                                                                                                                               |
| public Units extraSumWidthUnit(\[Units value\])                          |                                                                                                                                               |
| public Real extraSumWidthValue(\[Real value\])                           |                                                                                                                                               |
| public str font(\[str value\])                                           | Gets or sets the name of the font for the control to use.                                                                                     |
| public str fontInfoPrinter()                                             |                                                                                                                                               |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                               |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                               |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                               |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                               |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                               |
| public str fontInfoScreen()                                              |                                                                                                                                               |
| public int fontInfoScreenAscent()                                        |                                                                                                                                               |
| public int fontInfoScreenDescent()                                       |                                                                                                                                               |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                               |
| public int fontInfoScreenHeight()                                        |                                                                                                                                               |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                               |
| public int fontSize(\[int value\])                                       | Gets or sets the size of the font for the control to use.                                                                                     |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                                           |
| public int formatMST(\[int value\])                                      |                                                                                                                                               |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                               |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                               |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                                |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                               |
| public str heightStr(\[str value\])                                      |                                                                                                                                               |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                               |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                                       |
| public boolean italic(\[boolean value\])                                 |                                                                                                                                               |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                         |
| public int labelBold(\[int value\])                                      |                                                                                                                                               |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                                               |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                               |
| public str labelFont(\[str value\])                                      |                                                                                                                                               |
| public int labelFontSize(\[int value\])                                  |                                                                                                                                               |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                                               |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                               |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                               |
| public int labelPosition(\[int value\])                                  |                                                                                                                                               |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                                               |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                                               |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                                               |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                                               |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                                               |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                                               |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                               |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                               |
| public int leftMarginAnFrame()                                           |                                                                                                                                               |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                               |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                               |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                               |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                               |
| public int leftMode(\[int value\])                                       |                                                                                                                                               |
| public str leftStr(\[str value\])                                        |                                                                                                                                               |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                               |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                               |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                               |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                               |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                                   |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                               |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                               |
| public str menuItemName(\[str value\])                                   |                                                                                                                                               |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                               |
| public int minNoOfDecimals(\[int value\], \[AutoMode mode\])             |                                                                                                                                               |
| public AutoMode minNoOfDecimalsMode(\[AutoMode mode\])                   |                                                                                                                                               |
| public int minNoOfDecimalsValue(\[int value\])                           |                                                                                                                                               |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                               |
| public str name(\[str value\])                                           | Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public int noOfDecimals(\[int value\], \[AutoMode mode\])                |                                                                                                                                               |
| public AutoMode noOfDecimalsMode(\[AutoMode mode\])                      |                                                                                                                                               |
| public int noOfDecimalsValue(\[int value\])                              |                                                                                                                                               |
| public int numberOfLines(int height100mm)                                |                                                                                                                                               |
| public int position(\[int value\])                                       |                                                                                                                                               |
| public str previewInfo(str string)                                       |                                                                                                                                               |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                               |
| public int right100mm()                                                  |                                                                                                                                               |
| public int right100mmInclBorder()                                        |                                                                                                                                               |
| public int rightMarginAndFrame()                                         |                                                                                                                                               |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                               |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                               |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                               |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                               |
| public int rotateSign(\[int value\])                                     |                                                                                                                                               |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                               |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                               |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                                               |
| public int showZero(\[int value\])                                       |                                                                                                                                               |
| public int signDisplay(\[int value\])                                    |                                                                                                                                               |
| public boolean sumAll(\[boolean value\])                                 |                                                                                                                                               |
| public boolean sumNeg(\[boolean value\])                                 |                                                                                                                                               |
| public boolean sumPos(\[boolean value\])                                 |                                                                                                                                               |
| public TableId table(\[TableId value\])                                  | Gets or sets the table ID associated with the object.                                                                                         |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                               |
| public int thousandSeparator(\[int value\])                              |                                                                                                                                               |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                               |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                               |
| public int topMarginAndFrame()                                           |                                                                                                                                               |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                               |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                               |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                               |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                               |
| public int topMode(\[int value\])                                        |                                                                                                                                               |
| public str topStr(\[str value\])                                         |                                                                                                                                               |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                               |
| public Real topValue(\[Real value\])                                     |                                                                                                                                               |
| public boolean underline(\[boolean value\])                              |                                                                                                                                               |
| public boolean visible(\[boolean value\])                                |                                                                                                                                               |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                               |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                               |
| public str webTarget(\[str value\])                                      |                                                                                                                                               |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                               |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                               |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                                |
| public int widthOfString100mm(str string)                                |                                                                                                                                               |
| public str widthStr(\[str value\])                                       |                                                                                                                                               |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                               |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                                        |
| public void show()                                                       |                                                                                                                                               |
| public void hide()                                                       |                                                                                                                                               |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                                       |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                               |
| public void left(Real value, Units unit)                                 |                                                                                                                                               |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                                        |
| public void extraSumWidth(Real value, Units unit)                        |                                                                                                                                               |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                               |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                               |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                                               |
| public void top(Real value, Units unit)                                  |                                                                                                                                               |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                               |

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method allowNegative

    public int allowNegative([int value])

#### Parameters

value  

#### Return Value

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method autoInsSeparator

    public int autoInsSeparator([int value])

#### Parameters

value  

#### Return Value

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of MicrosoftWindows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of MicrosoftWindows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                        |
|--------|-------------------------------|
| 0      | Default.                      |
| 1      | The MicrosoftWindows palette. |
| 2      | The true-color scheme.        |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method decimalSeparator

    public int decimalSeparator([int value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method displaceNegative

    public int displaceNegative([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displaceNegativeMode

    public AutoMode displaceNegativeMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displaceNegativeValue

    public int displaceNegativeValue([int value])

#### Parameters

value  

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method extraSumWidthMode

    public int extraSumWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method extraSumWidthStr

    public str extraSumWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method extraSumWidthUnit

    public Units extraSumWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method extraSumWidthValue

    public Real extraSumWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method formatMST

    public int formatMST([int value])

#### Parameters

value  

#### Return Value

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelTabLeader

    public int labelTabLeader([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthStr

    public str labelWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method labelWidthUnit

    public Units labelWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public Real labelWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method minNoOfDecimals

    public int minNoOfDecimals([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method minNoOfDecimalsMode

    public AutoMode minNoOfDecimalsMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method minNoOfDecimalsValue

    public int minNoOfDecimalsValue([int value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in the code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in the code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method noOfDecimals

    public int noOfDecimals([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method noOfDecimalsMode

    public AutoMode noOfDecimalsMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method noOfDecimalsValue

    public int noOfDecimalsValue([int value])

#### Parameters

value  

#### Return Value

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method rotateSign

    public int rotateSign([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method showZero

    public int showZero([int value])

#### Parameters

value  

#### Return Value

### Method signDisplay

    public int signDisplay([int value])

#### Parameters

value  

#### Return Value

### Method sumAll

    public boolean sumAll([boolean value])

#### Parameters

value  

#### Return Value

### Method sumNeg

    public boolean sumNeg([boolean value])

#### Parameters

value  

#### Return Value

### Method sumPos

    public boolean sumPos([boolean value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method thousandSeparator

    public int thousandSeparator([int value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method show

    public void show()

### Method hide

    public void hide()

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method extraSumWidth

    public void extraSumWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method labelWidth

    public void labelWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

## Class ReportRun
    class ReportRun extends ObjectRun

The ReportRun class generates and prints a report or previews a report on the screen.

### Remarks

As opposed to the , which defines the structure of a report, a ReportRun object contains the runtime characteristics of the report.A ReportRun object can be created by using one of the following arguments:

-   An Args object where the name and optionally designName parameters are specified.
-   A created container, by using the for example.
-   The report name and an optional design name.

The section template node type allows the sections to be defined once and reuse them many times in different reports. A typical example of this would be a check or a giro.

### Examples

The following example runs the Customer design of the existing Cust report:

    static void testReportRun(args a) 
    {  
        reportRun rr; 
        args aa = new args("Cust"); 
        aa.designName("Customer"); 
        rr = new reportRun(aa); 
        rr.run(); 
    }

### Methods

| Method                                                                                                                                                    | Description                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean allPages(\[boolean all\])                                                                                                                  |                                                                                                                                                   |
| public boolean callMenuFunction(xMenuFunction menuFunction)                                                                                               |                                                                                                                                                   |
| public str caption(str reportSpelling, str reportName, str designCaption, str designName)                                                                 | Creates a caption when previewing a report, or a document name when printing a report.                                                            |
| public boolean collate(\[boolean collate\])                                                                                                               |                                                                                                                                                   |
| public TableId columnHeadings(\[TableId tableId\])                                                                                                        | Provides control of column headings in a report.                                                                                                  |
| public ReportControl control()                                                                                                                            | Retrieves the control that is being executed.                                                                                                     |
| public int copies(\[int numberOfCopies\])                                                                                                                 |                                                                                                                                                   |
| public int copiesTotal()                                                                                                                                  | Enables marking copies of reports.                                                                                                                |
| public int copy()                                                                                                                                         | Returns the number of the copy of a report.                                                                                                       |
| public str copyDescription()                                                                                                                              |                                                                                                                                                   |
| public xFormRun createProgressForm()                                                                                                                      | Creates the form that contains progress information.                                                                                              |
| public int currentYmm100()                                                                                                                                |                                                                                                                                                   |
| public ReportDesign design(\[AnyType nameOrReportDesign\])                                                                                                | Gets or sets the name of the design.                                                                                                              |
| public str deviceName(\[str device\])                                                                                                                     |                                                                                                                                                   |
| public Object dialog(Object dialog)                                                                                                                       |                                                                                                                                                   |
| public str driverName()                                                                                                                                   | Returns the printer driver name.                                                                                                                  |
| public boolean enableAllBodies(\[boolean enable\])                                                                                                        |                                                                                                                                                   |
| public boolean execute(int number)                                                                                                                        | Prints the programmable sections of a report.                                                                                                     |
| public boolean executeBodyColumnHeadings(TableId tableId, \[FieldId fieldId\])                                                                            | Prints the column headings of a body section in a report.                                                                                         |
| public boolean executeColumnHeadings(ReportSection section)                                                                                               |                                                                                                                                                   |
| public boolean executeControlColumnHeadings(int number)                                                                                                   | Executes the column headings of a programmable section.                                                                                           |
| public boolean executeFooter(\[TableId tableId\], \[FieldId fieldId\])                                                                                    | Execute a footer section.                                                                                                                         |
| public boolean executeHeader(\[TableId tableId\], \[FieldId fieldId\])                                                                                    | Executes a header section.                                                                                                                        |
| public boolean executeSection(ReportSection section)                                                                                                      | Prints the specified section in the report.                                                                                                       |
| public boolean fetch()                                                                                                                                    | Executes the report query and calls the send method for the record that is found by the query.                                                    |
| public int from(\[int fromPage\])                                                                                                                         |                                                                                                                                                   |
| public int generateDesign(\[Query query\], \[int designNo\])                                                                                              |                                                                                                                                                   |
| public boolean getDeclineOverwrite()                                                                                                                      |                                                                                                                                                   |
| public int getNumberOfPrinters()                                                                                                                          |                                                                                                                                                   |
| public str getPrinter(int number)                                                                                                                         |                                                                                                                                                   |
| public str getRangeDescription(int number)                                                                                                                |                                                                                                                                                   |
| public ReportViewer getReportViewer()                                                                                                                     |                                                                                                                                                   |
| public PrintMedium getTarget()                                                                                                                            |                                                                                                                                                   |
| public boolean hasGeneratedDesign()                                                                                                                       |                                                                                                                                                   |
| public str headerDescription()                                                                                                                            |                                                                                                                                                   |
| public int heightOfPageFooters()                                                                                                                          |                                                                                                                                                   |
| public int indent()                                                                                                                                       |                                                                                                                                                   |
| public boolean isBodyEnabled(TableId tableId)                                                                                                             |                                                                                                                                                   |
| public Int64 jobId()                                                                                                                                      |                                                                                                                                                   |
| public Common last(TableId tableId)                                                                                                                       |                                                                                                                                                   |
| public int mm100Left()                                                                                                                                    |                                                                                                                                                   |
| public int mm100PageHeight()                                                                                                                              |                                                                                                                                                   |
| public str name(\[str name\])                                                                                                                             | Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object.                         |
| public container pack()                                                                                                                                   | Serializes the current instance of the ReportRun class.                                                                                           |
| public container packDesign()                                                                                                                             |                                                                                                                                                   |
| public container packPageSettings()                                                                                                                       |                                                                                                                                                   |
| public container packPrinterSettings()                                                                                                                    |                                                                                                                                                   |
| public container packPrintJobSettings()                                                                                                                   |                                                                                                                                                   |
| public container packSubtotalSettings()                                                                                                                   |                                                                                                                                                   |
| public int page(\[int number\])                                                                                                                           |                                                                                                                                                   |
| public boolean pageFormatting()                                                                                                                           | Displays the printer properties of the printer.                                                                                                   |
| public int pagesTotal()                                                                                                                                   |                                                                                                                                                   |
| public str passThrough(str str)                                                                                                                           |                                                                                                                                                   |
| public int pixelsLeft()                                                                                                                                   |                                                                                                                                                   |
| public int print()                                                                                                                                        | Sends the generated report to a print medium, such as a printer or the screen.                                                                    |
| public int printerAttributes()                                                                                                                            |                                                                                                                                                   |
| public int printerAveragePPM()                                                                                                                            |                                                                                                                                                   |
| public str printerComment()                                                                                                                               |                                                                                                                                                   |
| public str printerDatatype()                                                                                                                              |                                                                                                                                                   |
| public int printerDefaultPriority()                                                                                                                       |                                                                                                                                                   |
| public str printerDriverName()                                                                                                                            |                                                                                                                                                   |
| public str printerFontInfo()                                                                                                                              | Indicates which font is used to print the report.                                                                                                 |
| public str printerLocation()                                                                                                                              |                                                                                                                                                   |
| public int printerPageHeight()                                                                                                                            |                                                                                                                                                   |
| public int printerPageWidth()                                                                                                                             |                                                                                                                                                   |
| public int printerPaper()                                                                                                                                 |                                                                                                                                                   |
| public str printerParameters()                                                                                                                            |                                                                                                                                                   |
| public str printerPortName()                                                                                                                              |                                                                                                                                                   |
| public str printerPrinterName()                                                                                                                           |                                                                                                                                                   |
| public str printerPrintProcessor()                                                                                                                        |                                                                                                                                                   |
| public int printerPriority()                                                                                                                              |                                                                                                                                                   |
| public int printerQueuedJobs()                                                                                                                            |                                                                                                                                                   |
| public str printerSepFile()                                                                                                                               |                                                                                                                                                   |
| public str printerServerName()                                                                                                                            |                                                                                                                                                   |
| public boolean printerSettings(\[int showWhat\])                                                                                                          | Enables the user to select printer settings.                                                                                                      |
| public str printerShareName()                                                                                                                             |                                                                                                                                                   |
| public TimeOfDay printerStartTime()                                                                                                                       |                                                                                                                                                   |
| public int printerStatus()                                                                                                                                |                                                                                                                                                   |
| public TimeOfDay printerUntilTime()                                                                                                                       |                                                                                                                                                   |
| public PrintJobSettings printJobSettings(\[container packedPrintJobSettings\])                                                                            |                                                                                                                                                   |
| public int printSum()                                                                                                                                     |                                                                                                                                                   |
| public xFormRun progressForm(\[xFormRun form\])                                                                                                           |                                                                                                                                                   |
| public str progressInfo(int pageNo, int lineNo)                                                                                                           | Creates a string that describes how much of the report has been generated during the execution of a report every time that a section is executed. |
| public boolean prompt(\[boolean enableCopy\], \[boolean enablePages\], \[boolean enableDevice\], \[boolean enableProperties\], \[boolean enablePrintTo\]) | Prompts the user a report is run.                                                                                                                 |
| public Query query(\[Query query\])                                                                                                                       |                                                                                                                                                   |
| public QueryRun queryRun(\[QueryRun queryRun\])                                                                                                           |                                                                                                                                                   |
| public Report report()                                                                                                                                    |                                                                                                                                                   |
| public str reportUser(\[str user\])                                                                                                                       |                                                                                                                                                   |
| public int rulerCM()                                                                                                                                      |                                                                                                                                                   |
| public int rulerINCH()                                                                                                                                    |                                                                                                                                                   |
| public str screenFontInfo()                                                                                                                               |                                                                                                                                                   |
| public ReportSection section()                                                                                                                            |                                                                                                                                                   |
| public int sectionsLeft(ReportSection section)                                                                                                            |                                                                                                                                                   |
| public boolean send(Common cursor, \[int level\], \[boolean triggerOffBody\], \[boolean newPageBeforeBody\])                                              | Triggers the body sections that belong to a section group.                                                                                        |
| public PrintMedium setTarget(PrintMedium target)                                                                                                          |                                                                                                                                                   |
| public boolean showMenuFunction(xMenuFunction menuFunction)                                                                                               |                                                                                                                                                   |
| public boolean showMenuReference(WebMenu menuReference)                                                                                                   |                                                                                                                                                   |
| public str sortInfo(Common cursor)                                                                                                                        |                                                                                                                                                   |
| public Date startDate()                                                                                                                                   |                                                                                                                                                   |
| public DateTime startDateTime()                                                                                                                           |                                                                                                                                                   |
| public Date startMachineDate()                                                                                                                            |                                                                                                                                                   |
| public TimeOfDay startTime()                                                                                                                              |                                                                                                                                                   |
| public Real sum(TableId tableId, FieldId fieldId, \[int indent\])                                                                                         |                                                                                                                                                   |
| public Real sumControl(str fieldName, \[int indent\])                                                                                                     |                                                                                                                                                   |
| public Real sumControlNeg(str fieldName, \[int indent\])                                                                                                  |                                                                                                                                                   |
| public Real sumControlPos(str fieldName, \[int indent\])                                                                                                  |                                                                                                                                                   |
| public str sumDescription()                                                                                                                               |                                                                                                                                                   |
| public Real sumNeg(TableId tableId, FieldId fieldId, \[int indent\])                                                                                      |                                                                                                                                                   |
| public Real sumPos(TableId tableId, FieldId fieldId, \[int indent\])                                                                                      |                                                                                                                                                   |
| public boolean suppressReportIsEmptyMessage(\[boolean suppress\])                                                                                         |                                                                                                                                                   |
| public str title(\[str title\])                                                                                                                           | Gets or sets the print job description.                                                                                                           |
| public int to(\[int toPage\])                                                                                                                             |                                                                                                                                                   |
| public str toString()                                                                                                                                     | Returns a textual description of the class.                                                                                                       |
| public boolean unpackPageSettings(container packedPageSetup)                                                                                              |                                                                                                                                                   |
| public boolean unpackPrinterSettings(container packedPrinterSetup)                                                                                        |                                                                                                                                                   |
| public boolean unpackPrintJobSettings(container packedPrintJobSettings)                                                                                   |                                                                                                                                                   |
| public boolean unpackSubtotalSettings(container packedSubtotalSetup)                                                                                      |                                                                                                                                                   |
| public PrinterOrientation userSelectedOrientation()                                                                                                       |                                                                                                                                                   |
| public void disableBody(\[TableId tableId\])                                                                                                              |                                                                                                                                                   |
| public void attach()                                                                                                                                      |                                                                                                                                                   |
| public void new(AnyType argsOrReportOrContainer, \[str designName\], \[boolean isWebReport\])                                                             | Initializes an instance of the ReportRun class.                                                                                                   |
| public void disableSection(ReportSection section)                                                                                                         |                                                                                                                                                   |
| public void arrangeLevelGlobal()                                                                                                                          |                                                                                                                                                   |
| public void setEscapeSequence(str str)                                                                                                                    |                                                                                                                                                   |
| public void enableBody(\[TableId tableId\])                                                                                                               |                                                                                                                                                   |
| public void clearAllRangeDescriptions()                                                                                                                   |                                                                                                                                                   |
| public void header(ReportSection headerSection, TableId tableId, FieldId fieldId)                                                                         | Controls the header.                                                                                                                              |
| public void unpackDesign(container packedDesign)                                                                                                          |                                                                                                                                                   |
| public void newPage(\[boolean doPageFooter\])                                                                                                             |                                                                                                                                                   |
| public void footer(ReportSection footerSection, TableId tableId, FieldId fieldId)                                                                         | Controls the footer.                                                                                                                              |
| public void reset(\[boolean delayExceptions\])                                                                                                            | Enables a single instance of the ReportRun class to create multiple reports.                                                                      |
| public void arrangeLevelNone()                                                                                                                            |                                                                                                                                                   |
| public void run()                                                                                                                                         | Runs the report.                                                                                                                                  |
| public void gotoYmm100(\[int mm100\])                                                                                                                     |                                                                                                                                                   |
| public void disableColumnHeadings(\[TableId tableId\])                                                                                                    |                                                                                                                                                   |
| public void enablePageFooter()                                                                                                                            |                                                                                                                                                   |
| public void init()                                                                                                                                        |                                                                                                                                                   |
| public void arrangeLevelControl()                                                                                                                         |                                                                                                                                                   |
| public void disablePageFooter()                                                                                                                           |                                                                                                                                                   |
| public void addPendingSums()                                                                                                                              | Prints the relevant footers of the report.                                                                                                        |
| public void arrangeLevelSection()                                                                                                                         |                                                                                                                                                   |
| public void enableSection(ReportSection section)                                                                                                          |                                                                                                                                                   |
| public void detach()                                                                                                                                      |                                                                                                                                                   |
| public void addRangeDescription(int x, int y, str text, \[str fontName\], \[int fontSize\])                                                               |                                                                                                                                                   |
| public void finalize()                                                                                                                                    |                                                                                                                                                   |

### Method allPages

    public boolean allPages([boolean all])

#### Parameters

all  

#### Return Value

### Method callMenuFunction

    public boolean callMenuFunction(xMenuFunction menuFunction)

#### Parameters

menuFunction  

#### Return Value

### Method caption

Creates a caption when previewing a report, or a document name when printing a report.

    public str caption(str reportSpelling, str reportName, str designCaption, str designName)

#### Parameters

reportSpelling  
The name of the design.

<!-- -->

reportName  
The name of the design.

<!-- -->

designCaption  
The name of the design.

<!-- -->

designName  
The name of the design.

#### Return Value

A string that contains "DesignLabel - ReportSpelling" if the DesignLabel is not empty. A string that contains "ReportName(DesignName) - ReportSpelling" if the DesignLabel is empty.

#### Remarks

The call to the super method in this method creates a string that is used as a caption when previewing a report and as the document name when printing a report.It is recommended that you always fill out the Caption property of the report design so that the caption that is used during the preview of the report is in the actual language.

### Method collate

    public boolean collate([boolean collate])

#### Parameters

collate  

#### Return Value

### Method columnHeadings

Provides control of column headings in a report.

    public TableId columnHeadings([TableId tableId])

#### Parameters

tableId  
A table ID; optional.

#### Return Value

The last tableId value for which columnHeading objects were printed.

### Method control

Retrieves the control that is being executed.

    public ReportControl control()

#### Return Value

The control that is being executed.

#### Remarks

This method is intended for internal use.

### Method copies

    public int copies([int numberOfCopies])

#### Parameters

numberOfCopies  

#### Return Value

### Method copiesTotal

Enables marking copies of reports.

    public int copiesTotal()

#### Return Value

The number of copies the user requested in the sysPrintForm form.

#### Remarks

Controls are typically evaluated during the execution of a report. A control that uses this method is evaluated when the report is printed.

### Method copy

Returns the number of the copy of a report.

    public int copy()

#### Return Value

The number of the copy.

#### Remarks

If the user prints three copies of a report a control that have a dataFunction method, this method will return one for the first copy, two for the second copy, and three for the last copy.

### Method copyDescription

    public str copyDescription()

#### Return Value

### Method createProgressForm

Creates the form that contains progress information.

    public xFormRun createProgressForm()

#### Return Value

The form to use to display the progress information.

#### Remarks

You can overload this method. The method is called when the first page is created. The default implementation will open the SysPrintProgress form.If you implement your own progress form, you must implement the setNames and setPagePercent methods because these methods are called within the kernel.This form is shown when the pages are created, not when the pages are printed.

### Method currentYmm100

    public int currentYmm100()

#### Return Value

### Method design

Gets or sets the name of the design.

    public ReportDesign design([AnyType nameOrReportDesign])

#### Parameters

nameOrReportDesign  
The name of the design; optional.

#### Return Value

The name of the design.

#### Remarks

This method can be used to change from one design to another while the report is executed.

### Method deviceName

    public str deviceName([str device])

#### Parameters

device  

#### Return Value

### Method dialog

    public Object dialog(Object dialog)

#### Parameters

dialog  

#### Return Value

### Method driverName

Returns the printer driver name.

    public str driverName()

#### Return Value

The printer driver name.

#### Remarks

The method often returns the string "winspool". This is the printer driver name that is used when the printer device context is created.If no printers have been set up on the computer, the string "Screen" is returned.

### Method enableAllBodies

    public boolean enableAllBodies([boolean enable])

#### Parameters

enable  

#### Return Value

### Method execute

Prints the programmable sections of a report.

    public boolean execute(int number)

#### Parameters

number  
The controlNumber value of the programmable section.

#### Return Value

false if the toPage object has been generated; otherwise, true.

### Method executeBodyColumnHeadings

Prints the column headings of a body section in a report.

    public boolean executeBodyColumnHeadings(TableId tableId, [FieldId fieldId])

#### Parameters

tableId  
The field ID of the DataField property of a section group; optional.

<!-- -->

fieldId  
The field ID of the DataField property of a section group; optional.

#### Return Value

true if any column headings were printed; otherwise, false.

#### Remarks

This method is useful when a report should contain more column headings than those automatically printed in the report.

### Method executeColumnHeadings

    public boolean executeColumnHeadings(ReportSection section)

#### Parameters

section  

#### Return Value

### Method executeControlColumnHeadings

Executes the column headings of a programmable section.

    public boolean executeControlColumnHeadings(int number)

#### Parameters

number  
The controlNumber value of the programmable section.

#### Return Value

true if any sections were printed; otherwise, false.

#### Remarks

This method is useful if you want to add columnHeading objects to a programmable section.If a programmable section causes a page break, the columnHeadings objects of the section are repeated. Under these circumstances this method not have to be called.

### Method executeFooter

Execute a footer section.

    public boolean executeFooter([TableId tableId], [FieldId fieldId])

#### Parameters

tableId  
The field ID of the dataField property of the footer section group; optional.

<!-- -->

fieldId  
The field ID of the dataField property of the footer section group; optional.

#### Return Value

true if anything was printed; otherwise, false.

### Method executeHeader

Executes a header section.

    public boolean executeHeader([TableId tableId], [FieldId fieldId])

#### Parameters

tableId  
The field ID of the dataField property of the header section group; optional.

<!-- -->

fieldId  
The field ID of the dataField property of the header section group; optional.

#### Return Value

### Method executeSection

Prints the specified section in the report.

    public boolean executeSection(ReportSection section)

#### Parameters

section  
The section to print.

#### Return Value

### Method fetch

Executes the report query and calls the send method for the record that is found by the query.

    public boolean fetch()

#### Return Value

true if execution of the report should continue; otherwise, false.

#### Remarks

The fetch method is called from the super call in the run method.

### Method from

    public int from([int fromPage])

#### Parameters

fromPage  

#### Return Value

### Method generateDesign

    public int generateDesign([Query query], [int designNo])

#### Parameters

query  

<!-- -->

designNo  

#### Return Value

### Method getDeclineOverwrite

    public boolean getDeclineOverwrite()

#### Return Value

### Method getNumberOfPrinters

    public int getNumberOfPrinters()

#### Return Value

### Method getPrinter

    public str getPrinter(int number)

#### Parameters

number  

#### Return Value

### Method getRangeDescription

    public str getRangeDescription(int number)

#### Parameters

number  

#### Return Value

### Method getReportViewer

    public ReportViewer getReportViewer()

#### Return Value

### Method getTarget

    public PrintMedium getTarget()

#### Return Value

### Method hasGeneratedDesign

    public boolean hasGeneratedDesign()

#### Return Value

### Method headerDescription

    public str headerDescription()

#### Return Value

### Method heightOfPageFooters

    public int heightOfPageFooters()

#### Return Value

### Method indent

    public int indent()

#### Return Value

### Method isBodyEnabled

    public boolean isBodyEnabled(TableId tableId)

#### Parameters

tableId  

#### Return Value

### Method jobId

    public Int64 jobId()

#### Return Value

### Method last

    public Common last(TableId tableId)

#### Parameters

tableId  

#### Return Value

### Method mm100Left

    public int mm100Left()

#### Return Value

### Method mm100PageHeight

    public int mm100PageHeight()

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another MSDAX application object.

    public str name([str name])

#### Parameters

name  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method pack

Serializes the current instance of the ReportRun class.

    public container pack()

#### Return Value

A container that contains the current instance of the ReportRun class.

### Method packDesign

    public container packDesign()

#### Return Value

### Method packPageSettings

    public container packPageSettings()

#### Return Value

### Method packPrinterSettings

    public container packPrinterSettings()

#### Return Value

### Method packPrintJobSettings

    public container packPrintJobSettings()

#### Return Value

### Method packSubtotalSettings

    public container packSubtotalSettings()

#### Return Value

### Method page

    public int page([int number])

#### Parameters

number  

#### Return Value

### Method pageFormatting

Displays the printer properties of the printer.

    public boolean pageFormatting()

#### Return Value

#### Remarks

This method on the Report object is never called by the kernel. It could be called by the sysPrintForm form when the user clicks the Properties button, but instead, the sysPrintForm form calls the directly.

### Method pagesTotal

    public int pagesTotal()

#### Return Value

### Method passThrough

    public str passThrough(str str)

#### Parameters

str  

#### Return Value

### Method pixelsLeft

    public int pixelsLeft()

#### Return Value

### Method print

Sends the generated report to a print medium, such as a printer or the screen.

    public int print()

#### Return Value

#### Remarks

The call to the super method in this method directs the generated report to a printMedium object, such as printer or screen.If the target is a screen, the call to the super method will create a reportViewer object on the client and call the showPage method.If the target is a printer, the call to the super method will create a reportOutput object and call the print method on this object. If the outputToClient method of the PrintJobSettings class has been called with a parameter of true, a reportViewer object will be created and the print method of that object will be called. In in this manner, a report that is generated on the server can be output to a printer that is set up on the client.

### Method printerAttributes

    public int printerAttributes()

#### Return Value

### Method printerAveragePPM

    public int printerAveragePPM()

#### Return Value

### Method printerComment

    public str printerComment()

#### Return Value

### Method printerDatatype

    public str printerDatatype()

#### Return Value

### Method printerDefaultPriority

    public int printerDefaultPriority()

#### Return Value

### Method printerDriverName

    public str printerDriverName()

#### Return Value

### Method printerFontInfo

Indicates which font is used to print the report.

    public str printerFontInfo()

#### Return Value

The name of the font.

#### Remarks

The font to use to print the report is not necessarily the same as that set on the font property of the control as that font might not be available on the user system.

### Method printerLocation

    public str printerLocation()

#### Return Value

### Method printerPageHeight

    public int printerPageHeight()

#### Return Value

### Method printerPageWidth

    public int printerPageWidth()

#### Return Value

### Method printerPaper

    public int printerPaper()

#### Return Value

### Method printerParameters

    public str printerParameters()

#### Return Value

### Method printerPortName

    public str printerPortName()

#### Return Value

### Method printerPrinterName

    public str printerPrinterName()

#### Return Value

### Method printerPrintProcessor

    public str printerPrintProcessor()

#### Return Value

### Method printerPriority

    public int printerPriority()

#### Return Value

### Method printerQueuedJobs

    public int printerQueuedJobs()

#### Return Value

### Method printerSepFile

    public str printerSepFile()

#### Return Value

### Method printerServerName

    public str printerServerName()

#### Return Value

### Method printerSettings

Enables the user to select printer settings.

    public boolean printerSettings([int showWhat])

#### Parameters

showWhat  
This parameter is currently not functional.

#### Return Value

true if execution of the report should continue; otherwise, false.

#### Remarks

The call to the super method in this method runs the sysPrintForm form. The prompt method is called from the super method call in the prompt method. The PrintFormName property on the reportDesign object determines which form the call to the super method in the printerSettiings object will run.

### Method printerShareName

    public str printerShareName()

#### Return Value

### Method printerStartTime

    public TimeOfDay printerStartTime()

#### Return Value

### Method printerStatus

    public int printerStatus()

#### Return Value

### Method printerUntilTime

    public TimeOfDay printerUntilTime()

#### Return Value

### Method printJobSettings

    public PrintJobSettings printJobSettings([container packedPrintJobSettings])

#### Parameters

packedPrintJobSettings  

#### Return Value

### Method printSum

    public int printSum()

#### Return Value

### Method progressForm

    public xFormRun progressForm([xFormRun form])

#### Parameters

form  

#### Return Value

### Method progressInfo

Creates a string that describes how much of the report has been generated during the execution of a report every time that a section is executed.

    public str progressInfo(int pageNo, int lineNo)

#### Parameters

pageNo  
The section number of the page.

<!-- -->

lineNo  
The section number of the page.

#### Return Value

A string that describes how much of the report has been generated.

### Method prompt

Prompts the user a report is run.

    public boolean prompt([boolean enableCopy], [boolean enablePages], [boolean enableDevice], [boolean enableProperties], [boolean enablePrintTo])

#### Parameters

enableCopy  
A Boolean value that indicates whether the user can select the target in the sysPrintForm form; optional.

<!-- -->

enablePages  
A Boolean value that indicates whether the user can select the target in the sysPrintForm form; optional.

<!-- -->

enableDevice  
A Boolean value that indicates whether the user can select the target in the sysPrintForm form; optional.

<!-- -->

enableProperties  
A Boolean value that indicates whether the user can select the target in the sysPrintForm form; optional.

<!-- -->

enablePrintTo  
A Boolean value that indicates whether the user can select the target in the sysPrintForm form; optional.

#### Return Value

true if execution of report should continue; otherwise, false.

#### Remarks

The call to the super method in the prompt method runs the sysPrintForm form.This method is called from the run method.

### Method query

    public Query query([Query query])

#### Parameters

query  

#### Return Value

### Method queryRun

    public QueryRun queryRun([QueryRun queryRun])

#### Parameters

queryRun  

#### Return Value

### Method report

    public Report report()

#### Return Value

### Method reportUser

    public str reportUser([str user])

#### Parameters

user  

#### Return Value

### Method rulerCM

    public int rulerCM()

#### Return Value

### Method rulerINCH

    public int rulerINCH()

#### Return Value

### Method screenFontInfo

    public str screenFontInfo()

#### Return Value

### Method section

    public ReportSection section()

#### Return Value

### Method sectionsLeft

    public int sectionsLeft(ReportSection section)

#### Parameters

section  

#### Return Value

### Method send

Triggers the body sections that belong to a section group.

    public boolean send(Common cursor, [int level], [boolean triggerOffBody], [boolean newPageBeforeBody])

#### Parameters

cursor  

<!-- -->

level  

<!-- -->

triggerOffBody  

<!-- -->

newPageBeforeBody  

#### Return Value

false if the toPage object has been generated; otherwise true.

#### Remarks

The executeSection method of the ReportSection class is called on each triggered section.By default in a master-detail report, the records from the master table have level of one, and the records from the details table have level of two.

### Method setTarget

    public PrintMedium setTarget(PrintMedium target)

#### Parameters

target  

#### Return Value

### Method showMenuFunction

    public boolean showMenuFunction(xMenuFunction menuFunction)

#### Parameters

menuFunction  

#### Return Value

### Method showMenuReference

    public boolean showMenuReference(WebMenu menuReference)

#### Parameters

menuReference  

#### Return Value

### Method sortInfo

    public str sortInfo(Common cursor)

#### Parameters

cursor  

#### Return Value

### Method startDate

    public Date startDate()

#### Return Value

### Method startDateTime

    public DateTime startDateTime()

#### Return Value

### Method startMachineDate

    public Date startMachineDate()

#### Return Value

### Method startTime

    public TimeOfDay startTime()

#### Return Value

### Method sum

    public Real sum(TableId tableId, FieldId fieldId, [int indent])

#### Parameters

tableId  

<!-- -->

fieldId  

<!-- -->

indent  

#### Return Value

### Method sumControl

    public Real sumControl(str fieldName, [int indent])

#### Parameters

fieldName  

<!-- -->

indent  

#### Return Value

### Method sumControlNeg

    public Real sumControlNeg(str fieldName, [int indent])

#### Parameters

fieldName  

<!-- -->

indent  

#### Return Value

### Method sumControlPos

    public Real sumControlPos(str fieldName, [int indent])

#### Parameters

fieldName  

<!-- -->

indent  

#### Return Value

### Method sumDescription

    public str sumDescription()

#### Return Value

### Method sumNeg

    public Real sumNeg(TableId tableId, FieldId fieldId, [int indent])

#### Parameters

tableId  

<!-- -->

fieldId  

<!-- -->

indent  

#### Return Value

### Method sumPos

    public Real sumPos(TableId tableId, FieldId fieldId, [int indent])

#### Parameters

tableId  

<!-- -->

fieldId  

<!-- -->

indent  

#### Return Value

### Method suppressReportIsEmptyMessage

    public boolean suppressReportIsEmptyMessage([boolean suppress])

#### Parameters

suppress  

#### Return Value

### Method title

Gets or sets the print job description.

    public str title([str title])

#### Parameters

title  
The new printJobDescription value; optional.

#### Return Value

A string that contains the job description.

#### Remarks

If reports are written to the printArchive object, the print job description is stored in the jobDescription field of the printJobHeader table. If the report is previewed, the print job description is used as the caption.This method is not called by the kernel during the execution of a report. Therefore overriding the method will have no effect.

### Method to

    public int to([int toPage])

#### Parameters

toPage  

#### Return Value

### Method toString

Returns a textual description of the class.

    public str toString()

#### Return Value

A string that describes the class.

#### Remarks

For most classes the toString method returns a string that contains the class handle and name, but for some classes more information is returned in the string.

### Method unpackPageSettings

    public boolean unpackPageSettings(container packedPageSetup)

#### Parameters

packedPageSetup  

#### Return Value

### Method unpackPrinterSettings

    public boolean unpackPrinterSettings(container packedPrinterSetup)

#### Parameters

packedPrinterSetup  

#### Return Value

### Method unpackPrintJobSettings

    public boolean unpackPrintJobSettings(container packedPrintJobSettings)

#### Parameters

packedPrintJobSettings  

#### Return Value

### Method unpackSubtotalSettings

    public boolean unpackSubtotalSettings(container packedSubtotalSetup)

#### Parameters

packedSubtotalSetup  

#### Return Value

### Method userSelectedOrientation

    public PrinterOrientation userSelectedOrientation()

#### Return Value

### Method disableBody

    public void disableBody([TableId tableId])

#### Parameters

tableId  

### Method attach

    public void attach()

### Method new

Initializes an instance of the ReportRun class.

    public void new(AnyType argsOrReportOrContainer, [str designName], [boolean isWebReport])

#### Parameters

argsOrReportOrContainer  

<!-- -->

designName  

<!-- -->

isWebReport  

### Method disableSection

    public void disableSection(ReportSection section)

#### Parameters

section  

### Method arrangeLevelGlobal

    public void arrangeLevelGlobal()

### Method setEscapeSequence

    public void setEscapeSequence(str str)

#### Parameters

str  

### Method enableBody

    public void enableBody([TableId tableId])

#### Parameters

tableId  

### Method clearAllRangeDescriptions

    public void clearAllRangeDescriptions()

### Method header

Controls the header.

    public void header(ReportSection headerSection, TableId tableId, FieldId fieldId)

#### Parameters

headerSection  
The ID of the field that contains the changed value.

<!-- -->

tableId  
The ID of the field that contains the changed value.

<!-- -->

fieldId  
The ID of the field that contains the changed value.

#### Remarks

This method works just like the footer method, except it is called before a group of records, whereas the footer method is called after a group of records.

### Method unpackDesign

    public void unpackDesign(container packedDesign)

#### Parameters

packedDesign  

### Method newPage

    public void newPage([boolean doPageFooter])

#### Parameters

doPageFooter  

### Method footer

Controls the footer.

    public void footer(ReportSection footerSection, TableId tableId, FieldId fieldId)

#### Parameters

footerSection  
The ID of the field that contains the changed value.

<!-- -->

tableId  
The ID of the field that contains the changed value.

<!-- -->

fieldId  
The ID of the field that contains the changed value.

#### Remarks

This method is called when a field is sorted after it changes value, even if the user has chosen not to print headers or footers.One call of the send method can trigger the printing of multiple footer sections and header sections before the body sections. The header and footer methods allow the user to execute code before or after printing the header or footer.

### Method reset

Enables a single instance of the ReportRun class to create multiple reports.

    public void reset([boolean delayExceptions])

#### Parameters

delayExceptions  

### Method arrangeLevelNone

    public void arrangeLevelNone()

### Method run

Runs the report.

    public void run()

#### Remarks

The call to the super method in this method calls the following methods:

-   prompt - Lets the user select the printer in the sysPrintForm form
-   fetch - Runs the report query
-   print - Directs the report to the printer or display.

### Method gotoYmm100

    public void gotoYmm100([int mm100])

#### Parameters

mm100  

### Method disableColumnHeadings

    public void disableColumnHeadings([TableId tableId])

#### Parameters

tableId  

### Method enablePageFooter

    public void enablePageFooter()

### Method init

    public void init()

### Method arrangeLevelControl

    public void arrangeLevelControl()

### Method disablePageFooter

    public void disablePageFooter()

### Method addPendingSums

Prints the relevant footers of the report.

    public void addPendingSums()

#### Remarks

This method should only be called in reports where the fetch method is called more than once.

### Method arrangeLevelSection

    public void arrangeLevelSection()

### Method enableSection

    public void enableSection(ReportSection section)

#### Parameters

section  

### Method detach

    public void detach()

### Method addRangeDescription

    public void addRangeDescription(int x, int y, str text, [str fontName], [int fontSize])

#### Parameters

x  

<!-- -->

y  

<!-- -->

text  

<!-- -->

fontName  

<!-- -->

fontSize  

### Method finalize

    public void finalize()

## Class ReportSection
    class ReportSection extends TreeNode

The ReportSection class contains a collection of report controls.

### Remarks

A section is printed on the report when the query for the report is executed or when the methods of the report are executed. This class lets you to create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called. A report section can be one of the following types: prologue, page header, header, footer, page footer, epilogue, programmable section, header, body, or footer. The section template node type lets you define sections one time and then reuse them many times in different reports. A typical example of this is a check or a giro.

### Examples

The following example adds a section to a report:

    static void test(args a) 
    {  
        report r; 
        reportDesign rd; 
        reportSection rs; 
        reportRun rr; 
        // Create a simple report that is not present in  
        // the Application Object Tree. 
        r = new report(); 
        rd = r.addDesign("myDesign"); 
        rs = rd.addProgrammableSection(1);  
        // Add a section triggered by execute(1). 
        rs.addTextControl("Hello world"); 
        // Run the report. 
        rr = new reportRun(r); 
        if (rr.prompt()) // Run the sysPrintForm form. 
        { 
            rr.execute(1); // Execute the programmableSection. 
            rr.print();   // Print report to the target 
                          // (for example, printer or screen) 
                          // selected during the previous prompt call. 
        } 
    }

### Methods

| Method                                                                                       | Description                                                                                                                               |
|----------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public ReportBitmapControl addBitmapControl()                                                | Adds a bitmap control to a report section.                                                                                                |
| public ReportShapeControl addBoxControl(\[ShapeType type\])                                  | Adds a shape control to a report section.                                                                                                 |
| public ReportControl addControl(TableId tableId, FieldId fieldId, \[int arrayIndex\])        | Adds a report control to a report section.                                                                                                |
| public ReportDateControl addDateControl(TableId tableId, FieldId fieldId)                    | Adds a date control to a report section.                                                                                                  |
| public ReportDateControl addDateDisplayControl(str displayFunc, \[TableId tableId\])         | Adds a date control to a report section.                                                                                                  |
| public ReportDateTimeControl addDateTimeControl(TableId tableId, FieldId fieldId)            |                                                                                                                                           |
| public ReportDateTimeControl addDateTimeDisplayControl(str displayFunc, \[TableId tableId\]) |                                                                                                                                           |
| public ReportControl addDisplayControl(str displayFunc, \[TableId tableId\])                 |                                                                                                                                           |
| public ReportEnumControl addEnumControl(TableId tableId, FieldId fieldId)                    |                                                                                                                                           |
| public ReportEnumControl addEnumDisplayControl(str displayFunc, \[TableId tableId\])         |                                                                                                                                           |
| public ReportFieldGroup addFieldGroup(TableId tableId, str name)                             |                                                                                                                                           |
| public ReportGuidControl addGuidControl(TableId tableId, FieldId fieldId)                    |                                                                                                                                           |
| public ReportGuidControl addGuidDisplayControl(str displayFunc, \[TableId tableId\])         |                                                                                                                                           |
| public ReportInt64Control addInt64Control(TableId tableId, FieldId fieldId)                  |                                                                                                                                           |
| public ReportInt64Control addInt64DisplayControl(str displayFunc, \[TableId tableId\])       |                                                                                                                                           |
| public ReportIntegerControl addIntegerControl(TableId tableId, FieldId fieldId)              |                                                                                                                                           |
| public ReportIntegerControl addIntegerDisplayControl(str displayFunc, \[TableId tableId\])   |                                                                                                                                           |
| public ReportPromptControl addPromptControl(TableId tableId, \[FieldId fieldId\])            |                                                                                                                                           |
| public ReportRealControl addRealControl(TableId tableId, FieldId fieldId)                    |                                                                                                                                           |
| public ReportRealControl addRealDisplayControl(str displayFunc, \[TableId tableId\])         |                                                                                                                                           |
| public ReportSectionGroup addSection(TableId tableId, \[FieldId fieldId\])                   |                                                                                                                                           |
| public ReportShapeControl addShapeControl(\[ShapeType type\])                                |                                                                                                                                           |
| public ReportStringControl addStringControl(TableId tableId, FieldId fieldId)                |                                                                                                                                           |
| public ReportStringControl addStringDisplayControl(str displayFunc, \[TableId tableId\])     |                                                                                                                                           |
| public ReportSumControl addSumControl(TableId tableId, FieldId fieldId)                      |                                                                                                                                           |
| public ReportSumControl addSumNameControl(str name)                                          |                                                                                                                                           |
| public ReportTextControl addTextControl(str text)                                            |                                                                                                                                           |
| public ReportTimeControl addTimeControl(TableId tableId, FieldId fieldId)                    |                                                                                                                                           |
| public ReportTimeControl addTimeDisplayControl(str displayFunc, \[TableId tableId\])         |                                                                                                                                           |
| public int arrange()                                                                         |                                                                                                                                           |
| public int arrangeMethod(\[int value\])                                                      |                                                                                                                                           |
| public int arrangeWhen(\[int value\])                                                        |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                                            | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public boolean autoHeader(\[boolean value\])                                                 |                                                                                                                                           |
| public int bold(\[int value\])                                                               | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int bottomMarginAndFrame()                                                            |                                                                                                                                           |
| public int bottomMarginMode(\[int value\])                                                   |                                                                                                                                           |
| public str bottomMarginStr(\[str value\])                                                    |                                                                                                                                           |
| public Units bottomMarginUnit(\[Units value\])                                               |                                                                                                                                           |
| public Real bottomMarginValue(\[Real value\])                                                |                                                                                                                                           |
| public int bottomMode(\[int value\])                                                         |                                                                                                                                           |
| public str bottomStr(\[str value\])                                                          |                                                                                                                                           |
| public Units bottomUnit(\[Units value\])                                                     |                                                                                                                                           |
| public Real bottomValue(\[Real value\])                                                      |                                                                                                                                           |
| public int characterSet(\[int value\])                                                       | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                                        | Gets or sets the color scheme of the control.                                                                                             |
| public int columnHeadingsStrategy(\[int value\])                                             |                                                                                                                                           |
| public int columns(\[int value\], \[ColumnsMode mode\])                                      |                                                                                                                                           |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                         |                                                                                                                                           |
| public int columnspaceMode(\[int value\])                                                    |                                                                                                                                           |
| public str columnspaceStr(\[str value\])                                                     |                                                                                                                                           |
| public Units columnspaceUnit(\[Units value\])                                                |                                                                                                                                           |
| public Real columnspaceValue(\[Real value\])                                                 |                                                                                                                                           |
| public int columnsValue(\[int value\])                                                       |                                                                                                                                           |
| public ReportControl control(FieldId fieldId, \[TableId tableId\])                           | Finds a control in the section, based on the control’s table and dataField properties.                                                    |
| public int controlCount()                                                                    |                                                                                                                                           |
| public ReportControl controlName(str name)                                                   | Finds a control in a section, based on the control's Name property.                                                                       |
| public ReportControl controlNo(int number)                                                   |                                                                                                                                           |
| public int controlNumber(\[int value\])                                                      |                                                                                                                                           |
| public int delete()                                                                          | Deletes the current node from the AOT.                                                                                                    |
| public str font(\[str value\])                                                               | Gets or sets the name of the font for the control to use.                                                                                 |
| public int fontSize(\[int value\])                                                           | Gets or sets the size of the font for the control to use.                                                                                 |
| public str footerText(\[str value\])                                                         |                                                                                                                                           |
| public int foregroundColor(\[int value\])                                                    | Gets or sets the text color for the control to use.                                                                                       |
| public boolean grandHeader(\[boolean value\])                                                |                                                                                                                                           |
| public boolean grandTotal(\[boolean value\])                                                 | Determines whether the FooterText property value can be displayed.                                                                        |
| public boolean hasButtons(\[boolean value\])                                                 |                                                                                                                                           |
| public int headerDetailLevel(\[int value\], \[AutoMode mode\])                               |                                                                                                                                           |
| public AutoMode headerDetailLevelMode(\[AutoMode mode\])                                     |                                                                                                                                           |
| public int headerDetailLevelValue(\[int value\])                                             |                                                                                                                                           |
| public str headerText(\[str value\])                                                         |                                                                                                                                           |
| public int height100mm(\[int height\])                                                       | Gets or sets the height of a section, excluding the height of the border and the top and bottom margins.                                  |
| public int heightmm100(\[int heightInclMargins\])                                            | Gets or sets the height of a section, including the height of the border and the top and bottom margins.                                  |
| public int heightMode(\[int value\])                                                         | Gets or sets a calculation mode for the height of the control.                                                                            |
| public str heightStr(\[str value\])                                                          |                                                                                                                                           |
| public Units heightUnit(\[Units value\])                                                     |                                                                                                                                           |
| public Real heightValue(\[Real value\])                                                      | Gets or sets the height of the control.                                                                                                   |
| public boolean italic(\[boolean value\])                                                     |                                                                                                                                           |
| public str label()                                                                           | Gets the description of the section node in the AOT.                                                                                      |
| public int labelBottomMarginMode(\[int value\])                                              |                                                                                                                                           |
| public str labelBottomMarginStr(\[str value\])                                               |                                                                                                                                           |
| public Units labelBottomMarginUnit(\[Units value\])                                          |                                                                                                                                           |
| public Real labelBottomMarginValue(\[Real value\])                                           |                                                                                                                                           |
| public int labelTopMarginMode(\[int value\])                                                 |                                                                                                                                           |
| public str labelTopMarginStr(\[str value\])                                                  |                                                                                                                                           |
| public Units labelTopMarginUnit(\[Units value\])                                             |                                                                                                                                           |
| public Real labelTopMarginValue(\[Real value\])                                              |                                                                                                                                           |
| public int leftMarginMode(\[int value\])                                                     |                                                                                                                                           |
| public int leftMarginsEtc()                                                                  |                                                                                                                                           |
| public str leftMarginStr(\[str value\])                                                      |                                                                                                                                           |
| public Units leftMarginUnit(\[Units value\])                                                 |                                                                                                                                           |
| public Real leftMarginValue(\[Real value\])                                                  |                                                                                                                                           |
| public LineType lineAbove(\[LineType value\])                                                |                                                                                                                                           |
| public LineType lineBelow(\[LineType value\])                                                |                                                                                                                                           |
| public LineType lineLeft(\[LineType value\])                                                 | Gets or sets the type of line that is used as the left border of a section.                                                               |
| public LineType lineRight(\[LineType value\])                                                |                                                                                                                                           |
| public TableId map(\[TableId value\])                                                        |                                                                                                                                           |
| public str name(\[str value\])                                                               | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public int noOfHeadingLines(\[int value\], \[AutoMode mode\])                                |                                                                                                                                           |
| public AutoMode noOfHeadingLinesMode(\[AutoMode mode\])                                      |                                                                                                                                           |
| public int noOfHeadingLinesValue(\[int value\])                                              |                                                                                                                                           |
| public str resolutionX(\[str value\])                                                        |                                                                                                                                           |
| public int resolutionXStr(str value)                                                         |                                                                                                                                           |
| public Units resolutionXUnit(\[Units value\])                                                |                                                                                                                                           |
| public str resolutionY(\[str value\])                                                        |                                                                                                                                           |
| public int resolutionYStr(str value)                                                         |                                                                                                                                           |
| public Units resolutionYUnit(\[Units value\])                                                |                                                                                                                                           |
| public int rightMarginMode(\[int value\])                                                    |                                                                                                                                           |
| public int rightMarginsEtc()                                                                 |                                                                                                                                           |
| public str rightMarginStr(\[str value\])                                                     |                                                                                                                                           |
| public Units rightMarginUnit(\[Units value\])                                                |                                                                                                                                           |
| public Real rightMarginValue(\[Real value\])                                                 |                                                                                                                                           |
| public int ruler(\[int value\])                                                              |                                                                                                                                           |
| public ReportSectionGroup sectionGroup(TableId tableId, \[FieldId fieldId\])                 | Finds an existing section group in the generated design.                                                                                  |
| public ReportBlockType sectionType()                                                         | Retrieves the type of a given report section, such as ReportBlockType::Prolog, ReportBlockType::PageHeader, or ReportBlockType::Body.     |
| public int sumDetailLevel(\[int value\], \[AutoMode mode\])                                  |                                                                                                                                           |
| public AutoMode sumDetailLevelMode(\[AutoMode mode\])                                        |                                                                                                                                           |
| public int sumDetailLevelValue(\[int value\])                                                |                                                                                                                                           |
| public TableId table(\[TableId value\])                                                      | Gets or sets the table ID associated with the object.                                                                                     |
| public LineThickness thickness(\[LineThickness value\])                                      |                                                                                                                                           |
| public int topMarginAndFrame()                                                               |                                                                                                                                           |
| public int topMarginMode(\[int value\])                                                      |                                                                                                                                           |
| public str topMarginStr(\[str value\])                                                       |                                                                                                                                           |
| public Units topMarginUnit(\[Units value\])                                                  |                                                                                                                                           |
| public Real topMarginValue(\[Real value\])                                                   |                                                                                                                                           |
| public int topMode(\[int value\])                                                            |                                                                                                                                           |
| public str topStr(\[str value\])                                                             |                                                                                                                                           |
| public Units topUnit(\[Units value\])                                                        |                                                                                                                                           |
| public Real topValue(\[Real value\])                                                         |                                                                                                                                           |
| public boolean underline(\[boolean value\])                                                  |                                                                                                                                           |
| public void columnspace(Real value, Units unit)                                              |                                                                                                                                           |
| public void bottom(Real value, Units unit)                                                   |                                                                                                                                           |
| public void labelBottomMargin(Real value, Units unit)                                        |                                                                                                                                           |
| public void labelTopMargin(Real value, Units unit)                                           |                                                                                                                                           |
| public void executeColumnHeadings()                                                          |                                                                                                                                           |
| public void executeSection()                                                                 | Prints the section on the report.                                                                                                         |
| public void rightMargin(Real value, Units unit)                                              |                                                                                                                                           |
| public void bottomMargin(Real value, Units unit)                                             |                                                                                                                                           |
| public void topMargin(Real value, Units unit)                                                |                                                                                                                                           |
| public void leftMargin(Real value, Units unit)                                               |                                                                                                                                           |
| public void top(Real value, Units unit)                                                      |                                                                                                                                           |
| public void height(Real value, Units unit)                                                   | Gets or sets the height of the control.                                                                                                   |

### Method addBitmapControl

Adds a bitmap control to a report section.

    public ReportBitmapControl addBitmapControl()

#### Return Value

The bitmap control that is created.

### Method addBoxControl

Adds a shape control to a report section.

    public ReportShapeControl addBoxControl([ShapeType type])

#### Parameters

type  
The type of shape control to add; optional.

#### Return Value

The shape control that is created.

### Method addControl

Adds a report control to a report section.

    public ReportControl addControl(TableId tableId, FieldId fieldId, [int arrayIndex])

#### Parameters

tableId  

<!-- -->

fieldId  

<!-- -->

arrayIndex  

#### Return Value

The report control that is created.

#### Remarks

This method adds the specified type of control, such as string, enumeration, integer, real, or date, depending on the type of the field that is specified by the arguments.

### Method addDateControl

Adds a date control to a report section.

    public ReportDateControl addDateControl(TableId tableId, FieldId fieldId)

#### Parameters

tableId  
The field ID.

<!-- -->

fieldId  
The field ID.

#### Return Value

The date control that is created.

#### Examples

    static void test(args a) 
    { 
        reportRun rr; 
        inventTrans rec; 
        int i; 
        // Create a simple report that is not present in 
        // the Application Object Tree. 
        report r = new report(); 
        reportDesign rd = r.addDesign("myDesign"); 
        reportSection rs = rd.AddSection(reportBlockType::body,  
        tablenum(inventTrans)); 
        int t = tablenum(inventTrans); 
        int f; 
        f = fieldnum(inventTrans, datePhysical); 
        rs.addDateControl(t,f); 
        // run the report 
        rr = new reportRun(r); 
        // Run the sysPrintForm form. 
        if (rr.prompt())  
        { 
            while select rec 
                rr.send(rec); 
            // Print report to the target (e.g. printer or screen) selected during the  
            // prompt call above. 
            rr.print();  
        } 
    }

### Method addDateDisplayControl

Adds a date control to a report section.

    public ReportDateControl addDateDisplayControl(str displayFunc, [TableId tableId])

#### Parameters

displayFunc  
The name of the table on which the display method is declared; optional.

<!-- -->

tableId  
The name of the table on which the display method is declared; optional.

#### Return Value

The date control that is created.

#### Remarks

The data control shows the result when a display method returns a date.

### Method addDateTimeControl

    public ReportDateTimeControl addDateTimeControl(TableId tableId, FieldId fieldId)

#### Parameters

tableId  

<!-- -->

fieldId  

#### Return Value

### Method addDateTimeDisplayControl

    public ReportDateTimeControl addDateTimeDisplayControl(str displayFunc, [TableId tableId])

#### Parameters

displayFunc  

<!-- -->

tableId  

#### Return Value

### Method addDisplayControl

    public ReportControl addDisplayControl(str displayFunc, [TableId tableId])

#### Parameters

displayFunc  

<!-- -->

tableId  

#### Return Value

### Method addEnumControl

    public ReportEnumControl addEnumControl(TableId tableId, FieldId fieldId)

#### Parameters

tableId  

<!-- -->

fieldId  

#### Return Value

### Method addEnumDisplayControl

    public ReportEnumControl addEnumDisplayControl(str displayFunc, [TableId tableId])

#### Parameters

displayFunc  

<!-- -->

tableId  

#### Return Value

### Method addFieldGroup

    public ReportFieldGroup addFieldGroup(TableId tableId, str name)

#### Parameters

tableId  

<!-- -->

name  

#### Return Value

### Method addGuidControl

    public ReportGuidControl addGuidControl(TableId tableId, FieldId fieldId)

#### Parameters

tableId  

<!-- -->

fieldId  

#### Return Value

### Method addGuidDisplayControl

    public ReportGuidControl addGuidDisplayControl(str displayFunc, [TableId tableId])

#### Parameters

displayFunc  

<!-- -->

tableId  

#### Return Value

### Method addInt64Control

    public ReportInt64Control addInt64Control(TableId tableId, FieldId fieldId)

#### Parameters

tableId  

<!-- -->

fieldId  

#### Return Value

### Method addInt64DisplayControl

    public ReportInt64Control addInt64DisplayControl(str displayFunc, [TableId tableId])

#### Parameters

displayFunc  

<!-- -->

tableId  

#### Return Value

### Method addIntegerControl

    public ReportIntegerControl addIntegerControl(TableId tableId, FieldId fieldId)

#### Parameters

tableId  

<!-- -->

fieldId  

#### Return Value

### Method addIntegerDisplayControl

    public ReportIntegerControl addIntegerDisplayControl(str displayFunc, [TableId tableId])

#### Parameters

displayFunc  

<!-- -->

tableId  

#### Return Value

### Method addPromptControl

    public ReportPromptControl addPromptControl(TableId tableId, [FieldId fieldId])

#### Parameters

tableId  

<!-- -->

fieldId  

#### Return Value

### Method addRealControl

    public ReportRealControl addRealControl(TableId tableId, FieldId fieldId)

#### Parameters

tableId  

<!-- -->

fieldId  

#### Return Value

### Method addRealDisplayControl

    public ReportRealControl addRealDisplayControl(str displayFunc, [TableId tableId])

#### Parameters

displayFunc  

<!-- -->

tableId  

#### Return Value

### Method addSection

    public ReportSectionGroup addSection(TableId tableId, [FieldId fieldId])

#### Parameters

tableId  

<!-- -->

fieldId  

#### Return Value

### Method addShapeControl

    public ReportShapeControl addShapeControl([ShapeType type])

#### Parameters

type  

#### Return Value

### Method addStringControl

    public ReportStringControl addStringControl(TableId tableId, FieldId fieldId)

#### Parameters

tableId  

<!-- -->

fieldId  

#### Return Value

### Method addStringDisplayControl

    public ReportStringControl addStringDisplayControl(str displayFunc, [TableId tableId])

#### Parameters

displayFunc  

<!-- -->

tableId  

#### Return Value

### Method addSumControl

    public ReportSumControl addSumControl(TableId tableId, FieldId fieldId)

#### Parameters

tableId  

<!-- -->

fieldId  

#### Return Value

### Method addSumNameControl

    public ReportSumControl addSumNameControl(str name)

#### Parameters

name  

#### Return Value

### Method addTextControl

    public ReportTextControl addTextControl(str text)

#### Parameters

text  

#### Return Value

### Method addTimeControl

    public ReportTimeControl addTimeControl(TableId tableId, FieldId fieldId)

#### Parameters

tableId  

<!-- -->

fieldId  

#### Return Value

### Method addTimeDisplayControl

    public ReportTimeControl addTimeDisplayControl(str displayFunc, [TableId tableId])

#### Parameters

displayFunc  

<!-- -->

tableId  

#### Return Value

### Method arrange

    public int arrange()

#### Return Value

### Method arrangeMethod

    public int arrangeMethod([int value])

#### Parameters

value  

#### Return Value

### Method arrangeWhen

    public int arrangeWhen([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method autoHeader

    public boolean autoHeader([boolean value])

#### Parameters

value  

#### Return Value

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method bottomMode

    public int bottomMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomStr

    public str bottomStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomUnit

    public Units bottomUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomValue

    public Real bottomValue([Real value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows:

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows:

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows:

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value that is based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

### Method columnHeadingsStrategy

    public int columnHeadingsStrategy([int value])

#### Parameters

value  

#### Return Value

### Method columns

    public int columns([int value], [ColumnsMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnsMode

    public ColumnsMode columnsMode([ColumnsMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspaceMode

    public int columnspaceMode([int value])

#### Parameters

value  

#### Return Value

### Method columnspaceStr

    public str columnspaceStr([str value])

#### Parameters

value  

#### Return Value

### Method columnspaceUnit

    public Units columnspaceUnit([Units value])

#### Parameters

value  

#### Return Value

### Method columnspaceValue

    public Real columnspaceValue([Real value])

#### Parameters

value  

#### Return Value

### Method columnsValue

    public int columnsValue([int value])

#### Parameters

value  

#### Return Value

### Method control

Finds a control in the section, based on the control’s table and dataField properties.

    public ReportControl control(FieldId fieldId, [TableId tableId])

#### Parameters

fieldId  
The control's table property; optional.

<!-- -->

tableId  
The control's table property; optional.

#### Return Value

The report control that is found.

#### Remarks

If the table ID is not supplied, the table property from the section’s parent section group is used.

### Method controlCount

    public int controlCount()

#### Return Value

### Method controlName

Finds a control in a section, based on the control's Name property.

    public ReportControl controlName(str name)

#### Parameters

name  
The Name property of the control.

#### Return Value

The control that is found.

### Method controlNo

    public ReportControl controlNo(int number)

#### Parameters

number  

#### Return Value

### Method controlNumber

    public int controlNumber([int value])

#### Parameters

value  

#### Return Value

### Method delete

Deletes the current node from the AOT.

    public int delete()

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method footerText

    public str footerText([str value])

#### Parameters

value  

#### Return Value

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method grandHeader

    public boolean grandHeader([boolean value])

#### Parameters

value  

#### Return Value

### Method grandTotal

Determines whether the FooterText property value can be displayed.

    public boolean grandTotal([boolean value])

#### Parameters

value  

#### Return Value

true if the FooterText property value is displayed; otherwise, false.

#### Remarks

The grandTotal property is available only when a report has unnested, multiple data sources.

### Method hasButtons

    public boolean hasButtons([boolean value])

#### Parameters

value  

#### Return Value

### Method headerDetailLevel

    public int headerDetailLevel([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method headerDetailLevelMode

    public AutoMode headerDetailLevelMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method headerDetailLevelValue

    public int headerDetailLevelValue([int value])

#### Parameters

value  

#### Return Value

### Method headerText

    public str headerText([str value])

#### Parameters

value  

#### Return Value

### Method height100mm

Gets or sets the height of a section, excluding the height of the border and the top and bottom margins.

    public int height100mm([int height])

#### Parameters

height  
The new value in 1/100 mm; optional.

#### Return Value

The height in 1/100 mm.

#### Remarks

This method acts as a heightExclBorderAndMargins method. The height that is returned corresponds to the value of the height property. Before you use this function to set the height property, make sure that the height property is not set to AUTO. Otherwise, built-in logic might recalculate the value.

### Method heightmm100

Gets or sets the height of a section, including the height of the border and the top and bottom margins.

    public int heightmm100([int heightInclMargins])

#### Parameters

heightInclMargins  
The new total height of the section in 1/100 mm; optional.

#### Return Value

The height in 1/100 mm.

#### Remarks

This method acts as a heightInclBorderAndMargins method. Before you use this function to set the height property, make sure that the height property is not set to AUTO. Otherwise, the built-in logic might set the height. If the heightmm100 method returns 1000, the total height of the section is 10 mm.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets the description of the section node in the AOT.

    public str label()

#### Return Value

A string that contains the description of the section node.

### Method labelBottomMarginMode

    public int labelBottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method labelBottomMarginStr

    public str labelBottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method labelBottomMarginUnit

    public Units labelBottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelBottomMarginValue

    public Real labelBottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method labelTopMarginMode

    public int labelTopMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method labelTopMarginStr

    public str labelTopMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method labelTopMarginUnit

    public Units labelTopMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelTopMarginValue

    public Real labelTopMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginsEtc

    public int leftMarginsEtc()

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method map

    public TableId map([TableId value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method noOfHeadingLines

    public int noOfHeadingLines([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method noOfHeadingLinesMode

    public AutoMode noOfHeadingLinesMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method noOfHeadingLinesValue

    public int noOfHeadingLinesValue([int value])

#### Parameters

value  

#### Return Value

### Method resolutionX

    public str resolutionX([str value])

#### Parameters

value  

#### Return Value

### Method resolutionXStr

    public int resolutionXStr(str value)

#### Parameters

value  

#### Return Value

### Method resolutionXUnit

    public Units resolutionXUnit([Units value])

#### Parameters

value  

#### Return Value

### Method resolutionY

    public str resolutionY([str value])

#### Parameters

value  

#### Return Value

### Method resolutionYStr

    public int resolutionYStr(str value)

#### Parameters

value  

#### Return Value

### Method resolutionYUnit

    public Units resolutionYUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginsEtc

    public int rightMarginsEtc()

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method ruler

    public int ruler([int value])

#### Parameters

value  

#### Return Value

### Method sectionGroup

Finds an existing section group in the generated design.

    public ReportSectionGroup sectionGroup(TableId tableId, [FieldId fieldId])

#### Parameters

tableId  
The field ID; optional.

<!-- -->

fieldId  
The field ID; optional.

#### Return Value

The specified section group.

#### Examples

    static void test(args a) 
    {  
        reportRun rr;  
        inventTrans rec;  
        int i;  
        int t = tablenum(inventTrans);  
        int f = fieldnum(inventTrans, datePhysical);  
        // Create a simple report that is not present in  
        // the Application Object Tree. 
        report r = new report();  
        reportDesign rd = r.addDesign("myDesign");  
        reportSectionGroup rsg;  
        reportSection rs = rd.AddSection(reportBlockType::body, t);  
        rs.addControl(t,f);  
        rsg = rd.SectionGroup(t);  
        if (rsg) 
        { 
            rs = rsg.AddSection(ReportBlockType::Header);  
            // Run the report. 
            rs.AddTextControl("This is the groupHeader"); 
        } 
        rr = new reportRun(r);  
        // Run the sysPrintForm form. 
        if (rr.prompt())  
        {  
            select rec;  
            rr.send(rec);  
            // Print report to the target, such as printer or screen. 
            rr.print();  
        } 
    }

### Method sectionType

Retrieves the type of a given report section, such as ReportBlockType::Prolog, ReportBlockType::PageHeader, or ReportBlockType::Body.

    public ReportBlockType sectionType()

#### Return Value

The report block type of the section.

#### Remarks

The reportBlockType type should be reportSectionType.

### Method sumDetailLevel

    public int sumDetailLevel([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method sumDetailLevelMode

    public AutoMode sumDetailLevelMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method sumDetailLevelValue

    public int sumDetailLevelValue([int value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method columnspace

    public void columnspace(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method bottom

    public void bottom(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method labelBottomMargin

    public void labelBottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method labelTopMargin

    public void labelTopMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method executeColumnHeadings

    public void executeColumnHeadings()

### Method executeSection

Prints the section on the report.

    public void executeSection()

#### Remarks

This method is called when the section is triggered. For example, a body section is triggered when ReportRun::send method is executed. It is the super method call in the executeSection method that actually prints the section in the report. In the Microsoft Dynamics AX Application Object Tree (AOT), you will find the executeSection method below each section's methods node. If you want to perform some action before a section is printed, such as go to the next page, this action can be coded in the executeSection method.

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

## Class ReportSectionGroup
    class ReportSectionGroup extends TreeNode

The ReportSectionGroup class defines a collection of report sections.

### Remarks

A report section group can contain header sections, body sections, and footer sections. This class lets you create, read, update, and delete X++ code and metadata. You must have access to the development security key (SysDevelopment) before you call this API.

### Examples

### Methods

| Method                                                       | Description                                                                                                               |
|--------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| public ReportSection addSection(ReportBlockType sectionType) |                                                                                                                           |
| public FieldId dataField(\[FieldId value\])                  |                                                                                                                           |
| public int delete()                                          |                                                                                                                           |
| public str name(\[str value\])                               | Gets or sets the name that is used in code to identify a form, report, rable, query, or another MSDAX application object. |
| public ReportSection section(ReportBlockType sectionType)    |                                                                                                                           |
| public TableId table(\[TableId value\])                      | Gets or sets the table ID associated with the object.                                                                     |

### Method addSection

    public ReportSection addSection(ReportBlockType sectionType)

#### Parameters

sectionType  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, rable, query, or another MSDAX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method section

    public ReportSection section(ReportBlockType sectionType)

#### Parameters

sectionType  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

## Class ReportShapeControl
    class ReportShapeControl extends ReportControl

The ReportShapeControl class enables you to create, read, update, and delete X++ code and metadata.

### Remarks

### Examples

### Methods

| Method                                                                   | Description                                                                                                       |
|--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                |
| public int bottomMarginAndFrame()                                        |                                                                                                                   |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                   |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                   |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                   |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                   |
| public int changeLabelCase(\[int value\])                                |                                                                                                                   |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                     |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                               |
| public ReportFieldType controlType()                                     |                                                                                                                   |
| public str cssClass(\[str value\])                                       |                                                                                                                   |
| public int delete()                                                      |                                                                                                                   |
| public str effectiveFont()                                               |                                                                                                                   |
| public str fontInfoPrinter()                                             |                                                                                                                   |
| public int fontInfoPrinterAscent()                                       |                                                                                                                   |
| public int fontInfoPrinterDescent()                                      |                                                                                                                   |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                   |
| public int fontInfoPrinterHeight()                                       |                                                                                                                   |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                   |
| public str fontInfoScreen()                                              |                                                                                                                   |
| public int fontInfoScreenAscent()                                        |                                                                                                                   |
| public int fontInfoScreenDescent()                                       |                                                                                                                   |
| public int fontInfoScreenExtLead()                                       |                                                                                                                   |
| public int fontInfoScreenHeight()                                        |                                                                                                                   |
| public int fontInfoScreenIntLead()                                       |                                                                                                                   |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                               |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                   |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                   |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                    |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                   |
| public str heightStr(\[str value\])                                      |                                                                                                                   |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                   |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                           |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                             |
| public int labelBold(\[int value\])                                      |                                                                                                                   |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                   |
| public str labelCssClass(\[str value\])                                  |                                                                                                                   |
| public str labelFont(\[str value\])                                      |                                                                                                                   |
| public int labelFontSize(\[int value\])                                  |                                                                                                                   |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                   |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                   |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                   |
| public int labelPosition(\[int value\])                                  |                                                                                                                   |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                   |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                   |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                   |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                   |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                   |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                   |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                   |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                   |
| public int leftMarginAnFrame()                                           |                                                                                                                   |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                   |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                   |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                   |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                   |
| public int leftMode(\[int value\])                                       |                                                                                                                   |
| public str leftStr(\[str value\])                                        |                                                                                                                   |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                   |
| public Real leftValue(\[Real value\])                                    |                                                                                                                   |
| public LineType line(\[LineType value\])                                 |                                                                                                                   |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                   |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                   |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                       |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                   |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                   |
| public str menuItemName(\[str value\])                                   |                                                                                                                   |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                   |
| public str modelFieldName(\[str value\])                                 |                                                                                                                   |
| public str name(\[str value\])                                           | Gets or sets the name used in code to identify a form, report, rable, query, or another MSDAX application object. |
| public int numberOfLines(int height100mm)                                |                                                                                                                   |
| public int position(\[int value\])                                       |                                                                                                                   |
| public str previewInfo(str string)                                       |                                                                                                                   |
| public int previewXCompensation100mm(str string)                         |                                                                                                                   |
| public int right100mm()                                                  |                                                                                                                   |
| public int right100mmInclBorder()                                        |                                                                                                                   |
| public int rightMarginAndFrame()                                         |                                                                                                                   |
| public int rightMarginMode(\[int value\])                                |                                                                                                                   |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                   |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                   |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                   |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                   |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                   |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                   |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                   |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                   |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                   |
| public int topMarginAndFrame()                                           |                                                                                                                   |
| public int topMarginMode(\[int value\])                                  |                                                                                                                   |
| public str topMarginStr(\[str value\])                                   |                                                                                                                   |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                   |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                   |
| public int topMode(\[int value\])                                        |                                                                                                                   |
| public str topStr(\[str value\])                                         |                                                                                                                   |
| public Units topUnit(\[Units value\])                                    |                                                                                                                   |
| public Real topValue(\[Real value\])                                     |                                                                                                                   |
| public ShapeType type(\[ShapeType value\])                               |                                                                                                                   |
| public boolean visible(\[boolean value\])                                |                                                                                                                   |
| public str webMenuItemName(\[str value\])                                |                                                                                                                   |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                   |
| public str webTarget(\[str value\])                                      |                                                                                                                   |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                   |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                   |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                    |
| public int widthOfString100mm(str string)                                |                                                                                                                   |
| public str widthStr(\[str value\])                                       |                                                                                                                   |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                   |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                            |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                   |
| public void left(Real value, Units unit)                                 |                                                                                                                   |
| public void top(Real value, Units unit)                                  |                                                                                                                   |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                   |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                           |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                   |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                   |
| public void hide()                                                       |                                                                                                                   |
| public void topMargin(Real value, Units unit)                            |                                                                                                                   |
| public void show()                                                       |                                                                                                                   |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                            |

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelTabLeader

    public int labelTabLeader([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthStr

    public str labelWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method labelWidthUnit

    public Units labelWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public Real labelWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method line

    public LineType line([LineType value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name used in code to identify a form, report, rable, query, or another MSDAX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method type

    public ShapeType type([ShapeType value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method labelWidth

    public void labelWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method hide

    public void hide()

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method show

    public void show()

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

## Class ReportStringControl
    class ReportStringControl extends ReportControl

The ReportStringControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                   | Description                                                                                                                               |
|--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                           |
| public int arrayIndex(\[int value\])                                     |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public int backgroundColor(\[int value\])                                | Gets or sets the background color of the control.                                                                                         |
| public int backStyle(\[int value\])                                      | Determines whether the control background can be transparent.                                                                             |
| public int bold(\[int value\])                                           | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int bottomMarginAndFrame()                                        |                                                                                                                                           |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                           |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                           |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                           |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                           |
| public int changeCase(\[int value\])                                     |                                                                                                                                           |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                           |
| public int characterSet(\[int value\])                                   | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                       |
| public ReportFieldType controlType()                                     |                                                                                                                                           |
| public str cssClass(\[str value\])                                       |                                                                                                                                           |
| public FieldId dataField(\[FieldId value\])                              |                                                                                                                                           |
| public str dataMethod(\[str value\])                                     |                                                                                                                                           |
| public int delete()                                                      |                                                                                                                                           |
| public boolean dynamicHeight(\[boolean value\])                          |                                                                                                                                           |
| public str effectiveFont()                                               |                                                                                                                                           |
| public str eval()                                                        |                                                                                                                                           |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])         |                                                                                                                                           |
| public str font(\[str value\])                                           | Gets or sets the name of the font for the control to use.                                                                                 |
| public str fontInfoPrinter()                                             |                                                                                                                                           |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                           |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                           |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                           |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                           |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                           |
| public str fontInfoScreen()                                              |                                                                                                                                           |
| public int fontInfoScreenAscent()                                        |                                                                                                                                           |
| public int fontInfoScreenDescent()                                       |                                                                                                                                           |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                           |
| public int fontInfoScreenHeight()                                        |                                                                                                                                           |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                           |
| public int fontSize(\[int value\])                                       | Gets or sets the size of the font for the control to use.                                                                                 |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                                       |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                           |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                           |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                            |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                           |
| public str heightStr(\[str value\])                                      |                                                                                                                                           |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                           |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                                   |
| public boolean italic(\[boolean value\])                                 |                                                                                                                                           |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                     |
| public int labelBold(\[int value\])                                      |                                                                                                                                           |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                                           |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                           |
| public str labelFont(\[str value\])                                      |                                                                                                                                           |
| public int labelFontSize(\[int value\])                                  |                                                                                                                                           |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                                           |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                           |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                           |
| public int labelPosition(\[int value\])                                  |                                                                                                                                           |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                                           |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                                           |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                                           |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                                           |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                                           |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                                           |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                           |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                           |
| public int leftMarginAnFrame()                                           |                                                                                                                                           |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                           |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                           |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                           |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                           |
| public int leftMode(\[int value\])                                       |                                                                                                                                           |
| public str leftStr(\[str value\])                                        |                                                                                                                                           |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                           |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                           |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                               |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                           |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                           |
| public str menuItemName(\[str value\])                                   |                                                                                                                                           |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                           |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                           |
| public str name(\[str value\])                                           | Gets or sets the name that is used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object. |
| public int numberOfLines(int height100mm)                                |                                                                                                                                           |
| public int position(\[int value\])                                       |                                                                                                                                           |
| public str previewInfo(str string)                                       |                                                                                                                                           |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                           |
| public int right100mm()                                                  |                                                                                                                                           |
| public int right100mmInclBorder()                                        |                                                                                                                                           |
| public int rightMarginAndFrame()                                         |                                                                                                                                           |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                           |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                           |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                           |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                           |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                           |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                           |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                                           |
| public TableId table(\[TableId value\])                                  | Gets or sets the table ID associated with the object.                                                                                     |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                           |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                           |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                           |
| public int topMarginAndFrame()                                           |                                                                                                                                           |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                           |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                           |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                           |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                           |
| public int topMode(\[int value\])                                        |                                                                                                                                           |
| public str topStr(\[str value\])                                         |                                                                                                                                           |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                           |
| public Real topValue(\[Real value\])                                     |                                                                                                                                           |
| public boolean underline(\[boolean value\])                              |                                                                                                                                           |
| public boolean visible(\[boolean value\])                                |                                                                                                                                           |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                           |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                           |
| public str webTarget(\[str value\])                                      |                                                                                                                                           |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                           |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                           |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                            |
| public int widthOfString100mm(str string)                                |                                                                                                                                           |
| public str widthStr(\[str value\])                                       |                                                                                                                                           |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                           |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                                    |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                                   |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                           |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                                           |
| public void hide()                                                       |                                                                                                                                           |
| public void left(Real value, Units unit)                                 |                                                                                                                                           |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                           |
| public void show()                                                       |                                                                                                                                           |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                                    |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                           |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                           |
| public void top(Real value, Units unit)                                  |                                                                                                                                           |

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determines whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeCase

    public int changeCase([int value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value that is based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method dynamicHeight

    public boolean dynamicHeight([boolean value])

#### Parameters

value  

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method eval

    public str eval()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelTabLeader

    public int labelTabLeader([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthStr

    public str labelWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method labelWidthUnit

    public Units labelWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public Real labelWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method labelWidth

    public void labelWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method hide

    public void hide()

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method show

    public void show()

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

## Class ReportSumControl
    class ReportSumControl extends ReportControl

The ReportSumcontrol class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                   | Description                                                                                                                       |
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                   |
| public int allowNegative(\[int value\])                                  |                                                                                                                                   |
| public int arrayIndex(\[int value\])                                     |                                                                                                                                   |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                |
| public int autoInsSeparator(\[int value\])                               |                                                                                                                                   |
| public int backgroundColor(\[int value\])                                | Gets or sets the background color of the control.                                                                                 |
| public int backStyle(\[int value\])                                      | Determiness whether the control background can be transparent.                                                                    |
| public int bold(\[int value\])                                           | Gets or sets the weight of font used to output text in the control.                                                               |
| public int bottomMarginAndFrame()                                        |                                                                                                                                   |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                   |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                   |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                   |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                   |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                   |
| public int characterSet(\[int value\])                                   | Gets or sets the character set of the font.                                                                                       |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                     |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                               |
| public ReportFieldType controlType()                                     |                                                                                                                                   |
| public str cssClass(\[str value\])                                       |                                                                                                                                   |
| public FieldId dataField(\[FieldId value\])                              |                                                                                                                                   |
| public str dataFieldName(\[str value\])                                  |                                                                                                                                   |
| public int decimalSeparator(\[int value\])                               |                                                                                                                                   |
| public int delete()                                                      |                                                                                                                                   |
| public int displaceNegative(\[int value\], \[AutoMode mode\])            |                                                                                                                                   |
| public AutoMode displaceNegativeMode(\[AutoMode mode\])                  |                                                                                                                                   |
| public int displaceNegativeValue(\[int value\])                          |                                                                                                                                   |
| public str effectiveFont()                                               |                                                                                                                                   |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])         |                                                                                                                                   |
| public int extraSumWidthMode(\[int value\])                              |                                                                                                                                   |
| public str extraSumWidthStr(\[str value\])                               |                                                                                                                                   |
| public Units extraSumWidthUnit(\[Units value\])                          |                                                                                                                                   |
| public Real extraSumWidthValue(\[Real value\])                           |                                                                                                                                   |
| public str font(\[str value\])                                           | Gets or sets the name of the font for the control to use.                                                                         |
| public str fontInfoPrinter()                                             |                                                                                                                                   |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                   |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                   |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                   |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                   |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                   |
| public str fontInfoScreen()                                              |                                                                                                                                   |
| public int fontInfoScreenAscent()                                        |                                                                                                                                   |
| public int fontInfoScreenDescent()                                       |                                                                                                                                   |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                   |
| public int fontInfoScreenHeight()                                        |                                                                                                                                   |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                   |
| public int fontSize(\[int value\])                                       | Gets or sets the size of the font for the control to use.                                                                         |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                               |
| public int formatMST(\[int value\])                                      |                                                                                                                                   |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                   |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                   |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                    |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                   |
| public str heightStr(\[str value\])                                      |                                                                                                                                   |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                   |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                           |
| public boolean italic(\[boolean value\])                                 |                                                                                                                                   |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                             |
| public int labelBold(\[int value\])                                      |                                                                                                                                   |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                                   |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                   |
| public str labelFont(\[str value\])                                      |                                                                                                                                   |
| public int labelFontSize(\[int value\])                                  |                                                                                                                                   |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                                   |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                   |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                   |
| public int labelPosition(\[int value\])                                  |                                                                                                                                   |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                                   |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                                   |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                                   |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                                   |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                                   |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                                   |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                   |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                   |
| public int leftMarginAnFrame()                                           |                                                                                                                                   |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                   |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                   |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                   |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                   |
| public int leftMode(\[int value\])                                       |                                                                                                                                   |
| public str leftStr(\[str value\])                                        |                                                                                                                                   |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                   |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                   |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                   |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                   |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                       |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                   |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                   |
| public str menuItemName(\[str value\])                                   |                                                                                                                                   |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                   |
| public int minNoOfDecimals(\[int value\], \[AutoMode mode\])             |                                                                                                                                   |
| public AutoMode minNoOfDecimalsMode(\[AutoMode mode\])                   |                                                                                                                                   |
| public int minNoOfDecimalsValue(\[int value\])                           |                                                                                                                                   |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                   |
| public str name(\[str value\])                                           | Gets or sets the name used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object. |
| public int noOfDecimals(\[int value\], \[AutoMode mode\])                |                                                                                                                                   |
| public AutoMode noOfDecimalsMode(\[AutoMode mode\])                      |                                                                                                                                   |
| public int noOfDecimalsValue(\[int value\])                              |                                                                                                                                   |
| public int numberOfLines(int height100mm)                                |                                                                                                                                   |
| public int position(\[int value\])                                       |                                                                                                                                   |
| public str previewInfo(str string)                                       |                                                                                                                                   |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                   |
| public int right100mm()                                                  |                                                                                                                                   |
| public int right100mmInclBorder()                                        |                                                                                                                                   |
| public int rightMarginAndFrame()                                         |                                                                                                                                   |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                   |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                   |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                   |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                   |
| public int rotateSign(\[int value\])                                     |                                                                                                                                   |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                   |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                   |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                                   |
| public int showZero(\[int value\])                                       |                                                                                                                                   |
| public int signDisplay(\[int value\])                                    |                                                                                                                                   |
| public int sumType(\[int value\])                                        |                                                                                                                                   |
| public TableId table(\[TableId value\])                                  | Gets or sets the table ID associated with the object.                                                                             |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                   |
| public int thousandSeparator(\[int value\])                              |                                                                                                                                   |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                   |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                   |
| public int topMarginAndFrame()                                           |                                                                                                                                   |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                   |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                   |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                   |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                   |
| public int topMode(\[int value\])                                        |                                                                                                                                   |
| public str topStr(\[str value\])                                         |                                                                                                                                   |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                   |
| public Real topValue(\[Real value\])                                     |                                                                                                                                   |
| public boolean underline(\[boolean value\])                              |                                                                                                                                   |
| public boolean visible(\[boolean value\])                                |                                                                                                                                   |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                   |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                   |
| public str webTarget(\[str value\])                                      |                                                                                                                                   |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                   |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                   |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                    |
| public int widthOfString100mm(str string)                                |                                                                                                                                   |
| public str widthStr(\[str value\])                                       |                                                                                                                                   |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                   |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                            |
| public void top(Real value, Units unit)                                  |                                                                                                                                   |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                   |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                   |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                   |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                   |
| public void show()                                                       |                                                                                                                                   |
| public void left(Real value, Units unit)                                 |                                                                                                                                   |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                            |
| public void extraSumWidth(Real value, Units unit)                        |                                                                                                                                   |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                                   |
| public void hide()                                                       |                                                                                                                                   |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                           |

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method allowNegative

    public int allowNegative([int value])

#### Parameters

value  

#### Return Value

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method autoInsSeparator

    public int autoInsSeparator([int value])

#### Parameters

value  

#### Return Value

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataFieldName

    public str dataFieldName([str value])

#### Parameters

value  

#### Return Value

### Method decimalSeparator

    public int decimalSeparator([int value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method displaceNegative

    public int displaceNegative([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displaceNegativeMode

    public AutoMode displaceNegativeMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displaceNegativeValue

    public int displaceNegativeValue([int value])

#### Parameters

value  

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method extraSumWidthMode

    public int extraSumWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method extraSumWidthStr

    public str extraSumWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method extraSumWidthUnit

    public Units extraSumWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method extraSumWidthValue

    public Real extraSumWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method formatMST

    public int formatMST([int value])

#### Parameters

value  

#### Return Value

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelTabLeader

    public int labelTabLeader([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthStr

    public str labelWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method labelWidthUnit

    public Units labelWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public Real labelWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method minNoOfDecimals

    public int minNoOfDecimals([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method minNoOfDecimalsMode

    public AutoMode minNoOfDecimalsMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method minNoOfDecimalsValue

    public int minNoOfDecimalsValue([int value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name used in code to identify a form, report, rable, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method noOfDecimals

    public int noOfDecimals([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method noOfDecimalsMode

    public AutoMode noOfDecimalsMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method noOfDecimalsValue

    public int noOfDecimalsValue([int value])

#### Parameters

value  

#### Return Value

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method rotateSign

    public int rotateSign([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method showZero

    public int showZero([int value])

#### Parameters

value  

#### Return Value

### Method signDisplay

    public int signDisplay([int value])

#### Parameters

value  

#### Return Value

### Method sumType

    public int sumType([int value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method thousandSeparator

    public int thousandSeparator([int value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method show

    public void show()

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method extraSumWidth

    public void extraSumWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method labelWidth

    public void labelWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method hide

    public void hide()

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

## Class ReportTextControl
    class ReportTextControl extends ReportControl

The ReportTextControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                   | Description                                                                                                                               |
|--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public int backgroundColor(\[int value\])                                | Gets or sets the background color of the control.                                                                                         |
| public int backStyle(\[int value\])                                      | Determines whether the control background can be transparent.                                                                             |
| public int bold(\[int value\])                                           | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int bottomMarginAndFrame()                                        |                                                                                                                                           |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                           |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                           |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                           |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                           |
| public int changeCase(\[int value\])                                     |                                                                                                                                           |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                           |
| public int characterSet(\[int value\])                                   | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                       |
| public ReportFieldType controlType()                                     |                                                                                                                                           |
| public str cssClass(\[str value\])                                       |                                                                                                                                           |
| public int delete()                                                      |                                                                                                                                           |
| public str effectiveFont()                                               |                                                                                                                                           |
| public str eval()                                                        |                                                                                                                                           |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])         |                                                                                                                                           |
| public str font(\[str value\])                                           | Gets or sets the name of the font for the control to use.                                                                                 |
| public str fontInfoPrinter()                                             |                                                                                                                                           |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                           |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                           |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                           |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                           |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                           |
| public str fontInfoScreen()                                              |                                                                                                                                           |
| public int fontInfoScreenAscent()                                        |                                                                                                                                           |
| public int fontInfoScreenDescent()                                       |                                                                                                                                           |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                           |
| public int fontInfoScreenHeight()                                        |                                                                                                                                           |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                           |
| public int fontSize(\[int value\])                                       | Gets or sets the size of the font for the control to use.                                                                                 |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                                       |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                           |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                           |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                            |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                           |
| public str heightStr(\[str value\])                                      |                                                                                                                                           |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                           |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                                   |
| public boolean italic(\[boolean value\])                                 |                                                                                                                                           |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                     |
| public int labelBold(\[int value\])                                      |                                                                                                                                           |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                                           |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                           |
| public str labelFont(\[str value\])                                      |                                                                                                                                           |
| public int labelFontSize(\[int value\])                                  |                                                                                                                                           |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                                           |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                           |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                           |
| public int labelPosition(\[int value\])                                  |                                                                                                                                           |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                                           |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                                           |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                                           |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                                           |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                                           |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                                           |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                           |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                           |
| public int leftMarginAnFrame()                                           |                                                                                                                                           |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                           |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                           |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                           |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                           |
| public int leftMode(\[int value\])                                       |                                                                                                                                           |
| public str leftStr(\[str value\])                                        |                                                                                                                                           |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                           |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                           |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                               |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                           |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                           |
| public str menuItemName(\[str value\])                                   |                                                                                                                                           |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                           |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                           |
| public str name(\[str value\])                                           | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public int numberOfLines(int height100mm)                                |                                                                                                                                           |
| public int position(\[int value\])                                       |                                                                                                                                           |
| public str previewInfo(str string)                                       |                                                                                                                                           |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                           |
| public int right100mm()                                                  |                                                                                                                                           |
| public int right100mmInclBorder()                                        |                                                                                                                                           |
| public int rightMarginAndFrame()                                         |                                                                                                                                           |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                           |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                           |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                           |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                           |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                           |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                           |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                                           |
| public str text(\[str value\])                                           |                                                                                                                                           |
| public int textExtentX100mm()                                            |                                                                                                                                           |
| public int textExtentY100mm()                                            |                                                                                                                                           |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                           |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                           |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                           |
| public int topMarginAndFrame()                                           |                                                                                                                                           |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                           |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                           |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                           |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                           |
| public int topMode(\[int value\])                                        |                                                                                                                                           |
| public str topStr(\[str value\])                                         |                                                                                                                                           |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                           |
| public Real topValue(\[Real value\])                                     |                                                                                                                                           |
| public int typeHeaderPrompt(\[int value\])                               |                                                                                                                                           |
| public boolean underline(\[boolean value\])                              |                                                                                                                                           |
| public boolean visible(\[boolean value\])                                |                                                                                                                                           |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                           |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                           |
| public str webTarget(\[str value\])                                      |                                                                                                                                           |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                           |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                           |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                            |
| public int widthOfString100mm(str string)                                |                                                                                                                                           |
| public str widthStr(\[str value\])                                       |                                                                                                                                           |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                           |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                                    |
| public void show()                                                       |                                                                                                                                           |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                           |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                           |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                                           |
| public void top(Real value, Units unit)                                  |                                                                                                                                           |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                                    |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                           |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                                   |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                           |
| public void left(Real value, Units unit)                                 |                                                                                                                                           |
| public void hide()                                                       |                                                                                                                                           |

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determines whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeCase

    public int changeCase([int value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The Integer values that are retrieved indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value that is based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method eval

    public str eval()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelTabLeader

    public int labelTabLeader([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthStr

    public str labelWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method labelWidthUnit

    public Units labelWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public Real labelWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method text

    public str text([str value])

#### Parameters

value  

#### Return Value

### Method textExtentX100mm

    public int textExtentX100mm()

#### Return Value

### Method textExtentY100mm

    public int textExtentY100mm()

#### Return Value

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method typeHeaderPrompt

    public int typeHeaderPrompt([int value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method show

    public void show()

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method labelWidth

    public void labelWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method hide

    public void hide()

## Class ReportTimeControl
    class ReportTimeControl extends ReportControl

The ReportTimeControl class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                   | Description                                                                                                                               |
|--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public int alignment(\[int value\])                                      |                                                                                                                                           |
| public int arrayIndex(\[int value\])                                     |                                                                                                                                           |
| public boolean autoDeclaration(\[boolean value\])                        | Determines whether the system can declare a member variable that has the same name as the control.                                        |
| public int backgroundColor(\[int value\])                                | Gets or sets the background color of the control.                                                                                         |
| public int backStyle(\[int value\])                                      | Determiness whether the control background can be transparent.                                                                            |
| public int bold(\[int value\])                                           | Gets or sets the weight of font that is used to output text in the control.                                                               |
| public int bottomMarginAndFrame()                                        |                                                                                                                                           |
| public int bottomMarginMode(\[int value\])                               |                                                                                                                                           |
| public str bottomMarginStr(\[str value\])                                |                                                                                                                                           |
| public Units bottomMarginUnit(\[Units value\])                           |                                                                                                                                           |
| public Real bottomMarginValue(\[Real value\])                            |                                                                                                                                           |
| public int changeLabelCase(\[int value\])                                |                                                                                                                                           |
| public int characterSet(\[int value\])                                   | Gets or sets the character set of the font.                                                                                               |
| public int colorScheme(\[int value\])                                    | Gets or sets the color scheme of the control.                                                                                             |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\]) | Gets or sets the configuration key that is assigned to the control.                                                                       |
| public ReportFieldType controlType()                                     |                                                                                                                                           |
| public str cssClass(\[str value\])                                       |                                                                                                                                           |
| public FieldId dataField(\[FieldId value\])                              |                                                                                                                                           |
| public str dataMethod(\[str value\])                                     |                                                                                                                                           |
| public int delete()                                                      |                                                                                                                                           |
| public str effectiveFont()                                               |                                                                                                                                           |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])         |                                                                                                                                           |
| public str font(\[str value\])                                           | Gets or sets the name of the font for the control to use.                                                                                 |
| public str fontInfoPrinter()                                             |                                                                                                                                           |
| public int fontInfoPrinterAscent()                                       |                                                                                                                                           |
| public int fontInfoPrinterDescent()                                      |                                                                                                                                           |
| public int fontInfoPrinterExtLead()                                      |                                                                                                                                           |
| public int fontInfoPrinterHeight()                                       |                                                                                                                                           |
| public int fontInfoPrinterIntLead()                                      |                                                                                                                                           |
| public str fontInfoScreen()                                              |                                                                                                                                           |
| public int fontInfoScreenAscent()                                        |                                                                                                                                           |
| public int fontInfoScreenDescent()                                       |                                                                                                                                           |
| public int fontInfoScreenExtLead()                                       |                                                                                                                                           |
| public int fontInfoScreenHeight()                                        |                                                                                                                                           |
| public int fontInfoScreenIntLead()                                       |                                                                                                                                           |
| public int fontSize(\[int value\])                                       | Gets or sets the size of the font for the control to use.                                                                                 |
| public int foregroundColor(\[int value\])                                | Gets or sets the text color for the control to use.                                                                                       |
| public int height100mm(\[int heightExclBorder\])                         |                                                                                                                                           |
| public int height100mmInclBorder(\[int heightInclBorder\])               |                                                                                                                                           |
| public int heightMode(\[int value\])                                     | Gets or sets a calculation mode for the height of the control.                                                                            |
| public int heightOfWordWrappedString100mm(str string)                    |                                                                                                                                           |
| public str heightStr(\[str value\])                                      |                                                                                                                                           |
| public Units heightUnit(\[Units value\])                                 |                                                                                                                                           |
| public Real heightValue(\[Real value\])                                  | Gets or sets the height of the control.                                                                                                   |
| public boolean italic(\[boolean value\])                                 |                                                                                                                                           |
| public str label(\[str value\])                                          | Gets or sets the label for a control.                                                                                                     |
| public int labelBold(\[int value\])                                      |                                                                                                                                           |
| public int labelCharacterSet(\[int value\])                              |                                                                                                                                           |
| public str labelCssClass(\[str value\])                                  |                                                                                                                                           |
| public str labelFont(\[str value\])                                      |                                                                                                                                           |
| public int labelFontSize(\[int value\])                                  |                                                                                                                                           |
| public boolean labelItalic(\[boolean value\])                            |                                                                                                                                           |
| public LineType labelLineBelow(\[LineType value\])                       |                                                                                                                                           |
| public LineThickness labelLineThickness(\[LineThickness value\])         |                                                                                                                                           |
| public int labelPosition(\[int value\])                                  |                                                                                                                                           |
| public int labelTabLeader(\[int value\])                                 |                                                                                                                                           |
| public boolean labelUnderline(\[boolean value\])                         |                                                                                                                                           |
| public int labelWidthMode(\[int value\])                                 |                                                                                                                                           |
| public str labelWidthStr(\[str value\])                                  |                                                                                                                                           |
| public Units labelWidthUnit(\[Units value\])                             |                                                                                                                                           |
| public Real labelWidthValue(\[Real value\])                              |                                                                                                                                           |
| public int left100mm(\[int leftExclBorder\])                             |                                                                                                                                           |
| public int left100mmInclBorder(\[int leftInclBorder\])                   |                                                                                                                                           |
| public int leftMarginAnFrame()                                           |                                                                                                                                           |
| public int leftMarginMode(\[int value\])                                 |                                                                                                                                           |
| public str leftMarginStr(\[str value\])                                  |                                                                                                                                           |
| public Units leftMarginUnit(\[Units value\])                             |                                                                                                                                           |
| public Real leftMarginValue(\[Real value\])                              |                                                                                                                                           |
| public int leftMode(\[int value\])                                       |                                                                                                                                           |
| public str leftStr(\[str value\])                                        |                                                                                                                                           |
| public Units leftUnit(\[Units value\])                                   |                                                                                                                                           |
| public Real leftValue(\[Real value\])                                    |                                                                                                                                           |
| public LineType lineAbove(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineBelow(\[LineType value\])                            |                                                                                                                                           |
| public LineType lineLeft(\[LineType value\])                             | Gets or sets the type of line that is used as the left border of a section.                                                               |
| public LineType lineRight(\[LineType value\])                            |                                                                                                                                           |
| public str menuItemLabel(\[str value\])                                  |                                                                                                                                           |
| public str menuItemName(\[str value\])                                   |                                                                                                                                           |
| public MenuItemType menuItemType(\[MenuItemType value\])                 |                                                                                                                                           |
| public str modelFieldName(\[str value\])                                 |                                                                                                                                           |
| public str name(\[str value\])                                           | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public int numberOfLines(int height100mm)                                |                                                                                                                                           |
| public int position(\[int value\])                                       |                                                                                                                                           |
| public str previewInfo(str string)                                       |                                                                                                                                           |
| public int previewXCompensation100mm(str string)                         |                                                                                                                                           |
| public int right100mm()                                                  |                                                                                                                                           |
| public int right100mmInclBorder()                                        |                                                                                                                                           |
| public int rightMarginAndFrame()                                         |                                                                                                                                           |
| public int rightMarginMode(\[int value\])                                |                                                                                                                                           |
| public str rightMarginStr(\[str value\])                                 |                                                                                                                                           |
| public Units rightMarginUnit(\[Units value\])                            |                                                                                                                                           |
| public Real rightMarginValue(\[Real value\])                             |                                                                                                                                           |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                |                                                                                                                                           |
| public str setHeightGetText(int lines, str string)                       |                                                                                                                                           |
| public boolean showLabel(\[boolean value\])                              |                                                                                                                                           |
| public TableId table(\[TableId value\])                                  | Gets or sets the table ID associated with the object.                                                                                     |
| public LineThickness thickness(\[LineThickness value\])                  |                                                                                                                                           |
| public int timeFormat(\[int value\])                                     |                                                                                                                                           |
| public int timeHours(\[int value\])                                      |                                                                                                                                           |
| public int timeMinute(\[int value\])                                     |                                                                                                                                           |
| public int timeSeconds(\[int value\])                                    |                                                                                                                                           |
| public int timeSeparator(\[int value\])                                  |                                                                                                                                           |
| public int top100mm(\[int topExclBorder\])                               |                                                                                                                                           |
| public int top100mmInclBorder(\[int topInclBorder\])                     |                                                                                                                                           |
| public int topMarginAndFrame()                                           |                                                                                                                                           |
| public int topMarginMode(\[int value\])                                  |                                                                                                                                           |
| public str topMarginStr(\[str value\])                                   |                                                                                                                                           |
| public Units topMarginUnit(\[Units value\])                              |                                                                                                                                           |
| public Real topMarginValue(\[Real value\])                               |                                                                                                                                           |
| public int topMode(\[int value\])                                        |                                                                                                                                           |
| public str topStr(\[str value\])                                         |                                                                                                                                           |
| public Units topUnit(\[Units value\])                                    |                                                                                                                                           |
| public Real topValue(\[Real value\])                                     |                                                                                                                                           |
| public boolean underline(\[boolean value\])                              |                                                                                                                                           |
| public boolean visible(\[boolean value\])                                |                                                                                                                                           |
| public str webMenuItemName(\[str value\])                                |                                                                                                                                           |
| public WebMenuItemType webMenuItemType(\[WebMenuItemType value\])        |                                                                                                                                           |
| public str webTarget(\[str value\])                                      |                                                                                                                                           |
| public int width100mm(\[int widthExclBorder\])                           |                                                                                                                                           |
| public int width100mmInclBorder(\[int widthInclBorder\])                 |                                                                                                                                           |
| public int widthMode(\[int value\])                                      | Gets or sets the calculation mode of the width of the control.                                                                            |
| public int widthOfString100mm(str string)                                |                                                                                                                                           |
| public str widthStr(\[str value\])                                       |                                                                                                                                           |
| public Units widthUnit(\[Units value\])                                  |                                                                                                                                           |
| public Real widthValue(\[Real value\])                                   | Gets or sets the width of the control.                                                                                                    |
| public void leftMargin(Real value, Units unit)                           |                                                                                                                                           |
| public void rightMargin(Real value, Units unit)                          |                                                                                                                                           |
| public void bottomMargin(Real value, Units unit)                         |                                                                                                                                           |
| public void width(Real value, Units unit)                                | Gets or sets the width of the control.                                                                                                    |
| public void top(Real value, Units unit)                                  |                                                                                                                                           |
| public void height(Real value, Units unit)                               | Gets or sets the height of the control.                                                                                                   |
| public void labelWidth(Real value, Units unit)                           |                                                                                                                                           |
| public void topMargin(Real value, Units unit)                            |                                                                                                                                           |
| public void left(Real value, Units unit)                                 |                                                                                                                                           |
| public void hide()                                                       |                                                                                                                                           |
| public void show()                                                       |                                                                                                                                           |

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method bottomMarginAndFrame

    public int bottomMarginAndFrame()

#### Return Value

### Method bottomMarginMode

    public int bottomMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method bottomMarginStr

    public str bottomMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method bottomMarginUnit

    public Units bottomMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method bottomMarginValue

    public Real bottomMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method changeLabelCase

    public int changeLabelCase([int value])

#### Parameters

value  

#### Return Value

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value, depending on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method controlType

    public ReportFieldType controlType()

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method delete

    public int delete()

#### Return Value

### Method effectiveFont

    public str effectiveFont()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontInfoPrinter

    public str fontInfoPrinter()

#### Return Value

### Method fontInfoPrinterAscent

    public int fontInfoPrinterAscent()

#### Return Value

### Method fontInfoPrinterDescent

    public int fontInfoPrinterDescent()

#### Return Value

### Method fontInfoPrinterExtLead

    public int fontInfoPrinterExtLead()

#### Return Value

### Method fontInfoPrinterHeight

    public int fontInfoPrinterHeight()

#### Return Value

### Method fontInfoPrinterIntLead

    public int fontInfoPrinterIntLead()

#### Return Value

### Method fontInfoScreen

    public str fontInfoScreen()

#### Return Value

### Method fontInfoScreenAscent

    public int fontInfoScreenAscent()

#### Return Value

### Method fontInfoScreenDescent

    public int fontInfoScreenDescent()

#### Return Value

### Method fontInfoScreenExtLead

    public int fontInfoScreenExtLead()

#### Return Value

### Method fontInfoScreenHeight

    public int fontInfoScreenHeight()

#### Return Value

### Method fontInfoScreenIntLead

    public int fontInfoScreenIntLead()

#### Return Value

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method height100mm

    public int height100mm([int heightExclBorder])

#### Parameters

heightExclBorder  

#### Return Value

### Method height100mmInclBorder

    public int height100mmInclBorder([int heightInclBorder])

#### Parameters

heightInclBorder  

#### Return Value

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightOfWordWrappedString100mm

    public int heightOfWordWrappedString100mm(str string)

#### Parameters

string  

#### Return Value

### Method heightStr

    public str heightStr([str value])

#### Parameters

value  

#### Return Value

### Method heightUnit

    public Units heightUnit([Units value])

#### Parameters

value  

#### Return Value

### Method heightValue

Gets or sets the height of the control.

    public Real heightValue([Real value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelCssClass

    public str labelCssClass([str value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelLineBelow

    public LineType labelLineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method labelLineThickness

    public LineThickness labelLineThickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelTabLeader

    public int labelTabLeader([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthStr

    public str labelWidthStr([str value])

#### Parameters

value  

#### Return Value

### Method labelWidthUnit

    public Units labelWidthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public Real labelWidthValue([Real value])

#### Parameters

value  

#### Return Value

### Method left100mm

    public int left100mm([int leftExclBorder])

#### Parameters

leftExclBorder  

#### Return Value

### Method left100mmInclBorder

    public int left100mmInclBorder([int leftInclBorder])

#### Parameters

leftInclBorder  

#### Return Value

### Method leftMarginAnFrame

    public int leftMarginAnFrame()

#### Return Value

### Method leftMarginMode

    public int leftMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method leftMarginStr

    public str leftMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method leftMarginUnit

    public Units leftMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftMarginValue

    public Real leftMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method leftMode

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftStr

    public str leftStr([str value])

#### Parameters

value  

#### Return Value

### Method leftUnit

    public Units leftUnit([Units value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public Real leftValue([Real value])

#### Parameters

value  

#### Return Value

### Method lineAbove

    public LineType lineAbove([LineType value])

#### Parameters

value  

#### Return Value

### Method lineBelow

    public LineType lineBelow([LineType value])

#### Parameters

value  

#### Return Value

### Method lineLeft

Gets or sets the type of line that is used as the left border of a section.

    public LineType lineLeft([LineType value])

#### Parameters

value  

#### Return Value

The type of line that is used as the left border.

### Method lineRight

    public LineType lineRight([LineType value])

#### Parameters

value  

#### Return Value

### Method menuItemLabel

    public str menuItemLabel([str value])

#### Parameters

value  

#### Return Value

### Method menuItemName

    public str menuItemName([str value])

#### Parameters

value  

#### Return Value

### Method menuItemType

    public MenuItemType menuItemType([MenuItemType value])

#### Parameters

value  

#### Return Value

### Method modelFieldName

    public str modelFieldName([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method numberOfLines

    public int numberOfLines(int height100mm)

#### Parameters

height100mm  

#### Return Value

### Method position

    public int position([int value])

#### Parameters

value  

#### Return Value

### Method previewInfo

    public str previewInfo(str string)

#### Parameters

string  

#### Return Value

### Method previewXCompensation100mm

    public int previewXCompensation100mm(str string)

#### Parameters

string  

#### Return Value

### Method right100mm

    public int right100mm()

#### Return Value

### Method right100mmInclBorder

    public int right100mmInclBorder()

#### Return Value

### Method rightMarginAndFrame

    public int rightMarginAndFrame()

#### Return Value

### Method rightMarginMode

    public int rightMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method rightMarginStr

    public str rightMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method rightMarginUnit

    public Units rightMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method rightMarginValue

    public Real rightMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method setHeightGetText

    public str setHeightGetText(int lines, str string)

#### Parameters

lines  

<!-- -->

string  

#### Return Value

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method thickness

    public LineThickness thickness([LineThickness value])

#### Parameters

value  

#### Return Value

### Method timeFormat

    public int timeFormat([int value])

#### Parameters

value  

#### Return Value

### Method timeHours

    public int timeHours([int value])

#### Parameters

value  

#### Return Value

### Method timeMinute

    public int timeMinute([int value])

#### Parameters

value  

#### Return Value

### Method timeSeconds

    public int timeSeconds([int value])

#### Parameters

value  

#### Return Value

### Method timeSeparator

    public int timeSeparator([int value])

#### Parameters

value  

#### Return Value

### Method top100mm

    public int top100mm([int topExclBorder])

#### Parameters

topExclBorder  

#### Return Value

### Method top100mmInclBorder

    public int top100mmInclBorder([int topInclBorder])

#### Parameters

topInclBorder  

#### Return Value

### Method topMarginAndFrame

    public int topMarginAndFrame()

#### Return Value

### Method topMarginMode

    public int topMarginMode([int value])

#### Parameters

value  

#### Return Value

### Method topMarginStr

    public str topMarginStr([str value])

#### Parameters

value  

#### Return Value

### Method topMarginUnit

    public Units topMarginUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topMarginValue

    public Real topMarginValue([Real value])

#### Parameters

value  

#### Return Value

### Method topMode

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topStr

    public str topStr([str value])

#### Parameters

value  

#### Return Value

### Method topUnit

    public Units topUnit([Units value])

#### Parameters

value  

#### Return Value

### Method topValue

    public Real topValue([Real value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

### Method webMenuItemName

    public str webMenuItemName([str value])

#### Parameters

value  

#### Return Value

### Method webMenuItemType

    public WebMenuItemType webMenuItemType([WebMenuItemType value])

#### Parameters

value  

#### Return Value

### Method webTarget

    public str webTarget([str value])

#### Parameters

value  

#### Return Value

### Method width100mm

    public int width100mm([int widthExclBorder])

#### Parameters

widthExclBorder  

#### Return Value

### Method width100mmInclBorder

    public int width100mmInclBorder([int widthInclBorder])

#### Parameters

widthInclBorder  

#### Return Value

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthOfString100mm

    public int widthOfString100mm(str string)

#### Parameters

string  

#### Return Value

### Method widthStr

    public str widthStr([str value])

#### Parameters

value  

#### Return Value

### Method widthUnit

    public Units widthUnit([Units value])

#### Parameters

value  

#### Return Value

### Method widthValue

Gets or sets the width of the control.

    public Real widthValue([Real value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method leftMargin

    public void leftMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method rightMargin

    public void rightMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method bottomMargin

    public void bottomMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method width

Gets or sets the width of the control.

    public void width(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method top

    public void top(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method height

Gets or sets the height of the control.

    public void height(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method labelWidth

    public void labelWidth(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method topMargin

    public void topMargin(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method left

    public void left(Real value, Units unit)

#### Parameters

value  

<!-- -->

unit  

### Method hide

    public void hide()

### Method show

    public void show()

## Class ReportViewer
    class ReportViewer extends ReportOutput

The ReportViewer class lets the user preview a report.

### Remarks

ReportViewer objects can exist only on the client, because a report preview can occur only on a client.

### Examples

The following code will print the job descriptions and the page numbers of jobs that are inserted in the printArchive on the current date, and it will show page 1 in the report viewer.

    static void aaaReportOutputExample(args a) 
    { 
        PrintJobHeader printJobHeader; 
        PrintJobPages printJobPages; 
        int myrecId; 
        reportViewer reportViewer; 
        while select printJobHeader where printJobHeader.CreatedDate >= 
                str2datetime("01/01/2011 12:00:00 am",123)
        { 
            myrecId = printJobHeader.recId; 
            print printJobHeader.jobDescription; 
            while select printJobPages  
                where printJobPages.pagesHeaderRecId == myRecId 
                    print printJobPages.PageNo; 
            reportViewer = new reportViewer(printJobHeader); 
            reportViewer.showPage(1); 
        } 
    }

### Methods

| Method                                                                                                          | Description                                     |
|-----------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| public boolean setNumberOfPages(int pageNo, \[boolean updataProgressForm\])                                     |                                                 |
| public void nextPage()                                                                                          |                                                 |
| public void lastPage()                                                                                          |                                                 |
| public void new(PrintJobHeader jobsCursor, \[PrintJobPages pagesCursor\], \[container packedPrintJobSettings\]) | Initializes a new instance of the Object class. |
| public void gotoPage(int pageNo)                                                                                |                                                 |
| public void pause()                                                                                             |                                                 |
| public void showPage(int pageNo)                                                                                |                                                 |
| public void firstPage()                                                                                         |                                                 |
| public void setAborted()                                                                                        |                                                 |
| public void close()                                                                                             |                                                 |
| public void prevPage()                                                                                          |                                                 |
| public void setCompleted()                                                                                      |                                                 |

### Method setNumberOfPages

    public boolean setNumberOfPages(int pageNo, [boolean updataProgressForm])

#### Parameters

pageNo  

<!-- -->

updataProgressForm  

#### Return Value

### Method nextPage

    public void nextPage()

### Method lastPage

    public void lastPage()

### Method new

Initializes a new instance of the Object class.

    public void new(PrintJobHeader jobsCursor, [PrintJobPages pagesCursor], [container packedPrintJobSettings])

#### Parameters

jobsCursor  

<!-- -->

pagesCursor  

<!-- -->

packedPrintJobSettings  

### Method gotoPage

    public void gotoPage(int pageNo)

#### Parameters

pageNo  

### Method pause

    public void pause()

### Method showPage

    public void showPage(int pageNo)

#### Parameters

pageNo  

### Method firstPage

    public void firstPage()

### Method setAborted

    public void setAborted()

### Method close

    public void close()

### Method prevPage

    public void prevPage()

### Method setCompleted

    public void setCompleted()

## Class ResultSet
    class ResultSet extends Object

The ResultSet class provides access to a table of data generated by executing a Statement.

### Remarks

For maximum portability, ResultSet columns within each row should be read in left-to-right order and each column should be read only once. A ResultSet provides access to a table of data generated by executing a instance. The table rows are retrieved in sequence. Within a row its column values can be accessed in any order. A ResultSet maintains a cursor that points to its current row of data. Initially the cursor is positioned before the first row. The 'next' method moves the cursor to the next row. For the getXX methods, Microsoft Dynamics AX attempts to convert the underlying data to the specified type and returns a suitable value. The getXX methods retrieve column values for the current row. You retrieve values using the index number of the column. Columns are numbered from 1. A ResultSet is automatically closed by the statement that generated it when that Statement is closed, re-executed, or is used to retrieve the next result from a sequence of multiple results.

### Examples

    static void example() 
    { 
        Connection Con; 
        Statement Stmt; 
        ResultSet R; 
        SqlStatementExecutePermission perm; 
        str sql = 'SELECT VALUE FROM SQLSYSTEMVARIABLES'; 
        Con = new Connection(); 
        Stmt = Con.createStatement(); 
        perm = new SqlStatementExecutePermission(sql); 
        perm.assert(); 
        R = Stmt.executeQuery(sql); 
        while ( R.next() ) 
        { 
            print R.getString(1); 
        } 
    }

### Methods

| Method                                    | Description                                                                               |
|-------------------------------------------|-------------------------------------------------------------------------------------------|
| public boolean getBoolean(int ColumnID)   | Retrieves the Boolean value of a column in the current row.                               |
| public int getByte(int ColumnID)          |                                                                                           |
| public Date getDate(int ColumnID)         | Retrieves the value of a column in the current row as an Microsoft Dynamics AXdate value. |
| public DateTime getDateTime(int ColumnID) |                                                                                           |
| public Guid getGuid(int ColumnID)         |                                                                                           |
| public int getInt(int ColumnID)           | Retrieves the value of a column in the current row as an integer.                         |
| public Int64 getInt64(int ColumnID)       |                                                                                           |
| public ResultSetMetaData getMetaData()    |                                                                                           |
| public Real getReal(int ColumnID)         | Retrieves the value of a column in the current row as a value of the type real.           |
| public str getString(int ColumnID)        | Gets the string value of a column in the current row.                                     |
| public boolean next()                     | Selects the first or subsequent row.                                                      |
| public boolean wasNull(int ColumnID)      | Reports whether the last column read has the value SQL NULL.                              |
| public void close()                       | Releases the object's database resources immediately.                                     |

### Method getBoolean

Retrieves the Boolean value of a column in the current row.

    public boolean getBoolean(int ColumnID)

#### Parameters

ColumnID  
The column ID.

#### Return Value

The value of a column in the current row.

### Method getByte

    public int getByte(int ColumnID)

#### Parameters

ColumnID  

#### Return Value

### Method getDate

Retrieves the value of a column in the current row as an Microsoft Dynamics AXdate value.

    public Date getDate(int ColumnID)

#### Parameters

ColumnID  
The ID of the column.

#### Return Value

The date.

### Method getDateTime

    public DateTime getDateTime(int ColumnID)

#### Parameters

ColumnID  

#### Return Value

### Method getGuid

    public Guid getGuid(int ColumnID)

#### Parameters

ColumnID  

#### Return Value

### Method getInt

Retrieves the value of a column in the current row as an integer.

    public int getInt(int ColumnID)

#### Parameters

ColumnID  
The column ID.

#### Return Value

The integer value of the column.

### Method getInt64

    public Int64 getInt64(int ColumnID)

#### Parameters

ColumnID  

#### Return Value

### Method getMetaData

    public ResultSetMetaData getMetaData()

#### Return Value

### Method getReal

Retrieves the value of a column in the current row as a value of the type real.

    public Real getReal(int ColumnID)

#### Parameters

ColumnID  
The ID of the column. The first column is 1, the second is 2, and so on.

#### Return Value

#### Examples

    while ( R.next() ) 
    { 
        print R.getReal(3); 
    }

### Method getString

Gets the string value of a column in the current row.

    public str getString(int ColumnID)

#### Parameters

ColumnID  
The column ID.

#### Return Value

The string value of the column.

### Method next

Selects the first or subsequent row.

    public boolean next()

#### Return Value

true if the new current row is valid; otherwise false.

#### Remarks

A ResultSet is initially positioned before its first row. The first call to the next method makes the first row the current row. The second call makes the second row the current row, and so on.

### Method wasNull

Reports whether the last column read has the value SQL NULL.

    public boolean wasNull(int ColumnID)

#### Parameters

ColumnID  
The column ID.

#### Return Value

true if the last column read has the value SQL nullNothingnullptrunita null reference (Nothing in Visual Basic); otherwise false.

#### Remarks

You must first call a get method, like the ResultSet.getInt method, on a column to try to read its value; then call the wasNull method to find whether the value was the SQL NULL.

### Method close

Releases the object's database resources immediately.

    public void close()

## Class ResultSetMetaData
    class ResultSetMetaData extends Object

### Remarks

### Examples

### Methods

| Method                                        | Description |
|-----------------------------------------------|-------------|
| public int getColumnCount()                   |             |
| public int getColumnDisplaySize(int ColumnID) |             |
| public str getColumnName(int ColumnID)        |             |
| public int getColumnType(int ColumnID)        |             |
| public int getPrecision(int ColumnID)         |             |
| public int getScale(int ColumnID)             |             |
| public int isNullable(int ColumnID)           |             |

### Method getColumnCount

    public int getColumnCount()

#### Return Value

### Method getColumnDisplaySize

    public int getColumnDisplaySize(int ColumnID)

#### Parameters

ColumnID  

#### Return Value

### Method getColumnName

    public str getColumnName(int ColumnID)

#### Parameters

ColumnID  

#### Return Value

### Method getColumnType

    public int getColumnType(int ColumnID)

#### Parameters

ColumnID  

#### Return Value

### Method getPrecision

    public int getPrecision(int ColumnID)

#### Parameters

ColumnID  

#### Return Value

### Method getScale

    public int getScale(int ColumnID)

#### Parameters

ColumnID  

#### Return Value

### Method isNullable

    public int isNullable(int ColumnID)

#### Parameters

ColumnID  

#### Return Value

## Class RunAsPermission
    class RunAsPermission extends CodeAccessPermission

The RunAsPermssion class controls the execution of code in the security context of another user.

### Remarks

You must call the assert method on the same tier, usually the server tier, that the corresponding CodeAccessPermission.demand method is called on before the protected API is executed. Call a method on the server tier from one of the following: The RunAsPermission class is designed to check permissions for the runAs function. For a list of all APIs protected by permissions, see Secured APIs.

-   A server static method –or–
-   A class instance method that is set to run on the server by using the RunOn class property

### Examples

The following code example shows a new instance of the RunAsPermission class. The assert method is called to declare that the code can then call the runAs function to run the EventJobDueDate.:runDueDateEventsForUser method in the security context of another user.

    server static void main(Args args) 
    { 
        RunAsPermission _perm; 
        UserId          _runAsUser; 
        SysUserInfo     _userInfo; 
        _userInfo = SysUserInfo::find(); 
        _runAsUser = _userInfo.Id; 
        _perm = new RunAsPermission(_runAsUser); 
        _perm.assert(); 
        // Invoke the protected API. 
        RunAs(_runAsUser, classnum(EventJobDueDate), "runDueDateEventsForUser"); 
        // Optionally, call revertAssert() to limit the scope of assert. 
        CodeAccessPermission::revertAssert(); 
    }

### Methods

| Method                                                 | Description                                                                                                         |
|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of a permission class object.                                                            |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission when overridden by a derived class. |
| public void new(UserId userId)                         | Initializes a new instance of the CodeAccessPermission class.                                                       |

### Method copy

Creates and returns a copy of a permission class object.

    public CodeAccessPermission copy()

#### Return Value

A copy of the derived class object.

#### Remarks

You can override this method as part of the process of making an API more secure.

### Method isSubsetOf

Determines whether a current permission is a subset of the specified permission when overridden by a derived class.

    public boolean isSubsetOf(CodeAccessPermission target)

#### Parameters

target  
A CodeAccessPermission class object.

#### Return Value

true if a current permission is a subset of a specified permission; otherwise, false.

#### Remarks

You can override the method as part of the process of making an API more secure.

### Method new

Initializes a new instance of the CodeAccessPermission class.

    public void new(UserId userId)

#### Parameters

userId  
A userId system data type that specifies an Microsoft Dynamics AX user.

#### Examples

The following example shows a new instance of the RunAsPermission class. The SysUserInfo table is used to initialize the userId parameter.

    server static void main(Args args) 
    { 
        RunAsPermission _perm; 
        UserId          _userId; 
        SysUserInfo     _userInfo; 
        _userInfo = SysUserInfo::find(); 
        _userId = _userInfo.Id; 
        _perm = new RunAsPermission(_userId); 
    }

