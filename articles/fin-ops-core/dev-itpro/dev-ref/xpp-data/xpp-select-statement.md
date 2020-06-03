---
# required metadata

title: Select statement
description: This topic describes the select statement in the X++ language.
author: robinarh
manager: AnnBe
ms.date: 11/08/2019
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

# Select statement

[!include [banner](../../includes/banner.md)]

This topic describes the **select** statement in the X++ language.

## select statements

The **select** statement fetches or manipulates data from the database.

+ All **select** statements use a table variable to fetch records. This variable must be declared before a **select** statement can be run.
+ The **select** statement fetches only one record, or field.
+ To fetch or traverse multiple records, you can use the **next** statement or the **while select** statement.
    + The **next** statement fetches the next record in the table. If no **select** statement precedes the **next** statement, an error occurs. If you use a **next** statement, don't use the **firstOnly** find option.
    + It's more appropriate to use a **while select** statement to traverse multiple records.
+ The results of a **select** statement are returned in a table buffer variable.
+ If you use a field list in the **select** statement, only those fields are available in the table variable.
+ If you use aggregate functions, such as **sum** or **count**, the results are returned in the fields that you perform the **sum** or **count** over.
+ You can count, average, or sum only integer and real fields.

## Select example

The following example fetches all the columns in the first row of the **CustomerTable** table and prints the **AccountNum** column of the row.

```xpp
CustTable custTable;
select * from custTable;
info("AccountNum: " + custTable.AccountNum);
```

For more examples of data selection, see [Select data](xpp-select.md).

## Insert example

The following example inserts a new record into the **CustomerTable** table. The **AccountNum** column of the new record is set to **2000**, and the **Name** field is set to **Ashley Schroeder**. Other fields in the record will be blank.

```xpp
ttsBegin;
    CustTable custTable;
    select forUpdate custTable;
    custTable.AccountNum = '2000';
    custTable.CustGroup = '1';
    custTable.insert();
ttsCommit;
```

## Update example

The following example selects the **CustomerTable** table for update. All records where the value of the **AccountNum** field is equal to **2000** are updated. The value of the **CreditMax** field is changed to **5000**.

```xpp
ttsBegin;
    CustTable custTable;
    select forUpdate custTable
    where custTable.AccountNum == '2000';
    custTable.CreditMax = 5000;
    custTable.update();
ttsCommit;
```

## Delete example

In the following example, all records in the **CustomerTable** table that satisfy the criterion in the **where** clause (that is, all records where the value of the **AccountNum** field is equal to **2000**) are deleted from the database. One record is deleted at a time.

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


## Syntax of select statements

These symbols are used in the syntax:
+ **\[\]**: Optional
+ **{}**: 0 or more
+ **\+**: 1 or more

