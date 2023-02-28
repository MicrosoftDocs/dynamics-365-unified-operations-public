---
title: Select statement
description: This article describes the select statement in the X++ language.
author: josaw1
ms.date: 08/27/2021
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Select statement

[!include [banner](../../includes/banner.md)]

The **select** statement fetches or manipulates data from the database.

+ All **select** statements use a table variable to fetch records. This variable must be declared before a **select** statement can be run.
+ The **select** statement fetches only one record, or field. To fetch or traverse multiple records, you can use the **next** statement or the **[while select](xpp-while-select.md)** statement.

    + The **next** statement fetches the next record in the table. If no **select** statement precedes the **next** statement, an error occurs. If you use a **next** statement, don't use the **firstOnly** find option.
    + It's more appropriate to use a **while select** statement to traverse multiple records.

+ The results of a **select** statement are returned in a table buffer variable.
+ If you use a field list in the **select** statement, only those fields are available in the table variable.

## Select example

The following example fetches all the columns in the first row of the CustTable table and prints the value in the **AccountNum** column of that row.

```xpp
CustTable custTable;
select * from custTable;
info("AccountNum: " + custTable.AccountNum);
```

For more examples of data selection, see [Select data](xpp-select.md).

## Insert example

The following example inserts a new record into the CustTable table. The **AccountNum** column of the new record is set to **2000**, and the **CustGroup** column is set to **1**. Other fields in the record will be blank.

```xpp
ttsBegin;
    CustTable custTable;
    select forUpdate custTable;
    custTable.AccountNum = '2000';
    custTable.CustGroup = '1';
    custTable.insert();
ttsCommit;
```

For more examples of data insertion, see [Insert data](xpp-insert.md).

## Update example

The following example selects the CustTable table for update. Only records where the value of the **AccountNum** field equals **2000** are updated. Because there is no call to **next**, and this example doesn't use a **select while** statement, only one record is updated. The value of the **CreditMax** field is changed to **5000**.

```xpp
ttsBegin;
    CustTable custTable;
    select forUpdate custTable
        where custTable.AccountNum == '2000';
    custTable.CreditMax = 5000;
    custTable.update();
ttsCommit;
```

For more examples of data updates, see [Update data](xpp-update.md).

## Delete example

In the following example, all records in the CustTable table where the **AccountNum** field equals **2000** are deleted from the database. One record is deleted at a time.

```xpp
ttsBegin;
    CustTable custTable;
    while select forUpdate CustTable
        where custTable.AccountNum == '2000'
    {
        custTable.delete();
    }
ttsCommit;
```

For more examples of data deletion, see [Delete data](xpp-select.md).

## Syntax of the select statement

The following symbols are used in the syntax:

+ **\[\]** – Brackets enclose an optional element.
+ **{}** – Braces enclose an element that can be included zero or more times.
+ **\+** – A plus sign indicates an element that can be included one or more times.
+ **|** – A bar indicates options.

