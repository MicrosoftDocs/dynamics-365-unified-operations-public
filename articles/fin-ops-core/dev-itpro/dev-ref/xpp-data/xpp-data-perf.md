---
# required metadata

title: Speeding up SQL operations in X++
description: This topic describes how to speed up SQL operations in the X++ language.
author: RobinARH
manager: AnnBe
ms.date: 06/18/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 150273
ms.assetid: 999a5ecf-559b-4d66-8b05-9a8e477e0518
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.version: AX 7.0.0
ms.search.validFrom: 2016-02-28

---

# Speeding up SQL operations

[!include [banner](../../includes/banner.md)]

This topic describes how to speed up SQL operations in the X++ language.

The following constructs let you insert, update, or delete multiple records. By using these constructs, you reduce communication between the application and the database, and therefore help increase performance. In some situations, record set–based operations can fall back to record-by-record operations.

| Construct         | Description                                                                                            |
|-------------------|--------------------------------------------------------------------------------------------------------|
| RecordSortedList  | Insert multiple records in one database trip. Use this construct when you want a subset of data from a specific table, and you want that data to be sorted in an order that doesn't currently exist as an index. |
| RecordInsertList  | Insert multiple records in one database trip. Use this construct when you don't have to sort the data. |
| insert\_recordset | Copy multiple records directly from one or more tables into another table in one database trip.        |
| update\_recordset | Update multiple rows in a table in one database trip.                                                  |
| delete\_from      | Delete multiple records from the database in one database trip.                                        |

## insert\_recordset
The **insert\_recordset** statement copies data directly from one or more source tables into one destination table in one server trip. It's faster to use **insert\_recordset** than an array insert. However, array inserts are more flexible if you want to handle the data before you insert it. **insert\_recordset** is a record set–based operator that performs operations on multiple records at a time. However, it can fall back to record-by-record operations in many situations.

### insert\_recordset syntax

*ListOfFields* in the destination table must match the list of fields in the source tables. Data is transferred in the order in which it appears in the list of fields. Fields in the destination table that aren't present in the list of fields are assigned **0** (zero) values, as in other areas. System fields, such as **RecId**, are assigned transparently by the kernel in the destination table.

**insert\_recordset** *DestinationTable* **(** *ListOfFields* **)**

**select** *ListOfFields1* **from** *SourceTable* **\[ where** *WhereClause* **\]** 

**\[ join** *ListOfFields2* **from** *JoinedSourceTable* **\[ where** *JoinedWhereClause* **\]\]**

### Example: Inserting data from another table

In this example, the **myNum** and **mySum** records are retrieved from the anotherTable table and inserted into the myTable table. The records are grouped according to **myNum**, and only **myNum** records that have a value that is less than or equal to **100** are included in the insertion.

```X++
insert_recordset myTable (myNum, mySum)
    select myNum, sum(myValue)
        from anotherTable
        group by myNum
        where myNum <= 100;
```

### Example: Inserting data from variables

The following example shows that the **insert\_recordset** statement can insert data that is provided in variables. In this example, the **firstonly** keyword is used so that only one row is inserted. Literals, such as **128** or **"this literal string"**, can't be used as a source of data that is inserted.

```X++
static void InsertVariable3Job(Args _args)
{
    TableAlphabet    tabA2;
    BankAccountTable tabB3;
    str  1 sLetter = "a";
    str 16 sExampleWord = "apple";
    DELETE_FROM tabA2;
    INSERT_RECORDSET tabA2
        (Letter ,ExampleWord)
    select firstonly
        sLetter ,sExampleWord // Variables.
    from tabB3;
    WHILE SELECT * from tabA2
    {
        info(tabA2 .Letter + " , " + tabA2 .ExampleWord);
    }

/***********  Actual Infolog output
Message (04:03:52 pm)
a , apple
***********/
}
```

### Example: Inserting data by using a join

The following example shows a join of three tables on an **insert\_recordset** statement that has a subselect. It also shows a **while** **select** statement that has a similar join. A variable is used to supply the inserted value for one column. The **str** variable must be declared, and must have a length that is less than or equal to the maximum length of the corresponding database field. In this example, there is an **insert\_recordset** statement for the tabEmplProj5 table. One of the target fields is named **Description**, and the field's data comes from the local variable **sDescriptionVariable**. The **insert\_recordset** statement succeeds even when the configuration key for the **Description** field is turned off. The system ignores both the **Description** field and the **sDescriptionVariable** variable. Therefore, this code provides an example of *configuration key automation*. Configuration key automation occurs when the system can automatically adjust the behavior of an **insert\_recordset** statement that inserts data into fields that the configuration key is turned off for.