|Symbol                |   | Expression                                                                |
|----------------------|---|---------------------------------------------------------------------------|
|*SelectStatement*     | = | **select** *Parameters*                                                   |
|*Parameters*          | = | { *FindOption* } [ *FieldList* **from** ] *TableBufferVariable* [ *IndexClause* ] [ *Options* ] [ *WhereClause* ] [ *JoinClause* ] |
|*FindOption*          | = | **crossCompany** [**:** *ContainerVariable*] \| **reverse** \| **firstFast** \|  *FirstOption* \| **forUpdate** \| **noFetch** \| *ForceOption* \| **forceSelectOrder** \| **forceNestedLoop** \| *LockOption* \| **repeatableRead** \| **validTimeState** |
|*FirstOption*         | = | **firstOnly** \| **firstOnly10** \| **firstOnly100** \| **firstOnly1000** |
|*LockOption*          | = | **optimisticLock** \| **pessimisticLock**                                 |
|*ForceOption*         | = | **forcePlaceholders** \| **forceLiterals**                                |
|*FieldList*           | = | { *Field* } \| **\***                                                     |
|*Field*               | = | *Aggregate* **(** *FieldIdentifier* **) | *FieldIdentifier*               |
|*Aggregate*           | = | **sum** \| **avg** \| **minof** \| **maxof** \| **count**                 |
|*Options*             | = | *OrderClause* \| *IndexClause*                                            |
|*OrderClause*         | = | [*OrderBy* [*GroupBy*]] \| [*GroupBy* [*OrderBy*]]                        |
|*OrderBy*             | = | **order** [**by**] *FieldOrder* {**,** *FieldOrder* }                     |
|*GroupBy*             | = | **group** [**by**] *FieldOrder* {**,** *FieldOrder* }                     |
|*FieldOrder*          | = | *FieldIdentifier* [ **asc** \| **desc** ]                                 |
|*IndexClause*         | = | **index** *IndexName* \| **index hint** *IndexName*                       |
|*WhereClause*         | = | **where** *Expression* *InClause*                                         |
|*InClause*            | = | **in** *List*                                                             |
|*JoinClause*          | = | [**exists** \| **notexists** \| **outer** ] **join**  *Parameters*        |
|*ContainerVariable*   | = | A container.                                                              |
|*Expression*          | = | Expression.                                                               |
|*TableBufferVariable* | = | The variable name for the results.                                        |
|*FieldIdentifier*     | = | The name of a field in the table.                                         |
|*IndexName*           | = | The name of an index for a table.                                         |
|*List*                | = | An array of values.                                                       |

## FindOptions keywords and examples

### crossCompany

The `crossCompany` keyword returns data for all companies that the user is authorized to read from. You can add a container to reduce the number of companies that are involved. The following code example returns data for companies that the user is authorized to read from. Results are limited to companies 'dat' and 'dmo'.

```xpp
CustTable custTable;
container conCompanies = ['dat','dmo'];
select crossCompany :conCompanies
    * from custTable;
```
    
### firstFast keyword

The `firstFast` keyword is a priority hint. The first row appears more quickly, but the total return time for this option might be slower. The **firstFast** hint is automatically issued from all pages.

The following code example returns the first row quickly.

```xpp
CustTable custTable;
select firstFast custTable
    order by AccountNum;
```

### firstOnly keywords

The `firstOnly` keywords speed up the fetch by returning a limited number of rows.

| Keyword           | Description |
|-------------------|-------------|
| firstOnly         | Returns only the first row. |
| firstOnly10       | Returns 10 rows. |
| firstOnly100      | Returns 100 rows. |
| firstOnly1000     | Returns 1,000 rows. |

The following code example returns only the first row of the results.

```xpp
CustTable custTable;
select firstonly custTable
    index hint AccountIdx
    where custTable.AccountNum == '5000';
```

### forceNestedLoop

The `forceNestedLoop` keyword forces the SQL Server database to use a nested-loop algorithm to process a particular SQL statement that contains a join algorithm. Therefore, a record from the first table is fetched before any records from the second table are fetched. Typically, other join algorithms, such as hash joins and merge joins, are considered. This keyword is often combined with the **forceSelectOrder** keyword.

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

    
### forcePlaceholders and forceLiterals keyword example.

The `forcePlaceholders` keyword instructs the kernel *not* to reveal the actual values that are used in **where** clauses to the SQL Server database at the time of optimization. By default, this behavior is used in all statements that aren't **join** statements. The advantage of using this keyword is that the kernel can reuse the access plan for similar statements that have other search values. The disadvantage is that the access plan is computed, but the fact that data distribution might be uneven isn't considered. The access plan is an on-average access plan. The **forcePlaceholders** and **forceLiterals** keywords are mutually exclusive.

The `forceLiterals` keyword instructs the kernel to reveal the actual values that are used in **where** clauses to the Microsoft SQL Server database at the time of optimization. The **forceLiterals** and **forcePlaceholders** keywords are mutually exclusive. 

> [!WARNING]
> You should not to use the **forceLiterals** keyword in **select** statements, because it could expose code to an SQL injection security threat.