| Symbol                | &nbsp;  | Expression |
|-----------------------|---|------------|
| *SelectStatement*     | = | **select** *Parameters* |
| *Parameters*          | = | { *FindOption* } \[ *FieldList* **from** \] *TableBufferVariable* \[ *IndexClause* \] \[ *Options* \] \[ *WhereClause* \] \[ *JoinClause* \] |
| *FindOption*          | = | **crossCompany** \[**:** *ContainerVariable*\] \| **reverse** \| **firstFast** \| *FirstOption* \| **forUpdate** \| **noFetch** \| *ForceOption* \| **forceSelectOrder** \| **forceNestedLoop** \| *LockOption* \| **repeatableRead** \| **validTimeState** |
| *FirstOption*         | = | **firstOnly** \| **firstOnly10** \| **firstOnly100** \| **firstOnly1000** |
| *LockOption*          | = | **optimisticLock** \| **pessimisticLock** |
| *ForceOption*         | = | **forcePlaceholders** \| **forceLiterals** |
| *FieldList*           | = | { *Field* } \| **\*** |
| *Field*               | = | *Aggregate* **(** *FieldIdentifier* **)** \| *FieldIdentifier* |
| *Aggregate*           | = | **sum** \| **avg** \| **minof** \| **maxof** \| **count** |
| *Options*             | = | *OrderClause* \| *IndexClause* |
| *OrderClause*         | = | \[*OrderBy* \[*GroupBy*\]\] \| \[*GroupBy* \[*OrderBy*\]\] |
| *OrderBy*             | = | **order** \[**by**\] *FieldOrder* {**,** *FieldOrder* } |
| *GroupBy*             | = | **group** \[**by**\] *FieldOrder* {**,** *FieldOrder* } |
| *FieldOrder*          | = | *FieldIdentifier* \[ **asc** \| **desc** \] |
| *IndexClause*         | = | **index** *IndexName* \| **index hint** *IndexName* |
| *WhereClause*         | = | **where** *Expression* *InClause* |
| *InClause*            | = | **in** *List* |
| *JoinClause*          | = | \[**exists** \| **notexists** \| **outer** \] **join** *Parameters* |
| *ContainerVariable*   | = | A container. |
| *Expression*          | = | An expression. |
| *TableBufferVariable* | = | The variable name for the results. |
| *FieldIdentifier*     | = | The name of a field in the table. |
| *IndexName*           | = | The name of an index for a table. |
| *List*                | = | An array of values. |

## Aggregate functions

The aggregate functions perform calculations on a single field over a group of records.

+ The result is returned in the field that you perform the aggregate function over.
+ The fields in the results are the aggregate values and the fields in the **group by** clause.
+ You can count, average, or sum only integer and real fields.
+ In cases where the **sum** function will return **null**, no rows are returned.

### Differences between X++ and SQL

In industry-standard SQL, a database query can contain aggregate functions. Examples include **count(RecID)** and **sum(columnA)**. When an aggregate function is used, but no rows match the **where** clause, a row must be returned to hold the result of the aggregates. The row that is returned shows the value **0** (zero) for the **count** function and **null** for the **sum** function. X++ doesn't support the concept of **null** values for the database. Therefore, in cases where the **sum** function will return **null**, no row is returned to the user. Additionally, every data type has a specific value that is treated as a **null** value in some circumstances.

## Grouping and ordering the query results

A query can have multiple **group by** clauses, but the fields can be qualified by a table name in only one **group by** clause. We recommend that you use table name qualifiers. The **order by** clause follows the same syntax patterns as **group by**. Both clauses, if they are provided, must appear after the **join** (or **from**) clause, and both must appear before any **where** clause that exists on the same **join** clause. We recommend that all **group by**, **order by**, and **where** clauses appear immediately after the last **join** clause. The following example shows a **group by** clause where a field is qualified by a table name.

```xpp
CustTable custTable;
CustGroup custGroup;
struct groupSummary = new struct("int CustomerCount; str CustGroup");

while select count(CreditMax) from custTable
    join custGroup
    order by custGroup.Name
    group by custGroup.CustGroup
    where custTable.CustGroup == custGroup.CustGroup
        && custGroup.Name like "*Days*"
{

    groupSummary.value("CustomerCount", custTable.CreditMax);
    groupSummary.value("CustGroup", custGroup.CustGroup);
    info(groupSummary.toString());
}

// Example output:
// (CustomerCount:1; CustGroup:"1")
// (CustomerCount:3; CustGroup:"2")
```

## Join tables

The following example shows how an inner join can be performed as part of a **select** statement. The example also shows an **order by** clause where each field is qualified by a table name. Therefore, you can use just one **order by** clause to control how the retrieved records are sorted.

