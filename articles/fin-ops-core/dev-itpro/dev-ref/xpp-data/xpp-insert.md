---
# required metadata

title: Insert data
description: This topic describes how to insert data into tables by using X++.
author: robinarh
manager: AnnBe
ms.date: 12/02/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 150273
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.version: AX 7.0.0
ms.search.validFrom: 2016-02-28

---

# Insert data

[!include [banner](../includes/banner.md)]

You can use SQL statements, either interactively or within source code, to insert one or more rows into tables stored in the database. This topic describes the select statement withing source code. The options for inserting new rows are:

+ **insert method**: Used together with a `select for update` statement, **insert** inserts one row at a time.
+ **do_insert**: The **Table.do_insert** method inserts one row at a time.
+ **insert_recordset**: Inserts multiple rows at the same time.
+ **RecordInsertList**: Inserts multiple rows at the same time.
+ **RecordSortedList.insertDatabase**: Inserts multiple rows at the same time.

## insert method

The **insert** method of the query variable inserts one record at a time. The **insert** method generates values for the **RecId** field and system fields, and then inserts the contents of the buffer (the column values) into the database.


Here is how the **insert** method works:

+ Only the specified columns of the rows that have been selected by the query are inserted into the named table.
+ The columns of the table that is copied from and the columns of the table that is copied to must be type-compatible.
+ If the columns of both tables match in type and order, column list can be omitted from the **insert** clause.

> [!WARNING]
> Where is this other table that is copied from?

> [!WARNING]
> Only the specified columns are inserted, or unspecified columns are set to the default value? or blank (as specified in next section)?