The following example iterates through the SalesTable joined with the SalesLine.

```xpp
CustGroup custGroup;
CustTable custTable;

while select forceplaceholders custGroup
    join custTable
    where custGroup.CustGroup == custTable.CustGroup
{
    Info(custTable.CustGroup);
}
```

### forceSelectOrder

The `forceSelectOrder` keyword forces the SQL Server database to access the tables in a join in the specified order. If two tables are joined, the first table in the statement is always accessed first. This keyword is often combined with the **forceNestedLoop** keyword. 

The following example joins the ForecastPurch and InventDim tables on the **itemId** field.

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
 
### noFetch

The `noFetch` keyword indicates that no records should be fetched now. Typically, this keyword is used when the result of the `select` statement is passed on to another application object, such as a query that performs the actual fetch.

The following example creates a query variable, but does not fetch the records.

```xpp
CustTable custTable;
select noFetch custTable
    order by AccountNum;
```
    
### reverse

The `reverse` keyword returns records in reverse order.

```xpp
CustTable custTable;
select reverse custTable
    order by AccountNum;
```

### validTimeState

The `validTimeState` keyword selects rows from a table where the **ValidTimeStateFieldType** property is set to a value other than **None**.

```xpp
CustPackingSlipTransHistory history;
utcDateTime dateFrom, dateTo = DateTimeUtil::utcNow();
anytype recid = -1;
//dateFrom = DateTimeUtil::utcNow();
//dateTo = dateFrom;
select
    validTimeState(dateFrom, dateTo)
    *
    from history;
recid = history.getFieldValue("RecId");
info('RecId:' + int642Str(recid));
```

> [!WARNING]
> why use "getFieldValue" here, instead of history.RecId?

## Aggregate keywords

### avg

The `avg` keyword returns the average of the fields.

```xpp
CustTable custTable;
select avg(Value) from custTable;
info(int642Str(custTable.Value));
```

###  count keyword example

The `count` keyword returns the number of records.

```xpp
CustTable custTable;
int64 iCountRows;
select count(RecID) from custTable;
iCountRows = custTable.RecID;
info('Rows: ' + int642Str(iCountRows));
```

###  maxof keyword example

The `maxof` keyword returns the maximum of the fields.

```xpp
CustTable custTable;
select maxof(CreditMax) from custTable;
info(int642Str(custTable.Value));
```

###  minof keyword example

The `minof` keyword returns the minimum of the fields.

```xpp
CustTable custTable;
select minof(CreditMax) from custTable;
info(int642Str(custTable.Value));
```

###  sum keyword example

The `sum` keyword returns the sum of the fields. It can be used to sum all accounts, order lines, and so on. |

```xpp
CustTable custTable;
select sum(CreditMax) from custTable;
info(int642Str(custTable.Value));
```

### Aggregate functions: Differences between X++ and SQL

In industry-standard SQL, a database query can contain aggregate functions. Examples include `count(RecID)` and `sum(columnA)`. When an aggregate function is used, but no rows match the **where** clause, a row must be returned to hold the result of the aggregates. The row that is returned shows the value **0** (zero) for the **count** function and **null** for the **sum** function. X++ doesn't support the concept of **null** values for the database. Therefore, in cases where the **sum** function will return **null**, no row is returned to the user. Additionally, every data type has a specific value that is treated as a **null** value in some circumstances.

## Options examples

### asc

The `asc` keyword is an option on the `order by` or `group by` clause. It specifies an ascending sort. If neither `asc` nor `desc` is specified, the sort is ascending.

```xpp
CustTable custTable;
select * from custTable
    order by Value asc;
```

### desc

The `desc` keyword is an option on the `order by` or `group by` clause. It specifies an descending sort. If neither `asc` nor `desc` is specified, the sort is ascending.

```xpp
CustTable custTable;
select * from custTable
    order by Value desc;
```