```xpp
CustTable custTable;
CustGroup custGroup;
struct output = new struct("int AccountNum; str CustGroup");

while select AccountNum from custTable
    join Name from custGroup
    order by custGroup.Name, custTable.AccountNum
    where custTable.CustGroup == custGroup.CustGroup
{
    info(custGroup.Name + ': ' + custTable.AccountNum);
}

// Example output:
// Days1: 6000
// Days1: 6001
// Days2: 5000
```

## Using where, order by, and index hint together in a query

You use the **order by** keyword in **select** statements to order the data that is returned. Use the **index hint** keyword to specify the index that should be used in the query, and to sort the selected records in the manner that is defined by the index. Indexes optimize the selection of records. To select records in a specific order, combine the **index hint** keyword with an **order by** expression. If you want the output to be sorted in reverse order, use the **reverse** keyword. If a table index has been disabled (that is, if the index's **Enabled** property is set to **No**), the **select** statement that references the index is still valid. However, the database can't use the index as a hint to sort the data, because the index doesn't exist in the database. The following table shows how to use the **index hint** and **order by** keywords in **select** statements.

| Task | select statement |
|------|-----|
| Select records when the order isn't significant. | select .. where ... |
| Select records when the order is significant. | select .. order by ... where ... |
| Select records, and force a specific index to be used. | select .. index hint ... where ... |
| Select records when the order is significant, and force a specific index to be used. | select .. index hint ... order by ... where ... |

The following example shows how to select transactions from the SalesTable table, based on a range of customers and due dates.

```xpp
SalesTable salesTable;
select salesTable
    index hint CustIdx
    order by CustAccount
    where
        salesTable.CustAccount >= '3000'
        && salesTable.CustAccount <= '4000'
        && salesTable.FixedDueDate >= 12\12\2004
        && salesTable.FixedDueDate <= 05\05\2009;
```

## asc keyword

The **asc** keyword is an option on the **order by** or **group by** clause. It specifies an ascending sort order. If neither **asc** nor **desc** is specified, the sort is ascending.

```xpp
CustTable custTable;
select * from custTable
    order by Value asc;
```

## avg keyword

The **avg** keyword returns the average of the fields.

```xpp
CustTable custTable;
select avg(Value) from custTable;
info(int642Str(custTable.Value));
```

## count keyword

The **count** keyword returns the number of records.

```xpp
CustTable custTable;
int64 iCountRows;
select count(RecID) from custTable;
iCountRows = custTable.RecID;
info('Rows: ' + int642Str(iCountRows));
```

## crossCompany keyword

The **crossCompany** keyword returns data for all companies that the user is authorized to read from. You can add a container to reduce the number of companies that are involved. The following example returns data for companies that the user is authorized to read from. Results are limited to the **dat** and **dmo** companies.

```xpp
CustTable custTable;
container conCompanies = ['dat','dmo'];
select crossCompany :conCompanies
    * from custTable;
```

### crossCompany clause can contain arbitrary expressions

The **crossCompany** clause can be used on **select** statements to indicate the companies that the search statement should take into account. The syntax has been enhanced to allow arbitrary expressions (of type container) instead of a single identifier, which is a variable of type container.

This code examples creates a container with the companies.

```xpp
private void SampleMethod()
{
    MyTable t;
    container mycompanies = ['dat', 'dmo'];
    select crosscompany: mycompanies t;
}
```

This code uses an expression instead of the variable.

```xpp
private void SampleMethod()
{
    MyTable t;
    container mycompanies = ['dat', 'dmo'];
    select crosscompany: (['dat'] + ['dmo']) t;
}
```

## desc keyword

The **desc** keyword is an option on the **order by** or **group by** clause. It specifies a descending sort order. If neither **asc** nor **desc** is specified, the sort is ascending.

```xpp
CustTable custTable;
select * from custTable
    order by Value desc;
```

## exists keyword

The **exists** keyword is a method that returns a Boolean value and a **join** clause.

```xpp
CtrTable ctrTable;
CustTable custTable;
while select AccountNum, Value from custTable
    order by AccountNum
    exists join * from ctrTable
    where (ctrTable.AccountNum == custTable.AccountNum)
{
}
```

## firstFast keyword

The **firstFast** keyword is a priority hint. The first row appears more quickly, but the total return time for this option might be slower. The **firstFast** hint is automatically issued from all pages.

The following code example quickly returns the first row.

```xpp
CustTable custTable;
select firstFast custTable
    order by AccountNum;
```

## firstOnly, firstOnly10, firstOnly100, and firstOnly1000 keywords

The **firstOnly** keywords speed up the fetch by returning a limited number of rows. When you include **firstOnly** in your query, the runtime returns a table buffer. When you omit **firstOnly**, the runtime allocates an object that can iterate over records. From a performance perspective, you should use **firstOnly** only when your intent is to fetch the first record.

| Keyword       | Description                |
|---------------|----------------------------|
| firstOnly     | Return only the first row. |
| firstOnly10   | Return 10 rows.            |
| firstOnly100  | Return 100 rows.           |
| firstOnly1000 | Return 1,000 rows.         |

The following code example returns only the first row of the results.

```xpp
CustTable custTable;
select firstOnly custTable
    index hint AccountIdx
    where custTable.AccountNum == '5000';
```

## forceLiterals keyword

The **forceLiterals** keyword instructs the kernel to reveal the actual values that are used in **where** clauses to the Microsoft SQL Server database at the time of optimization. The **forceLiterals** and **forcePlaceholders** keywords are mutually exclusive. For more information, see the [forcePlaceholders keyword](#forceplaceholders-keyword) section.

> [!WARNING]
> You should not use the **forceLiterals** keyword in **select** statements, because it could expose code to an SQL injection security threat.

## forceNestedLoop keyword

The **forceNestedLoop** keyword forces the SQL Server database to use a nested-loop algorithm to process a particular SQL statement that contains a join algorithm. Therefore, a record from the first table is fetched before any records from the second table are fetched. Typically, other join algorithms, such as hash joins and merge joins, are considered. This keyword is often combined with the **forceSelectOrder** keyword.

```xpp
CustGroup custGroup;
CustTable custTable;

while select forceNestedLoop custGroup
    join custTable
    where custGroup.CustGroup == custTable.CustGroup
{
    Info(custTable.CustGroup);
}
```

## forcePlaceholders keyword

The **forcePlaceholders** keyword instructs the kernel **not** to reveal the actual values that are used in **where** clauses to the SQL Server database at the time of optimization. By default, this behavior is used in all statements that aren't **join** statements. The advantage of using this keyword is that the kernel can reuse the access plan for similar statements that have other search values. The disadvantage is that, although the access plan is computed, the fact that data distribution might be uneven isn't considered. The access plan is an on-average access plan. The **forcePlaceholders** and **forceLiterals** keywords are mutually exclusive.

The following example iterates through the **CustGroup** table that is joined with the **CustTable** table.

```xpp
CustGroup custGroup;
CustTable custTable;

while select forcePlaceholders custGroup
    join custTable
    where custGroup.CustGroup == custTable.CustGroup
{
    Info(custTable.CustGroup);
}
```

## forceSelectOrder keyword

The **forceSelectOrder** keyword forces the SQL Server database to access the tables in a join in the specified order. If two tables are joined, the first table in the statement is always accessed first. This keyword is often combined with the **forceNestedLoop** keyword.

The following example joins the CustGroup and CustTable tables on the **CustGroup** field.

```xpp
CustGroup custGroup;
CustTable custTable;

while select forceSelectOrder custGroup
    join custTable
    where custGroup.CustGroup == custTable.CustGroup
{
    Info(custTable.CustGroup);
}
```

## forUpdate keyword

The **forUpdate** keyword selects records for update only. Depending on the underlying database, the records might be locked for other users. The following example selects the **CreditMax** column in the CustTable table for update, for the record where the **AccountNum** value is **2000**.

```xpp
ttsBegin;
    CustTable custTable;
    select forUpdate custTable
        where custTable.AccountNum == '2000';
    custTable.CreditMax = 5000;
    custTable.update();
ttsCommit;
```

## group by keyword

The **group by** keyword instructs the database to group selected records by fields.

```xpp
CustTable custTable;
while select sum(CreditMax) from custTable
    group by CustGroup
{
    info(custTable.CustGroup + ' ' + int642Str(custTable.CreditMax));
}
```

## in keyword

The **in** keyword filters rows where a value is contained in a list.

If you don't use the **in** keyword, the code that you write will resemble the following example.

```X++
// This code doesn't use the in keyword.
private CostAmountStdAdjustment calcCostAmountStdAdjustment()
{
    InventSettlement inventSettlement;

    select sum(CostAmountAdjustment) from inventSettlement
        where inventSettlement.TransRecId == this.RecId
            && inventSettlement.Cancelled == NoYes::No
            && (inventSettlement.OperationsPosting == LedgerpostingType::purchStdProfit
                || inventSettlement.OperationsPosting == LedgerpostingType::purchStdLoss
                || inventSettlement.OperationsPosting == LedgerpostingType::InventStdProfit
                || inventSettlement.OperationsPosting == LedgerpostingType::InventStdLoss);

    return inventSettlement.CostAmountAdjustment;
}
```

If you use the **in** keyword, the code that you write will resemble the following example.

```X++
// This code uses the in keyword.
private CostAmountStdAdjustment calcCostAmountStdAdjustment()
{
    InventSettlement inventSettlement;
    container ledgerPostingTypes = this.ledgerPostingTypesForCostAmountStdAdjustmentCalculation();

    select sum(CostAmountAdjustment) from inventSettlement
        where inventSettlement.TransRecId == this.RecId
            && inventSettlement.Cancelled == NoYes::No
            && inventSettlement.OperationsPosting in ledgerPostingTypes;

    return inventSettlement.CostAmountAdjustment;
}

protected container ledgerPostingTypesForCostAmountStdAdjustmentCalculation()
{
return [
    LedgerPostingType::purchStdProfit,
    LedgerPostingType::PurchStdLoss,
    LedgerPostingType::InventStdProfit,
    LedgerPostingType::InventStdLoss
];
}
```

## index keyword

The **index** keyword instructs the database to sort the selected records as specified by the index.

```xpp
CustTable custTable;
while select AccountNum, Value from custTable
    index AccountIdx
{
    Info(custTable.AccountNum +  ": " + int642Str(custTable.Value));
}
```

## index hint keyword

The **index hint** keyword forces SQL Server to use a specific index. Using **index hint** keyword, means you take away the control of which index to use from the Query Optimizer. An incorrect index hint can greatly affect performance. Index hints should be applied only to SQL statements that don't have dynamic **where** clauses or **order by** clauses, and where the effect of the hint can be verified.

Before you can use **index hint** in queries, you must call **allowIndexHint(true)** on the table. The default behavior for **index hint** is **false**, and the hint is ignored.

> [!WARNING]
> You should use **index hint** sparingly and with caution, and only when you can be sure that it improves performance. The **index hint** keyword and API let you pass the correct hints when they are required. If you're ever in doubt, avoid using **index hint**.

In the following example, the **AccountIdx** index is used to sort the records in the query on the CustTable table.

```xpp
str _accountNum = '111';
CustTable custTable;
custTable.allowIndexHint(true);

while select forUpdate custTable
    index hint AccountIdx
    where custTable.AccountNum == _accountNum
{
}
```

## join keyword

The **join** keyword is used to join tables on a column that is shared by both tables. The join criteria are specified in a **where** clause, because there is no **on** keyword, such as is found in SQL. This keyword reduces the number of SQL statements that are required if you want to loop through a table and update transactions in a related table. For example, you process 500 records in a table and want to update related records in another table. If you use a nested **while select**, there will be 501 trips to the database. However, if you use a **join**, there will be just one trip to the database.

```xpp
CustTable custTable;
CustGroup custGroup;
int totalCredit;

while select custGroup
    join custTable
    where custGroup.CustGroup == custTable.CustGroup
{
    totalCredit += custTable.CreditMax;
}
}
```

## maxof keyword

The **maxof** keyword returns the maximum of the fields.

```xpp
CustTable custTable;
select maxof(CreditMax) from custTable;
info(int642Str(custTable.Value));
```

## minof keyword

The **minof** keyword returns the minimum of the fields.

```xpp
CustTable custTable;
select minof(CreditMax) from custTable;
info(int642Str(custTable.Value));
```

## noFetch keyword

The **noFetch** keyword indicates that no records should be fetched now. Typically, this keyword is used when the result of the **select** statement is passed on to another application object, such as a query that performs the actual fetch.

The following example creates a query variable but doesn't fetch the records.

```xpp
CustTable custTable;
select noFetch custTable
    order by AccountNum;
```

## notExists keyword

The **notExists** keyword is selected only if there are no posts.

``` xpp
CustTable custTable;
CtrTable ctrTable;

while select AccountNum, Value from custTable
    order by AccountNum
    notExists join * from ctrTable
    where (ctrTable.AccountNum == custTable.AccountNum)
{
}
```

## optimisticLock keyword

The **optimisticLock** keyword forces a statement to run by using optimistic concurrency control, even if a different value is set on the table.

```xpp
CustTable custTable;
select optimisticLock custTable
    where custTable.AccountNum > '1000';
```

## order by keyword

The **order by** keyword instructs the database to sort the selected records by the fields in the **order by** list. The keyword **by** is optional.

```xpp
CustTable custTable;
select * from custTable
    order by accountNum desc
    where custTable.AccountNum > '100';
info("AccountNum: " + custTable.AccountNum);
```

The following example prints the highest **AccountNum** value in the CustTable table.

```xpp
CustTable custTable;
select reverse custTable
    order by accountNum;
info("AccountNum: " + custTable.AccountNum);
```

## outer keyword

The **outer** keyword returns all rows from the table that is named first, even rows that have no match in the table that is named second. This join is a left outer join. Default values are substituted for any data that could not be obtained from a matching row in the other joined table.

There is no **left** keyword, and there is no right outer join.

For an inner join, the behavior if you filter on an **on** clause is the same as the behavior if you filter on the **where** clause.

```xpp
CustTable custTable;
CustGroup custGroupTable;

while select CustGroup from custGroupTable
    order by CustGroup
    outer join * from custGroupTable
    where custTable.CustGroup == custGroupTable.CustGroup
{
    Info(custTable.CustGroup + ', ' + custGroupTable.Name);
}
```

The following example is based on two tables. The field types and example data are included. There is a one-to-many relationship between the SalesOrder parent table and the SalesOrderLine child table. For each row in the SalesOrder table, there are 0 (zero) or more rows in the SalesOrderLine table. There are two rows in the SalesOrder table.

| SalesOrderID (integer, primary key) | DateAdded (date) |
|-------------------------------------|------------------|
| 1                                   | 2010-01-01       |
| 2                                   | 2010-02-02       |

The SalesOrderLine table contains a foreign key field that is named **SalesOrderID**. This field references the primary key column of the SalesOrder table. A **SalesOrderID** value of **2** doesn't occur in the data for the SalesOrderLine table.

| SalesOrderLineID (string, primary key) | Quantity (integer) | SalesOrderID (integer, foreign key) |
|----------------------------------------|--------------------|-------------------------------------|
| AA                                     | 32                 | 1                                   |
| BB                                     | 67                 | 1                                   |
| CC                                     | 66                 | 1                                   |

The following code has a **select** statement that reads the two tables. The **select** statement includes a left **outer join** clause. Both the join criteria and the data filter are on the **where** clause. The output from the code is also shown. The second record in the output has a **SalesOrderID** value of **2**. However, that value isn't present in the SalesOrderLine table. Therefore, some of the fields in the second record have default values: **0** for an integer and a zero-length string for a string.

```xpp
SalesOrder recSalesOrder;
SalesOrderLine recSalesOrderLine;
struct struct4 = new struct
    ("int SalesOrderID;"
    + "date DateAdded;"
    + "str SalesOrderLineID;"
    + "int Quantity"
    );
while select *
    from
        recSalesOrder
        outer join recSalesOrderLine
    where
        recSalesOrder.SalesOrderID == recSalesOrderLine.SalesOrderID
        && recSalesOrderLine.Quantity == 66
{
    struct4.value("SalesOrderID", recSalesOrder.SalesOrderID);
    struct4.value("DateAdded", recSalesOrder.DateAdded);
    struct4.value("SalesOrderLineID", recSalesOrderLine.SalesOrderLineID);
    struct4.value("Quantity", recSalesOrderLine.Quantity);
    info(struct4.toString());
}

// Example output:
// (SalesOrderID:1; DateAdded:2010/1/1; SalesOrderLineID:"CC"; Quantity:66)
// (SalesOrderID:2; DateAdded:2010/2/2; SalesOrderLineID:""; Quantity:0)
```

## pessimisticLock keyword

The **pessimisticLock** keyword forces a statement to run by using pessimistic concurrency control, even if a different value is set on the table.

```xpp
CustTable custTable;
select pessimisticLock custTable
    where custTable.AccountNum > '1000';
```

## repeatableRead keyword

This **repeatableRead** keyword specifies that the current transaction must be completed before other transactions can modify data that has been read by logic inside the current transaction. An explicit transaction is completed at either **ttsAbort** or the outermost **ttsCommit**. For a standalone **select** statement, the transaction duration is the duration of the **select** command. However, the database sometimes enforces the equivalent of **repeatableRead** in individual **select** statements, even if this keyword doesn't appear in your code. (The behavior depends on the method that the database uses to determine whether it should scan the tables.) For more information, see the documentation for the underlying relational database product.

## reverse keyword

The **reverse** keyword returns records in reverse order.

```xpp
CustTable custTable;
select reverse custTable
    order by AccountNum;
```

## sum keyword

The **sum** keyword returns the sum of the fields. It can be used to sum all accounts, order lines, and so on.

```xpp
CustTable custTable;
select sum(CreditMax) from custTable;
info(int642Str(custTable.Value));
```

## validTimeState keyword

The **validTimeState** keyword selects rows from a table where the **ValidTimeStateFieldType** property is set to a value other than **None**.

```xpp
CustPackingSlipTransHistory history;
utcDateTime dateFrom, dateTo = DateTimeUtil::utcNow();
anytype recid = -1;
select
    validTimeState(dateFrom, dateTo)
    *
    from history;
recid = history.RecId;
info('RecId:' + int642Str(recid));
```

## where keyword

The **where** keyword filters rows from a table where the expression is **true**.

The following example finds a customer that has an **AccountNum** value that is more than 100.

```xpp
CustTable custTable;
select * from custTable
    where custTable.AccountNum > '100';
info("AccountNum: " + custTable.AccountNum);
```

The following examples prints the lowest **AccountNum** value that is more than 100.

```xpp
CustTable custTable;
select * from custTable
    order by accountNum
    where custTable.AccountNum > '100';
info("AccountNum: " + custTable.AccountNum);
```

The following example prints the highest **AccountNum** value that is more than 100.

```xpp
CustTable custTable;
select * from custTable
    order by accountNum desc
    where custTable.accountNum > "100";
info("AccountNum: " + custTable.AccountNum);
```

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
