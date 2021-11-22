---
title: Insert data
description: This topic describes how to insert data into tables by using X++.
author: tonyafehr
ms.date: 06/16/2020
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
ms.dyn365.ops.version: AX 7.0.0
ms.search.validFrom: 2016-02-28

---

# Insert data

[!include [banner](../../includes/banner.md)]

You can use SQL statements, either interactively or in source code, to insert one or more rows into tables that are stored in the database.

+ **[insert method](#insert-method)** – Insert one row at a time.
+ **[doInsert method](#do-insert-method)** – Insert one row at a time.
+ **[insert\_recordset statement](#insert-recordset-statement)** – Copy multiple records directly from one or more tables into another table in one database trip.
+ **[RecordInsertList.insertDatabase](/dotnet/api/dynamics.ax.application#method-insertdatabase)** – Insert multiple rows at the same time in one database trip. Use this construct when you don't have to sort the data.
+ **[RecordSortedList.insertDatabase](/dotnet/api/dynamics.ax.application#method-insertdatabase)** – Insert multiple rows at the same time in one database trip. Use this construct when you want a subset of data from a specific table, and you want that data to be sorted in an order that doesn't currently exist as an index.

**RecordSortedList**, **RecordInsertList**, and **insert\_recordset** let you insert multiple records. By using these methods, you reduce communication between the application and the database. Therefore, you help increase performance. In some situations, record set–based operations can fall back to record-by-record operations. For more information, see [Conversion of operations from set-based to record-by-record](xpp-data-perf.md).

## <a id="insert-method"></a>insert method

The **insert** method inserts one record at a time. It generates values for the **RecId** field and system fields, and then inserts the contents of the buffer (that is, the column values) into the database.

+ Don't use a **select** statement on the table variable before you call the **insert** method.
+ The **insert** method doesn't handle all the key field requirements and table dependencies. You must write code to handle them.

Here is how the **insert** method works:

+ Only the specified columns of the rows that have been selected by the query are inserted into the named table.
+ The columns of the table that is copied from and the columns of the table that is copied to must be type-compatible.
+ If the columns of both tables match in type and order, the column list can be omitted from the **insert** clause.

The following example inserts a new record into the CustGroup table. The **CustGroup** column of the new record is set to **41**. Other fields in the record will be blank.

```xpp
CustGroup custGroup;
ttsBegin;
custGroup.CustGroup = '41';
custGroup.insert();
ttsCommit;
```

To override the behavior of the **insert** method, use the **[doInsert](#do-insert-method)** method.

## <a id="do-insert-method"></a>doInsert method

The **doInsert** method generates values for the **RecId** field and other system fields, and then inserts the contents of the buffer into the database. Use this method when the **insert** method on the table must be bypassed.

> [!WARNING]
> A call to **doInsert** skips all logic, including database event handlers (for example **oninserting** and **oninserted**), chain-of-command **onInsert()**, and the **insert()** call itself. It's generally considered bad practice to use **doInsert**, and we don't recommend that you use it.

## <a id="insert-recordset-statement"></a>insert\_recordset statement

The **insert\_recordset** statement copies data directly from one or more source tables into one destination table in one server trip. It's faster to use **insert\_recordset** than an array insert (**RecordInsertList.insertDatabase** or **RecordSortedList.insertDatabase**). However, array inserts are more flexible if you want to handle the data before you insert it. Although **insert\_recordset** is a record set–based operator that performs operations on multiple records at a time, it can fall back to record-by-record operations in many situations. For more information, see [Conversion of operations from set-based to record-by-record](xpp-data-perf.md).

In the following syntax for the **insert\_recordset** statement, brackets (\[\]) indicate optional elements of the statement.

**insert\_recordset** *DestinationTable* **(** *ListOfFields* **)**

**select** *ListOfFields1* **from** *SourceTable* **\[ where** *WhereClause* **\]** 

**\[ join** *ListOfFields2* **from** *JoinedSourceTable* **\[ where** *JoinedWhereClause* **\]\]**

+ *ListOfFields* in the destination table must match the list of fields in the source tables. Data is transferred in the order in which it appears in the list of fields. Fields in the destination table that aren't present in the list of fields are assigned **0** (zero) values, as in other areas. System fields, such as **RecId**, are assigned transparently by the kernel in the destination table.
+ *WhereClause* and *JoinedWhereClause* are described in the *WhereClause* clause in the **[select](xpp-select-statement.md#where-keyword)** statement.

### insert\_recordset: Inserting data from another table

In this example, the **Value** column in the NameValuePair table is summed for each **Name** value. The results of the aggregation are stored in the ValueSumByName table.

```xpp
ValueSumByName valueSumName;
NameValuePair nameValuePair;

insert_recordset valueSumName (Name, ValueSum)
    select Name, sum(Value)
    from nameValuePair
    group by Name;
```

### insert\_recordset: Inserting data from variables

The following example shows that the **insert\_recordset** statement can insert variable data.

- Include the **firstonly** keyword to insert only one new record. If you omit **firstonly**, a record is inserted for each record in the CustTable table.
- Literals, such as **128** or **"this literal string"**, can't be used in the query as a source of data that is inserted.
- The columns in the source table don't have to correspond to the target table.

In this example, one new record is inserted into the NameValuePair table. This record has an **Id** value of **1**, a **Name** value of **Name1**, and a **Value** value of **1**.

```xpp
NameValuePair nameValuePair;
CustTable custTable;

int id_var = 1;
str name_var = 'Name1';
int value_var = 1;

insert_recordset nameValuePair (Id, Name, Value)
select firstonly id_var, name_var, value_var from custTable;
```

### insert\_recordset: Inserting data by using a join

The following example shows a join of three tables on an **insert\_recordset** statement that has a subselect. It also shows a **while select** statement that has a similar join. A variable is used to supply the inserted value for one column. The **str** variable must be declared, and it must have a length that is less than or equal to the maximum length of the corresponding database field.

In this example, there is an **insert\_recordset** statement for the tabEmplProj5 table. One of the target fields is named **Description**, and its data comes from the local **sDescriptionVariable** variable. The **insert\_recordset** statement succeeds even when the configuration key for the **Description** field is turned off. The system ignores both the **Description** field and the **sDescriptionVariable** variable. Therefore, this code provides an example of *configuration key automation*. Configuration key automation occurs when the system can automatically adjust the behavior of an **insert\_recordset** statement that inserts data into fields that the configuration key is turned off for.

```xpp
static void InsertJoin42Job(Args _args)
{
    GmTabDepartment tabDept2;
    GmTabEmployee tabEmpl3;
    GmTabProject tabProj4;
    GmTabEmployeeProject tabEmplProj5;
    str 64 sDescriptionVariable = "From variable.";
    delete_from tabEmplProj5;
    insert_recordset tabEmplProj5
        (  Description
        , EmployeeRecId
        , ProjectRecId
        )
    select sDescriptionVariable, RecId
    from tabEmpl3
        join tabDept2
            where tabEmpl3 .DepartmentGuid == tabDept2 .DepartmentGuid
        join RecId from tabProj4
            where tabDept2 .DepartmentGuid == tabProj4 .DepartmentGuid;
    info(strFmt("%1 == Number of rows inserted.", tabEmplProj5.rowCount()));        
    
    while select tabEmplProj5
        join tabEmpl3
            where tabEmplProj5.EmployeeRecId == tabEmpl3.RecId
        join tabProj4
            where tabEmplProj5.ProjectRecId == tabProj4.RecId
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

## Handling DuplicateKeyException exceptions

The following example shows how you can catch a **DuplicateKeyException** exception in the context of an explicit transaction. The exception is thrown when a call to **xRecord.insert** fails because the key value already exists. In the **catch** block, your code can either take corrective action or log the error for later analysis. Your code can then continue without losing all the pending work of the transaction. You can't catch a **DuplicateKeyException** exception that is caused by a set-based operation such as **insert\_recordset**.

This example depends on two tables: SourceTable and DestinationTable. Each table has one mandatory integer field. The fields are named **SourceKeyField** and **DestinationKeyField**, respectively. A unique index is defined on each key field. The SourceTable table must have at least one record in it.

```xpp
static void JobDuplicKeyException44Job(Args _args)
{
    SourceTable      sourceTable; // Must have at least one record.
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
        while select sourceTable 
            order by SourceKeyField asc
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


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