### group by

The `group by` keyword instructs the database to group selected records by fields.

```xpp
CustTable custTable;
while select sum(CreditMax) from custTable
    group by CustGroup
{
    info(custTable.CustGroup + ' ' + int642Str(custTable.CreditMax));
}
```

## order by

The `order by` keyword instructs the database to sort the selected records by the fields in the `order by` list.

```xpp
CustTable custTable;
select * from custTable
    order by accountNum desc
    where custTable.AccountNum > '100';
info("AccountNum: " + custTable.AccountNum);
```

The following example print the highest AccountNum in the **CustTable** table.

```xpp
CustTable custTable;
select reverse custTable
    order by accountNum;
info("AccountNum: " + custTable.AccountNum);
```

## IndexClause examples

### index

The `index` keyword instructs the database to sort the selected records in the manner that is defined by the index.

```xpp
CustTable custTable;
while select AccountNum, Value from custTable
    index AccountIdx
{
    Info(custTable.AccountNum +  ": " + int642Str(custTable.Value));
}
```

### index hint

The `index hint` keyword gives the database a hint to use this index to sort the selected records in the manner that is defined by the index. The database can ignore the hint. An incorrect index hint can greatly affect performance. Index hints should be applied only to SQL statements that don't have dynamic **where** clauses or **order by** clauses, and where the effect of the hint can be verified.

```xpp
str _accountNum = '111';
CustTable custTable;

while select forUpdate custTable
    index hint AccountIdx
    where custTable.AccountNum == _accountNum
{
}
```

## JoinClause examples

### exists

The `exists` keyword is a method that returns a Boolean value and a **join** clause.

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

<-- START HERE -->

### join

The `join` keyword is used to join tables on a column that is shared by both tables. The join criteria are specified in a **where** clause, because there is no `on` keyword (as is found in SQL). This keyword reduces the number of SQL statements that are required if you want to loop through a table and update transactions in a related table. For example, you process 500 records in a table and want to update related records in another table. If you use a nested **while select**, there will be 501 trips to the database. However, if you use a **join**, there will be just one trip to the database.


```xpp
while select ledgerTable
    join ledgerTrans
    where ledgerTrans.accountNum == ledgerTable.accountNum
{
    amountMST += ledgerTrans.amountMST;
}
```

### notExists

The `notExists` keyword is selected only if there are no posts.

``` xpp
while select AccountNum, Name from custTable
    order by AccountNum
    notExists join * from ctr
    where (ctr.AccountNum ==
        custTable.AccountNum)
```

### outer

The `outer` keyword returns all rows from the table that is named first, even if rows have no match in the table that is named second. This join is a left outer join. Default values are substituted for the data that couldn't be obtained from a matching row in the other joined table. 

There is no `left` keyword, and there is no right outer join.

For an inner join, the behavior if you filter on an **on** clause is the same as the behavior if you filter on the **where** clause.

```xpp
while select AccountNum
    from custTable
    order by AccountNum
    outer join * from custBankAccount
    where custBankAccount.AccountNum == custTable.AccountNum
{
    info(custTable.AccountNum + ', ' + custBankAccount.DlvMode);
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
static void SelectOuterJoinExample(Args _args)
{
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
}

// Example output:
// (SalesOrderID:1;
// DateAdded:2010/1/1;
// SalesOrderLineID:"CC";
// Quantity:66)
// (SalesOrderID:2;
// DateAdded:2010/2/2;
// SalesOrderLineID:"";
// Quantity:0)
```

## Lock examples

The `optimisticLock` keyword forces a statement to run by using optimistic concurrency control, even if a different value is set on the table.

```xpp
select optimisticLock custTable
    where custTable.AccountNum > '1000'
```

The `pessimisticLock` keyword forces a statement to run by using pessimistic concurrency control, even if a different value is set on the table.  |

```xpp
select pessimisticLock custTable
    where custTable.AccountNum > '1000';
```