To override the behavior of the **insert** method, use the [**doInsert**](#doInsert-method) method. 

### insert example

The following example inserts a new record into the **CustTable** table. The **AccountNum** column of the new record is set to **5000**, and the **Name** field is set to **MyCompany**. Other fields in the record will be blank.

```xpp
CustTable custTable;
ttsBegin;
select forUpdate custTable;
custTable.AccountNum = '5000';
custTable.insert();
ttsCommit;
```


## doInsert method

The **doInsert** method generates values for the **RecId** field and other system fields, and then inserts the contents of the buffer into the database. Use this method when the **insert** method on the table must be bypassed. In the following example, a new record is inserted. The **name** field of the record is set to **Tomas Richardson**, and the **value** field is set to **100**.

```xpp
ttsBegin;
myTable.name = 'Tomas Richardson';
myTable.value = 100;
myTable.doInsert();
ttsCommit;
```


## Transactional integrity
If steps aren't taken to help guarantee the integrity of transactions, data corruption could occur. At the very least, you might experience poor scalability with respect to concurrent users on the system. Two internal checking features help guarantee the integrity of transactions: the **forUpdate** check and the **tssLevel** check. A **forUpdate** check helps guarantee that a record can be updated or deleted only if it has first been selected for update. You can select a record for update by using either the **forUpdate** keyword in the **select** statement or the **selectForUpdate** method on tables. A **ttsLevel** check helps guarantee that a record can be updated or deleted only within the same transaction scope where it was selected for update. The following statements are used to help guarantee integrity:

-   **ttsBegin** – This statement marks the beginning of a transaction. It helps guarantee data integrity, and also helps guarantees that all updates that are done until the transaction ends (through **ttsCommit** or **ttsAbort**) are consistent (all or none).
-   **ttsCommit** – This statement marks the successful end of a transaction. It ends and commits a transaction. The Finance and Operations application helps guarantee that a transaction that has been committed will be performed according to intentions.
-   **ttsAbort** – This statement lets you explicitly discard all changes in the current transaction. In this case, the database is rolled back to the original state where nothing has been changed. Typically, you use this statement if you've detected that the user wants to break the current job. The **ttsAbort** statement helps guarantee that the database is consistent.

Usually, it's a better idea to use exception handling instead of **ttsAbort**. The **throw** statement automatically aborts the current transaction. As the following example shows, statements between **ttsBegin** and **ttsCommit** can include one or more transaction blocks. In these cases, nothing is actually committed until the successful exit from the final **ttsCommit** statement.

```X++
ttsBegin;
    // Some statements.
ttsBegin;
    // More statements.
ttsCommit;
ttsCommit;
```

The following example selects a set of records and updates the **NameAlias** field.

```X++
Custtable custTable;
ttsBegin;
select forUpdate custTable where custTable.AccountNum == '4000';
custTable.NameAlias = custTable.Name;
custTable.update();
ttsCommit;
```

### Example of code that is rejected by the two transaction integrity checks

In this example, the first failure occurs because the **forupdate** keyword is missing. The second failure occurs because the transaction scope of the update differs from the transaction scope where the record was selected for update in **ttsCommit**.

```X++
ttsBegin;
select myTable; // Rejected by the forUpdate check.
mytable.myField = 'xyz';
myTable.update();
ttsCommit;
ttsBegin;
select forUpdate * from myTable;
myTable.myField = 'xyz';
ttsCommit;
...
ttsBegin;
myTable.update(); // Rejected by the ttsLevel check.
ttsCommit;
```

## Speeding up SQL operations
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


## Handle a DuplicateKeyException

The following example shows how you can catch a **DuplicateKeyException** exception in the context of an explicit transaction. The exception is thrown when a call to **xRecord.insert** fails because key value already exists. In the **catch** block, your code can either take corrective action or log the error for later analysis. Your code can then continue without losing all the pending work of the transaction. You can't catch a duplicate key exception that is caused by a set-based operation such as **insert\_recordset**. This example depends on two tables: **SourceTable** and **DestinationTable**. Both tables have one mandatory integer field. These fields are named **SourceKeyField** and **DestinationKeyField**, respectively. A unique index is defined on each key field. The TableNumberA table must have at least one record in it.

```xpp
static void JobDuplicKeyException44Job(Args _args)
{
    SourceTable sourceTable; // Must have at least one record.
    DestinationTable destinationTable;
    int countTries = 0;
    int numberAdjust = 0;
    int newKey;
    int inote;
    container notes;
    
    // Empty the destination table.
    delete_from destinationTable;

    // Copy all the records from SourceTable to DestinationTable
    insert_recordset destinationTable (destinationKeyField)
        select SourceKeyField from sourceTable order by SourceKeyField asc;

    // Copy the records from SourceTable to DestinationTable, one at a time.
    // This immediately throws a DuplicateKeyException.
    ttsBegin;
    try
    {
        countTries++;
        notes += strFmt("Inside the try block, try count is %1.", countTries);
        while select * from sourceTable order by SourceKeyField asc
        {
            destinationTable.clear();
            newKey = sourceTable.SourceKeyField + numberAdjust;
            destinationTable.DestinationKeyField = newKey;
            notes += strFmt("%1 is the key to be tried." , newKey);
            destinationTable.insert();
            notes += "Success: .insert()";
        }
        ttsCommit;
    }
    catch (Exception::DuplicateKeyException, destinationTable) // Table is optional.
    {
        notes += "Inside the catch block.";
        notes += 'Error: ' + infolog.text().strReplace('\n', '');
        if (countTries <= 1)
        {
            notes += "Will issue retry.";
            numberAdjust = 1;
            retry; // Erases Infolog.
        }
        else
        {
            notes += "Aborting the transaction.";
            ttsAbort;
        }
    }

    for (inote = 1; inote <= conLen(notes); inote++)
    {
        info(conPeek(notes, inote));
    }
}

/* Output
    ---- Inside the try block, try count is 1.
    ---- 11 is the key to be tried.
    ---- Inside the catch block.
    Cannot create a record in DestinationTable (DestinationTable).
    The record already exists.
    ---- Will issue retry.
    ---- Inside the try block, try count is 2.
    ---- 12 is the key to be tried.
    ---- .insert() successful.
*/
```