```X++
static void InsertJoin42Job(Args _args)
{
    GmTabDepartment tabDept2;
    GmTabEmployee tabEmpl3;
    GmTabProject tabProj4;
    GmTabEmployeeProject tabEmplProj5;
    str 64 sDescriptionVariable = "From variable.";
    DELETE_FROM tabEmplProj5;
    INSERT_RECORDSET tabEmplProj5
        (
        Description
        , EmployeeRecId
        , ProjectRecId
        )
    Select
        sDescriptionVariable
        , RecId
    from
        tabEmpl3
        join
            tabDept2
            where tabEmpl3 .DepartmentGuid == tabDept2 .DepartmentGuid
        join RecId
            from tabProj4
            where tabDept2 .DepartmentGuid == tabProj4 .DepartmentGuid
    info(int642str(tabEmplProj5 .rowCount())
        + " ==Number of rows inserted.");
    WHILE SELECT *
        from
            tabEmplProj5
            join tabEmpl3
                where tabEmplProj5 .EmployeeRecId == tabEmpl3 .RecId
            join tabProj4
                where tabEmplProj5 .ProjectRecId == tabProj4 .RecId
    {
        info(
            tabEmpl3 .EmployeeName
            + "  --works on--  "
            + tabProj4 .ProjectName
            + " (" + tabEmplProj5 .Description + ")."
            );
    }

/*****************  Actual Infolog output
Message (01:05:41 pm)
4 ==Number of rows inserted.
Alice  --works on--  Project ZZZ (From variable.).
Alice  --works on--  Project YY (From variable.).
Beth  --works on--  Project ZZZ (From variable.).
Beth  --works on--  Project YY (From variable.).
*****************/
}
```

## update\_recordset
The **update\_recordset** statement lets you update multiple rows in one trip to the server. Therefore, the power of SQL Server can help improve the performance of some tasks. The ****update\_recordset**** statement resembles **delete\_from** in X++ and **update set** in SQL. It doesn't retrieve each record separately by fetching, changing, and updating, Instead, it works on an SQL-style record set on the database server side. If the **update** method is overridden, the implementation falls back to a classic looping construction, where one record at a time is updated. (This behavior resembles the behavior of **delete\_from** for deletions.) Therefore, the construction works on temporary tables and whole table–cached tables by using the looping construction.

### Example: Update that is based on a calculated value

The following example updates the myTableBuffer table and increments the value of the **field1** field by ten percent in all records in the table.

```X++
MyTable myTableBuffer;
update_recordset myTableBuffer
setting field1 = field1 * 1.10;
```

### Example: Update that uses a where clause

The following example updates all records in the myTable table where the **field1** field has the value **0**. The **field1** field is assigned a new value of **1**. The **field2** field is assigned a value that is the sum of **fieldX** and **fieldY**. This example updates multiple fields at the same time, and it updates only those rows that satisfy the **where** clause.

```X++
MyTable myTableBuffer;
update_recordset myTableBuffer
setting
    field1 = 1,
    field2 = fieldX + fieldY
where field1 == 0;
```

### Example: Updating joined tables

The following example shows that the **update\_recordset** statement supports joins of several tables. Data from the joined tables can be used to assign values to fields in the table that is being updated.

```X++
static void Join22aJob(Args _args)
{
    TableEmployee tabEmpl;
    TableDepartment tabDept;
    TableProject tabProj;
    update_recordset tabEmpl
    setting
        currentStatusDescription = tabDept .DeptName
            + ", " + tabProj .ProjName
    join tabDept
        where tabDept .DeptId == tabEmpl .DeptId
    join tabProj
        where tabProj .ProjId == tabEmpl .ProjId;
    info(strFmt("Number of records updated is %1."
        ,tabEmpl .rowCount()));
}
```

## delete\_from
You can delete multiple records from a database table by using a **delete\_from** statement. This approach can be more efficient and faster than an approach that uses the **xRecord .delete** method in a loop to delete one record at a time. If you've overridden the **delete** method, the system interprets the **delete\_from** statement into code that calls the **delete** method one time for each row that is deleted.