## where examples

The `where` keyword filters rows from a table where the *expression* is **true**.

The following example finds a customer with AccountNum greater than 100.

```xpp
CustTable custTable;
select * from custTable
    where custTable.AccountNum > "100";
info("AccountNum: " + custTable.AccountNum);
```

The following examples prints the AccountNum of the lowest AccountNum that is greater than 100.

```xpp
CustTable custTable;
select *
    from custTable 
    order by accountNum
    where custTable.AccountNum > "100";
info("AccountNum: " + custTable.AccountNum);
```

The following example prints the AccountNum of the highest AccountNum that is greater than 100.
```xpp
select *
    from custTable 
    order by accountNum desc
    where custTable.accountNum > "100";
info("AccountNum: " + custTable.AccountNum);
```

## in examples

This `in` keyword filters rows where a value is contained in a list.

Without using the `in` keyword, you would write code like this:

```X++
private CostAmountStdAdjustment calcCostAmountStdAdjustment() 
{
    InventSettIement inventSettIement; 

    select sum(CostAmountAdjustment) fron inventSettIement 
        where inventSettlement.TransRecld == this.RecId 
            && inventSettlement.Cencelled == NoYes::No 
            && (inventSettlement.OperationsPosting == LedgerpostingType::purchStdProfit 
                || inventSettlement.OperationsPosting == LedgerpostingType::purchStdLoss
                || inventSettlement.OperationsPosting == LedgerpostingType::InventStdProfit
                || inventSettlement.OperationsPosting == LedgerpostingType::InventStdLoss);

    return inventSettlement.CostAmountAdjustment; 
}
```

Using the `in` keyword, you would write code like this:

```X++
private CostAmountStdAdjustment calcCostAmountStdAdjustment() 
{
    InventSettlement inventSettlement; 
    container ledgerPostingTypes = this.ledgerPostingTypesForCostAmountStdAdjustmentCalculation(); 
    
    select sum(CostAmountAdjustment) from inventSettlement 
        where inventSettlement.TransRecId == this.RecId 
            && inventSettlement.Cancelled == NoYes::No
            && inventSettlement.OperationsPosting in ledgerPostingTypes;
            
    return inventSettlement.CostAmountAdjustment; 

protected container ledgerPostingTypesForCostAmountStdAdjustmentCalculation() 
{
    return [
        LedgerPostingType: : purchStdProfit, 
        LedgerPostingType: : PurchStdLoss, 
        LedgerPostingType: : InventStdProfit, 
        LedgerPostingType: : InventStdLoss
    ];
}
```

## repeatableRead keyword

This `repeatableRead` keyword specifies that the current transaction must be completed before other transactions can modify data that has been read by logic inside the current transaction. An explicit transaction is completed at either `ttsAbort` or the outermost `ttsCommit`. For a stand-alone **select** statement, the transaction duration is the duration of the **select** command. However, the database sometimes enforces the equivalent of `repeatableRead` in individual **select** statements, even if this keyword doesn't appear in your code. (The behavior depends on the method that the database uses to determine whether it should scan the tables.) For more information, see the documentation for the underlying relational database product.

### join example

The following example shows how an inner join can be performed as part of a **select** statement. The example also shows an **order by** clause, where each field is qualified by a table name. Therefore, you can use just one **order by** clause to control how the retrieved records are sorted.

```xpp
CustTable custTable;
CashDisc cashDisc;
struct sut4 = new struct("str AccountNum; str CashDisc; str Description");
while select firstOnly10 *
    from custTable
    order by cashDisc.Description
    join cashDisc
    where 
        custTable.CashDisc == cashDisc.CashDiscCode
        && cashDisc.Description like "*Days*"
    {
        sut4.value("AccountNum", custTable.AccountNum );
        sut4.value("CashDisc", cashDisc.CashDiscCode );
        sut4.value("Description", cashDisc.Description );
        info(sut4.toString());
    }
}

// Example output:
// (AccountNum:"1101"; CashDisc:"0.5%D10"; Description:"0.5% 10 days")
// (AccountNum:"4001"; CashDisc:"0.5%D10"; Description:"0.5% 10 days")
// (AccountNum:"1102"; CashDisc:"0.5%D30"; Description:"0.5% 30 days")
// (AccountNum:"1201"; CashDisc:"0.5%D30"; Description:"0.5% 30 days")
// (AccountNum:"2211"; CashDisc:"0.5%D30"; Description:"0.5% 30 days")
```

### group by and order by example

The following example shows that the fields in the **group by** clause can be qualified by a table name. There can be multiple **group by** clauses. However, the fields can be qualified by a table name in only one **group by** clause. We recommend that you use table name qualifiers. The **order by** clause follows the same syntax patterns as **group by**. Both clauses, if they are provided, must appear after the **join** (or **from**) clause, and both must appear before any **where** clause that exists on the same **join** clause. We recommend that all **group by**, **order by**, and **where** clauses appear immediately after the last **join** clause.

```xpp
CustTable custTable;
CashDisc cashDisc;
sut4 = new struct("str AccountNum_Count; str CashDisc; str Description");
while select count(AccountNum)
    from custTable
    order by cashDisc.Description
    join cashDisc
        group by cashDisc.CashDiscCode
        where 
            custTable.CashDisc == cashDisc.CashDiscCode
            && cashDisc.Description like "*Days*"
{
    sut4.value("AccountNum_Count", custTable.AccountNum );
    sut4.value("CashDisc", cashDisc.CashDiscCode );
    sut4.value("Description", cashDisc.Description );
    info(sut4.toString());
}

// Example output:
// (AccountNum_Count:"2"; CashDisc:"0.5%D10"; Description:"")
// (AccountNum_Count:"3"; CashDisc:"0.5%D30"; Description:"")
}
```


## while select statements
A **while select** statement is used to handle data. It's the most widely used form of the **select** statement. The **while select** statement loops over many records that meet specific criteria, and can run a statement on each record. Typically, when you use the **while select** statement for data manipulation, you do it in a transaction to ensure data integrity. The results of a **while select** statement are returned in a table buffer variable. If you use a field list in the **select** statement, only those fields are available in the table variable. If you use aggregate functions, such as **sum** or **count**, the results are returned in the fields that you perform the **sum** or **count** over. You can count, average, or sum only integer and real fields. The syntax of a **while select** statement resembles the syntax of a **select** statement, but the statement is preceded by **while select** instead of **select**. The **select** statement itself is run only one time, immediately before the first iteration of the statements in the loop. Any Boolean expressions (such as **iCounter &lt; 1**) that are added to the **while select** are tested only one time. This behavior differs from the behavior of the **while** statement in languages such as C++ and C\#. For example, the following loop can have more than one iteration.

```xpp
static void JobWhileSelect(Args _args)
{
    int iCounter = 0;
    BankAccountTable xrecBAT;
    while select * from xrecBAT
        where iCounter < 1
    {
        iCounter++;
        Global::info(strFmt("%1 , %2", iCounter, xrecBAT.AccountID));
    }
}

/*** Display from infolog:
Message (04:59:38 pm)
1 , Cash1
2 , STB-DKK
3 , STB-EUR
***/
```

### while select example

The following example prints the account number and sales group of every customer in the CustTable table whose account number is within a specified range.

```xpp
static void JobPrintTel(Args _args)
{
    CustTable xrecCT;
    while select xrecCT
        order by xrecCT.AccountNum
            where  xrecCT.AccountNum >= "4010"
                && xrecCT.AccountNum <= "4100"
    {
        Global::info(strFmt("%1 , %2",
            xrecCT.AccountNum, xrecCT.SalesGroup));
    }
}

/*** Display from Infolog:
Message (06:04:03 pm)
4010 , CSG-EU
4011 , CSG-EU
4012 , CSG-OTH
4013 , CSG-OTH
4014 , CSG-OTH
4015 , CSG-OTH
4016 , CSG-EU
4017 , CSG-EU
4018 , CSG-EU
4020 , 
4024 , 
***/
```