### Example: Efficiently deleting records by using delete\_from

The following example shows an efficient way to delete multiple records.

```X++
static void DeleteMultiRow1aJob(Args _args)
{
    MyWidgetTable tabWidget;
    delete_from tabWidget
        where tabWidget .quantity <= 100;
}
```

#### Example: Inefficiently deleting records by using forUpdate

The following example is inefficient. It issues a separate SQL **delete** call to the database server for every record. The **xRecord** **.delete** method never deletes more than one record per call.

```X++
static void DeleteMultiRow1bJob(Args _args)
{
    MyWidgetTable tabWidget; // extends xRecord.
    ttsBegin;
    while select
        forUpdated
        tabWidget
        where tabWidget .quantity <= 100
    {
        tabWidget .delete();
    }
    ttsCommit;
}
```
### Example: A delete operation that has an inner join

Inner joins aren't supported on the **delete\_from** statement. Therefore, you can't use the unmodified **join** keyword on the **delete\_from** statement. However, you can logically accomplish an inner join by using other techniques. The following example shows the new and old techniques for achieving inner join logic through a sequence of statements.

```X++
// This is the new and recommended way of using the delete_from method and inner joins.
// The following code example is relatively efficient. It issues a
// separate delete_from statement for each loop iteration. However, each
// delete_from statement can delete multiple records, a subset of all the
// records that the job deletes.
static void DeleteInnerJoin2bJob(Args _args)
{
    MyWidgetTable tabWidget; // extends xRecord.
    ttsBegin;
    while select
        from tabGalaxy
            where tabGalaxy .isTrusted == 0
    {
        delete_from tabWidget
            where tabWidget .GalaxyRecId ==
                tabGalaxy .RecId;
    }
    ttsCommit;
}

// This is the old way of using the delete method and inner joins.
// The following delete method is inefficient. It issues a
// separate SQL delete call to the database server for each record.
static void DeleteInnerJoin2aJob(Args _args)
{
    MyWidgetTable tabWidget; // extends xRecord.
    ttsBegin;
    while select
        forUpdate
        tabWidget
        join tabGalaxy
            where
                tabWidget .GalaxyRecId == tabGalaxy .RecId
                && tabGalaxy .isTrusted == 0
    {
        tabWidget .delete();
    }
    ttsCommit;
}
```
### Example: A delete operation that uses the notexists join keyword

You can use the **notexists join** keyword pair in a **delete\_from** statement. The **delete\_from** statements in the following example are efficient. The **notexists join** clause enables the **delete\_from** statement to delete a specific set of rows. In this example, the **delete\_from** statement removes all parent-order header rows that there are no child-order line rows for. You can also use the **exists join** clause on the **delete\_from** statement.