### while select example

The following example uses the **forUpdate** keyword.

```xpp
static void LedgerJob(Args _args)
{
    LedgerJournalTrans ledgerJournalTrans;
    LedgerJournalTable ledgerJournalTable;
    LedgerJournalId    jnJournalNum;
    Voucher            vVoucher;
    Counter            counter = 0;
    jnJournalNum = "999999_999"; //"000012_003";
    vVoucher = "88888_888"; //"00001_IRG";
    ledgerJournalTable =
        ledgerJournalTable::find(jnJournalNum);
    ttsBegin;
    while select forUpdate ledgerJournalTrans
        index hint NumVoucherIdx
            where ledgerJournalTrans.journalNum == jnJournalNum
                && ledgerJournalTrans.voucher == vVoucher
    {
        ledgerJournalTrans.doDelete();
        counter++;
    }
    //NumberSeq updates needed?
    ttsCommit;
    Global::info(strFmt("counter = %1", counter));
}
```

### Deleting a set of records

You can use a **while select** statement to loop over a set of records that meet some criteria, and perform an action on each record. In the following example, the statement is used to delete a set of records.

```xpp
TableName myXrec;
while select myXrec where conditions // conditions is a Boolean variable defined elsewhere.
{
    myXrec.delete();
}
```

You can achieve the same effect by using the **delete\_from** keyword.

```xpp
TableName myXrec;
delete_from myXrec where conditions; // conditions is a Boolean variable defined elsewhere.
```

### select statements on fields

You can use a **select** statement in a lookup on a field. After a **select** statement that fetches a record in a table, you can enter **.fieldName** to reference a field in the table. These **select** statements must be used in expressions. A *normal **select** statement* differs from a *field **select** statement*:

-   The field **select** statement operates directly on a table.
-   The normal **select** statement operates on a table buffer variable.

### select field example

```xpp
void selectFieldExamples ()
{
    // Prints the NameRef field from the selected customer
    print (select CustTable order by AccountStatement).AccountStatement;

    // Uses the balance field from the customer with AccountNum 3000
    if ((select custTable where CustTable.AccountNum == '3000').CreditMax < 50000)
        print "This customer has a credit maximum less than $50,000.";
}
```

### index and order by keywords

You use the `order by` keyword in **select** statements to order the data that is returned. Use the `index hint` keyword to specify the index that should be used in the query and to sort the selected records in the manner that is defined by the index. Indexes optimize the selection of records. To select records in a specific order, combine the `index hint` keyword with an **order by** expression. If you want the output to be sorted in reverse order, use the `reverse` keyword. If a table index has been disabled (that is, if the index's **Enabled** property is set to **No**), the **select** statement that references the index is still valid. However, the database can't use the index as a hint to sort the data, because the index doesn't exist in the database. The following table shows how to use the `index hint` and `order by` keywords in **select** statements.

| Task                                                                                 | Use                                   |
|--------------------------------------------------------------------------------------|---------------------------------------|
| Select records when the order isn't significant.                                     | select .. where ...                   |
| Select records when the order is significant.                                        | select .. order by ... where ...      |
| Select records, and force a specific index to be used.                               | select .. index hint ... where ...    |
| Select records when the order is significant, and force a specific index to be used. | select .. index hint ... order by ... where ... |

### index and order by example

The following example shows how to select transactions from the **SalesTable** table, based on a range of customers and due dates.

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

### index hint

Before you can use **index hint** in queries, you must specify that hints can be used on the server.

1.  Go to **Start** > **Administrative Tools** > **Microsoft Dynamics AX Server Configuration**.
2.  On the **Database Tuning** tab, select **Allow INDEX hints in queries**, and then click **OK**.
3.  When a message box prompts you to restart the Application Object Server (AOS) service, click **Yes**. Index hints won't be enabled until the service is restarted.

When an `index hint` keyword in a **select** statement refers to a non-clustered index, and the **where** clause contains only the fields that are found in a clustered index on the same table, the clustered index is used instead of the index that is specified in the hint. For example, you run **sp\_helpindex InventTable** in SQL Server Management Studio and you see that the **InventTable** table has a clustered index on the **DataAreaId** and **ItemId** columns, and a non-clustered index on the **DataAreaId**, **ItemProductId**, and **ItemType** columns.

| Index name       | Description                                        | Key columns                         |
|------------------|----------------------------------------------------|-------------------------------------|
| I\_175ITEMIDX    | Clustered, unique, primary key, located on PRIMARY | DATAAREAID, ITEMID                  |
| I\_175PRODUCTIDX | Non-clustered, located on PRIMARY                  | DATAAREAID, ITEMPRODUCTID, ITEMTYPE |

In the following code, the clustered index is used instead of the non-clustered index that is specified by **index hint**.

```xpp
InventTable inv;
select * from inv index hint GroupItemIdx
    where inv.ItemId == 'B-R14';
```

## Writing a select statement as an expression

You can use a **select** statement as an expression. This type of **select** statement is known as an *expression **select** statement*. A table buffer variable can't be used in an expression **select** statement. The name of the table must be used in the **from** clause. One limitation of expression **select** statements is that the **join** keyword isn't supported in an expression join.

In the following example, the **select** statement inside the parentheses returns one row. 
+ The only column that can be populated with data is the column that is named before the **from** clause in the **select** clause. 
+ After the closing parenthesis, the name of that column is used to reference the data value: **AccountNum**. 
+ This example returns a maximum of one row, because it uses the `firstonly` keyword. However, the value that is assigned to **sAccountNum** is the same, even if the `firstonly` keyword is omitted. 
+ The table name can't be used to qualify a field name in the **order by** clause.

```xpp
str sAccountNum;
sAccountNum = (select firstonly AccountNum from CustTable
    order by AccountNum des) 
    .AccountNum;
info(strFmt("Max AccountNum: %1", sAccountNum));

// Output: Max AccountNum: 4507
```

Here is a simpler way to achieve the same result as the previous example.

```xpp
str sAccountNum;
sAccountNum = (select maxof(AccountNum) from CustTable).AccountNum;
info(strFmt("Max RecId: %1", sAccountNum));

// Output: Max AccountNum: 4507
```

The following example returns the maximum RecId of customers that are not blocked. In a **where** clause, the table name must be used as a qualifier of the field. Here, the **maxof** aggregate function is used, and the **RecId** field is mentioned in the function. The field that is mentioned in the aggregate function must be the same as the field name that is used to reference the data value after the closing parenthesis. Otherwise, empty data is returned.

```xpp
int64 nRecId;
nRecId = (select maxof(RecId) from CustTable
    where CustTable.Blocked == CustVendorBlocked::No)
    .RecId;
info(strFmt("Max RecId: %1", nRecId));

// Output: Max RecId: 5637144604
```

In the following example, a field name (in this case, **RecId**) is used to reference a data value that isn't a **RecId** value. The **count** aggregate function doesn't return a **RecId** value. Typically, the **RecId** field is used with the **count** function.

```xpp
int64 nRecId;
nRecId = (select count(RecId) from CustTable
    where CustTable.Blocked == CustVendorBlocked::No)
    .RecId;
info(strFmt("Count of unblocked customers: %1", nRecId));

// Output: Count of unblocked customers: 29
```

There are some limitations of **expression select statements**:
+ The `join` keyword isn't supported in **expression select statements**. 
+ You can only mention one table in an **expression select statement**, therefore subselects are not supported as a workaround to the unsupported `join` keyword.