```X++
static void DeleteFromNotexists3bJob(Args _args)
{
    GmTabOrderHeader tabOHeader;
    GmTabOrderLine tabOLine;
    AddressState tabAddressState;
    str 127 sOH_Info;
    str 127 sOL_Data;
    int64 i64OHRecId;
    delete_from tabOLine;
    delete_from tabOHeader;
    // Inserts into parent table.
    sOH_Info = "Albert needs tires.";
    insert_recordset tabOHeader
        (OH_Info)
        select firstOnly sOH_Info from tabAddressState;
    sOH_Info = "Benson wants plastic.";
    insert_recordset tabOHeader
        (OH_Info)
        select firstOnly sOH_Info from tabAddressState;
    // Obtain a OrderHeader RecId,
    // use it to insert one child row.
    sOL_Data = "4 re-treads.";
    while select firstOnly tabOHeader
        order by OH_Info
        where tabOHeader .OH_Info like "A*"
    {
        i64OHRecId = tabOHeader .RecId;
        insert_recordset tabOLine
            (OL_Data ,OrderHeaderRecId)
            select firstOnly
                sOL_Data ,i64OHRecId
                from tabAddressState;
        break;
    }
    // Before the delete notexists.
    // Display all parent, and then all child rows.
    while select tabOHeader
        order by OH_Info
    {
        info(strFmt(
            "Before: OHeader:  OH_Info==%1 , RecId==%2"
            ,tabOHeader .OH_Info ,tabOHeader .RecId
            ));
    }
    while select tabOLine
        order by OL_Data
    {
        info(strFmt(
            "Before: OLine:  OL_Data==%1 , OrderHeaderRecId==%2"
            ,tabOLine .OL_Data ,tabOLine .OrderHeaderRecId
            ));
    }
    // Delete_From NotExists Join, to remove from the
    // parent table all order headers without children.
    delete_from tabOHeader
        notexists join tabOLine
            where tabOHeader .RecId ==
                tabOLine .OrderHeaderRecId;
    info(strFmt
        ("%1 is the number of childless OHeader records deleted."
        ,tabOHeader.rowCount()));
    // After the delete notexists.
    // Display all parent, and then all child rows.
    info("- - - - - - - - - - - - - - -");
    while select tabOHeader
        order by OH_Info
    {
        info(strFmt(
            "After: OHeader:  OH_Info==%1 , RecId==%2"
            ,tabOHeader .OH_Info ,tabOHeader .RecId
            ));
    }
    while select tabOLine
        order by OL_Data
    {
        info(strFmt(
            "After: OLine:  OL_Data==%1 , OrderHeaderRecId==%2"
            ,tabOLine .OL_Data ,tabOLine .OrderHeaderRecId
            ));
    }

/**************  Actual Infolog output
Message (12:54:14 pm)
Before: OHeader:  OH_Info==Albert needs tires. , RecId==5637144608
Before: OHeader:  OH_Info==Benson wants plastic. , RecId==5637144609
Before: OLine:  OL_Data==4 re-treads. , OrderHeaderRecId==5637144608
1 is the number of childless OHeader records deleted.
- - - - - - - - - - - - - - -
After: OHeader:  OH_Info==Albert needs tires. , RecId==5637144608
After: OLine:  OL_Data==4 re-treads. , OrderHeaderRecId==5637144608
**************/
}
```

## Maintain fast SQL operations
There are situations where record set–based operations can be converted to slower record-by-record operations. The following information identifies these situations.


### Non-SQL tables

| Operation | Can be converted |
|---|---|
|DELETE_FROM|Yes|
|UPDATE_RECORDSET|Yes|
|INSERT_RECORDSET|Yes|
|ARRAY_INSERT|Yes|
|Use this setting for overrides|Not applicable|

### Delete actions

| Operation | Can be converted |
|---|---|
|DELETE_FROM|Yes|
|UPDATE_RECORDSET|No|
|INSERT_RECORDSET|No|
|ARRAY_INSERT|No|
|Use this setting for overrides|**skipDeleteActions**|

### The database log is enabled.

| Operation | Can be converted |
|---|---|
|DELETE_FROM|Yes|
|UPDATE_RECORDSET|Yes|
|INSERT_RECORDSET|Yes|
|ARRAY_INSERT|No|
|Use this setting for overrides|**skipDatabaseLog**|

### Overridden method

| Operation | Can be converted |
|---|---|
|DELETE_FROM|Yes|
|UPDATE_RECORDSET|Yes|
|INSERT_RECORDSET|Yes|
|ARRAY_INSERT|Yes|
|Use this setting for overrides|**skipDataMethods**|

### Alerts are set up for the table.

| Operation | Can be converted |
|---|---|
|DELETE_FROM|Yes|
|UPDATE_RECORDSET|Yes|
|INSERT_RECORDSET|Yes|
|ARRAY_INSERT|No|
|Use this setting for overrides|**skipEvents**|

### The ValidTimeStateFieldType property on a table isn't equal to None.

| Operation | Can be converted |
|---|---|
|DELETE_FROM|Yes|
|UPDATE_RECORDSET|Yes|
|INSERT_RECORDSET|Yes|
|ARRAY_INSERT|Yes|
|Use this setting for overrides|Not applicable|


You can use the settings that are shown for **Use this setting for overrides** to explicitly skip or ignore one or more factors that adversely affect performance. If, for some reason, one of the previously mentioned SQL operations is downgraded to a record-by-record operation, all the **skip\*** settings are also ignored. For example, in the following code, the **insert** method on the myTable table is run, even though it's explicitly stated that this method should be skipped if a container or memo field is defined for myTable.

```X++
public void tutorialRecordInsertList()
{
    MyTable myTable;
    RecordInsertList insertList = new RecordInsertList(
        myTable.TableId,
        True);
    int i;
    for ( i = 1; i <=  100; i++ )
    {
        myTable.value = i;
        insertList.add(myTable);
    }
    insertList.insertDatabase();
}
```



