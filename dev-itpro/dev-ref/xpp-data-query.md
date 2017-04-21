---
# required metadata

title: X++ data selection and manipulation
description: This topic describes the support for data selection and manipulation in the X++ language.
author: RobinARH
manager: AnnBe
ms.date: 04/21/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 150273
ms.assetid: 999a5ecf-559b-4d66-8b05-9a8e477e0518
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.intro: AX 7.0.0
ms.search.validFrom: 2016-02-28

---

# X++ data selection and manipulation

This topic describes the support for data selection and manipulation in the X++ language.

You can use SQL statements, either interactively or within source code, to access and retrieve data that is stored in the database. You use the following statements for data manipulation:

-   **select** – Select the data to modify.
-   **insert** – Add one or more new records to a table.
-   **update** – Modify data in existing table records.
-   **delete** – Remove existing records from a table.

Before any data can be changed, you must use a **select** statement to select the data to update. The **select forUpdate** command selects records for update only. The **insert**, **update**, and **delete** statements perform operations on one record at a time. The **array insert**, **insert\_recordset**, **RecordInsertList**, and **update\_recordset** statements perform operations on multiple records at the same time.

## select statements
The **select** statement fetches or manipulates data from the database. All **select** statements use a table variable to fetch records. This variable must be declared before a **select** statement can be run. The **select** statement fetches only one record, or field. To fetch additional records, you can use the **next** statement. The **next** statement fetches the next record in the table. If no **select** statement precedes the **next** statement, an error occurs. If you use a **next** statement, don't use the **firstOnly** find option. If you must traverse several records, it's more appropriate to use a **while** **select** statement. The results of a **select** statement are returned in a table buffer variable. If you use a field list in the **select** statement, only those fields are available in the table variable. If you use aggregate functions, such as **sum** or **count**, the results are returned in the fields that you perform the **sum** or **count** over. You can count, average, or sum only integer and real fields.

## Syntax of select statements
|                   |     |                                                                                                                                                                                                                                                                                                    |
|-------------------|-----|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *SelectStatement* | =   | **select** *Parameters*                                                                                                                                                                                                                                                                            |
| *Parameters*      |     | **\[ \[** *FindOptions* **\]** **\[** *FieldList* **from \] \]** *TableBufferVariable* **\[** *IndexClause* **\]** **\[** *Options* **\]** **\[** *WhereClause* **\]** **\[** *JoinClause* **\]**                                                                                                  |
| *FindOptions*     | =   | **crossCompany** | **reverse** | **firstFast** | \[ **firstOnly** | **firstOnly10** | **firstOnly100** | **firstOnly1000** \] | **forUpdate** | **noFetch** | \[**forcePlaceholders** | **forceLiterals**\] | **forceselectorder** | **forceNestedLoop** | **repeatableRead** | **validTimeState** |
| *FieldList*       | =   | *Field* **{ ,** *Field* **}** | **\***                                                                                                                                                                                                                                                             |
| *Field*           | =   | *Aggregate* **(** *FieldIdentifier* **) |** *FieldIdentifier*                                                                                                                                                                                                                                      |
| *Aggregate*       | =   | **sum** | **avg** | **minof** | **maxof** | **count**                                                                                                                                                                                                                                              |
| *Options*         | =   | **\[ order by** , **group by ,** *FieldIdentifier* **\[ asc** | **desc \] { ,** *FieldIdentifier* **\[ asc** | **desc \] }\]** | **\[** *IndexClause* **\]**                                                                                                                                       |
| *IndexClause*     | =   | **index** *IndexName* | **index hint** *IndexName*                                                                                                                                                                                                                                                 |
| *WhereClause*     | =   | **where** *Expression*                                                                                                                                                                                                                                                                             |
| *JoinClause*      | =   | \[**exists** | **notexists** | **outer** \] **join** *Parameters*                                                                                                                                                                                                                                  |

### Keywords that are used in select statements

| Keyword           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| asc               | This keyword is an option on the **order by** or **group by** clause. It specifies an ascending sort. If neither **asc** nor **desc** is specified, the sort is ascending.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| avg               | This keyword returns the average of the fields.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| count             | This keyword returns the number of records.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| crossCompany      | This keyword returns data for all companies that the user is authorized to read from. You can add a container to reduce the number of companies that are involved.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| desc              | This keyword is an option on the **order by** or **group by** clause. It specifies a descending sort. If neither **asc** nor **desc** is specified, the sort is ascending.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| exists            | This keyword is a method that returns a Boolean value and a **join** clause.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| firstFast         | This keyword is a priority hint. Although the first row appears more quickly, but the total return time for this option might be slower. The **firstFast** hint is automatically issued from all pages.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| firstOnly         | This keyword helps speed up the fetch by returning only the first row.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| firstOnly10       | This keyword is the same as **firstOnly**, but it returns 10 rows instead of one.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| firstOnly100      | This keyword is the same as **firstOnly**, but it returns 100 rows instead of one.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| firstOnly1000     | This keyword is the same as **firstOnly**, but it returns 1,000 rows instead of one.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| forceLiterals     | This keyword instructs the kernel to reveal the actual values that are used in **where** clauses to the Microsoft SQL Server database at the time of optimization. The **forceLiterals** and **forcePlaceholders** keywords are mutually exclusive. You should not to use the **forceLiterals** keyword in **select** statements, because it could expose code to an SQL injection security threat.                                                                                                                                                                                                                                                                                                                                                              |
| forceNestedLoop   | This keyword forces the SQL Server database to use a nested-loop algorithm to process a particular SQL statement that contains a join algorithm. Therefore, a record from the first table is fetched before any records from the second table are fetched. Typically, other join algorithms, such as hash joins and merge joins, are considered. This keyword is often combined with the **forceSelectOrder** keyword.                                                                                                                                                                                                                                                                                                                                           |
| forcePlaceholders | This keyword instructs the kernel *not* to reveal the actual values that are used in **where** clauses to the SQL Server database at the time of optimization. By default, this behavior is used in all statements that aren't **join** statements. The advantage of using this keyword is that the kernel can reuse the access plan for similar statements that have other search values. The disadvantage is that the access plan is computed, but the fact that data distribution might be uneven isn't considered. The access plan is an on-average access plan. The **forcePlaceholders** and **forceLiterals** keywords are mutually exclusive.                                                                                                            |
| forceSelectOrder  | This keyword forces the SQL Server database to access the tables in a join in the specified order. If two tables are joined, the first table in the statement is always accessed first. This keyword is often combined with the **forceNestedLoop** keyword.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| forUpdate         | This keyword selects records for update only. Depending on the underlying database, the records might be locked for other users.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| group by          | This keyword instructs the database to group selected records by fields.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| index             | This keyword instructs the database to sort the selected records in the manner that is defined by the index.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| index hint        | This keyword gives the database a hint to use this index to sort the selected records in the manner that is defined by the index. The database can ignore the hint. An incorrect index hint can greatly affect performance. Index hints should be applied only to SQL statements that don't have dynamic **where** clauses or **order by** clauses, and where the effect of the hint can be verified.                                                                                                                                                                                                                                                                                                                                                            |
| join              | This keyword is used to join tables on a column that is shared by both tables. The join criteria are specified in a **where** clause, because there is no **on**. This keyword reduces the number of SQL statements that are required if you want to loop through a table and update transactions in a related table. For example, you process 500 records in a table and want to update related records in another table. If you use a nested **while select**, there will be 501 trips to the database. However, if you use a **join**, there will be just one trip to the database.                                                                                                                                                                           |
| maxof             | This keyword returns the maximum of the fields.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| minof             | This keyword returns the minimum of the fields.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| noFetch           | This keyword indicates that no records should be fetched now. Typically, this keyword is used when the result of the **select** statement is passed on to another application object, such as a query that performs the actual fetch.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| notExists         | This keyword is selected only if there are no posts.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| optimisticLock    | This keyword forces a statement to run by using optimistic concurrency control, even if a different value is set on the table.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| order by          | This keyword instructs the database to sort the selected records by the fields in the **order by** list.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| outer             | This keyword returns all rows from the table that is named first, even if rows have no match in the table that is named second. This join is a left outer join, even though there is no **left**. There is no right outer join.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| pessimisticLock   | This keyword forces a statement to run by using pessimistic concurrency control, even if a different value is set on the table.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| repeatableRead    | This keyword specifies that the current transaction must be completed before other transactions can modify data that has been read by logic inside the current transaction. An explicit transaction is completed at either **ttsAbort** or the outermost **ttsCommit**. For a stand-alone **select** statement, the transaction duration is the duration of the **select** command. However, the database sometimes enforces the equivalent of **repeatableRead** in individual **select** statements, even if this keyword doesn't appear in your code. (The behavior depends on the method that the database uses to determine whether it should scan the tables.) For more information, see the documentation for the underlying relational database product. |
| reverse           | Records are returned in reverse order.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| sum               | This keyword returns the sum of the fields. It can be used to sum all accounts, order lines, and so on.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| validTimeState    | This keyword filters rows from a table where the **ValidTimeStateFieldType** property is set to a value other than **None**.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |

#### Keyword examples

    // asc keyword example.
    select * from custTable
        order by Name asc;

    // avg keyword example. 
    CustTable custTable;;
    select avg(value) from custTable;
    print custTable.value;

    // count keyword example. 
    CustTable xCT;int64 iCountRows; ;
    Select COUNT(RecID) from xCT;
    iCountRows = xCT.RecID;

    // crossCompany keyword example.
    CustTable custTable;
    container conCompanies = ['dat','dmo'];
    select crossCompany :conCompanies
        * from custTable;

    // desc keyword example.
    select * from custTable
        order by Name desc;

    // exists keyword example. 
    while select AccountNum, Name from custTable
        order by AccountNum
        exists join * from ctr
        where (ctr.AccountNum ==
            custTable.AccountNum)

    // firstFast keyword example.
    select firstFast custTable
        order by AccountNum;

    // firstOnly keyword example.
    static InventTable find(ItemIditemId, boolean update = false)
    {
        InventTable inventTable;
        inventTable.selectForUpdate(update);
        if (itemId)
        {
            select firstonly inventTable
                index hint ItemIdx
                where inventTable.itemId == itemId;
        }
        return inventTable;
    }

    // forceNestedLoop keyword example.
    while select forceSelectOrder
        forceNestedLoop inventTransThis
    index hint TransIdIdx
    where inventTransThis.InventTransId
        == inventTrans.InventTransId
        && inventTransThis.StatusIssue
        <= StatusIssue::ReservOrdered

    // forcePlaceholders keyword example.
    static void forcePlaceHoldersExample(Args _args){
        SalesTable salesTable;
        SalesLine salesLine;
        while select forcePlaceholders salesLine
            join salesTable
                where salesTable.SalesId ==
                    salesLine.SalesId
                    && salesTable.SalesId == '10'
        {
            //more code
        }
    }

    // forceSelectOrder keyword example.
    display ForecastHasPurch hasForecastPurch(){
        ForecastPurch forecastPurch;
        InventDim nventDim;
    select firstOnly forcePlaceholders
        forceSelectOrder recId
        from forecastPurch
        index hint ItemIdx
        where forecastPurch.itemId == this.itemId
    exists join inventDim
        index hint DimIdIdx
        where inventDim.inventDimId == forecastPurch.inventDimId
            && inventDim.configId == this.configId;
        return forecastPurch.recId;
    }

    // forUpdate keyword example.
    ttsBegin; while select forUpdate ledgerJournalTrans
        index hint NumVoucherIdx
        where ledgerJournalTrans.journalNum ==
        _journalNum &&
        ledgerJournalTrans.voucher == _voucher
    {
        ledgerJournalTrans.doDelete();
        counter++;
    }
    if (counter
        && ledgerJournalTable.journalType
        != LedgerJournalType::Periodic)
    {
        NumberSeq::release(
            ledgerJournalTable.voucherSeries,
            _voucher);
    }
    ttsCommit;

    // group by keyword example.
    CustTable custTable;;
    while select sum(CreditMax) from custTable
        group by CustGroup
    {
        print custTable.CustGroup, " ",custTable.CreditMax;
    }

    // index keyword example.
    CustTable custTable;;
    while select AccountNum, Name from custTable
        index AccountIdx
    {
        print custTable.AccountNum, " ", custTable.Name;
    }

    // index hint keyword example.
    while select forUpdate ledgerJournalTrans
        index hint NumVoucherIdx
        where ledgerJournalTrans.journalNum
            == _journalNum

    // join keyword example.
    while select ledgerTable
        join ledgerTrans
        where ledgerTrans.accountNum == ledgerTable.accountNum
    {
        amountMST += ledgerTrans.amountMST;
    }

    // maxof keyword example.
    CustTable custTable;;
    select maxof(CreditMax) from custTable;

    // minof keyword example.
    CustTable custTable;;
    select minof(CreditMax) from custTable;

    // noFetch keyword example.
    select noFetch custTable
        order by AccountNum

    // notExists keyword example.
    while select AccountNum, Name from custTable
        order by AccountNum
        notExists join * from ctr
        where (ctr.AccountNum ==
            custTable.AccountNum)

    // optimisticLock keyword example.
    select optimisticLock custTable
        where custTable.AccountNum > '1000'

    // order by keyword example.
    select * from custTable
        order by accountNum desc
        where custTable.AccountNum > "100";

    // outer keyword example.
    while select AccountNum
        from custTable
        order by AccountNum
        outer join * from custBankAccount
        where custBankAccount.AccountNum ==
            custTable.AccountNum
    {
        print custTable.AccountNum,
        " , ", custBankAccount.DlvMode;
    } 

    // pessimisticLock keyword example.
    select pessimisticLock custTable
        where custTable.AccountNum > '1000';

    // reverse keyword example.
    select reverse custTable
        order by AccountNum;

    // sum keyword example.
    CustTable custTable;;
    select sum(CreditMax) from custTable;

    // validTimeState keyword example.
    static void VtsJob1(Args _args)
    {
        // A validTimeState table.
        CustPackingSlipTransHistory xrec1;
        utcDateTime myDateFrom , myDateTo;
        anytype myAnytype = -1;
        myDateFrom = DateTimeUtil::utcNow();
        myDateTo = myDateFrom;
        SELECT
            validTimeState(myDateFrom, myDateTo)
                *
                FROM xrec1;
        myAnytype = xrec1.getFieldValue("RecId");
        info(myAnytype);
    }

## select statement examples
The following examples show how you can use **select** statements.

    CustTable custTable;
    // A customer is found and returned in custTable
    select * from custTable;
    info("A: " + custTable.AccountNum);

    // A customer with account number > "100" is found
    select * from custTable
        where custTable.AccountNum > "100";
    info("B: " + custTable.AccountNum);

    // Customer with the lowest account number > "100" found:
    select *
        from custTable 
        order by accountNum
        where custTable.AccountNum > "100";
    info("C1: " + custTable.AccountNum);

    // The next customer is read
    next custTable;
    info("C2: " + custTable.AccountNum);

    // Customer with highest account number
    // (greater than 100) found: Fourth Coffee
    select *
        from custTable 
        order by accountNum desc
        where custTable.accountNum > "100";
    info("D1: " + custTable.AccountNum);

    // The next record is read (DESC): Fabrikam, Inc.
    next custTable;
    info("D2: " + custTable.AccountNum);

    // Customer with highest account number found: Fourth Coffee
    select reverse custTable
        order by accountNum;
    info("E: " + custTable.AccountNum);

    // Customer with "lowest" name and account number
    // in the interval 100 to 1000 is found. This is Coho Winery.
    select *
        from custTable
        order by DlvMode
        where custTable.accountNum > "100"
            && custTable.accountNum < "1000";
    info("F: " + custTable.AccountNum);

    // The count select returns the number of customers.
    select count(AccountNum)
        from custTable;

    // Prints the result of the count
    info(strFmt("G: %1 = Count of AccountNums", custTable.accountNum));

    // Returns the average credit max for non-blocked customers.
    select avg(CreditMax)
        from custTable
        where custTable.blocked == CustVendorBlocked::No;

    // Prints the result of the avg
    info(strFmt("H: %1 = Average CreditMax", custTable.CreditMax));

    /*** Display from infolog:
    Message (02:00:34 pm)
    A: 4000
    B: 4000
    C1: 4000
    C2: 4001
    D1: 4507
    D2: 4506
    E: 4507
    F: 
    G: 29 = Count of AccountNums
    H: 103.45 = Average CreditMax
    ***/

### join example

The following example shows how an inner join can be performed as part of an SQL **select** statement. The example also shows an **order by** clause, where each field is qualified by a table name. Therefore, you can use just one **order by** clause to control how the retrieved records are sorted.

    CustTable xrecCustTable;
    CashDisc xrecCashDisc;
    struct sut4;
    sut4 = new struct("str AccountNum; str CashDisc; str Description");
    while select firstOnly10 *
        from xrecCustTable
        order by xrecCashDisc.Description
        join xrecCashDisc
        where xrecCustTable.CashDisc ==
            xrecCashDisc.CashDiscCode
            && xrecCashDisc.Description LIKE "*Days*"
        {
            sut4.value("AccountNum", xrecCustTable.AccountNum );
            sut4.value("CashDisc", xrecCashDisc.CashDiscCode );
            sut4.value("Description", xrecCashDisc.Description );
            info(sut4.toString());
        }
    /*********  Actual Infolog output
    Message (02:29:37 pm)
    (AccountNum:"1101"; CashDisc:"0.5%D10"; Description:"0.5% 10 days")
    (AccountNum:"4001"; CashDisc:"0.5%D10"; Description:"0.5% 10 days")
    (AccountNum:"1102"; CashDisc:"0.5%D30"; Description:"0.5% 30 days")
    (AccountNum:"1201"; CashDisc:"0.5%D30"; Description:"0.5% 30 days")
    (AccountNum:"2211"; CashDisc:"0.5%D30"; Description:"0.5% 30 days")
    (AccountNum:"1202"; CashDisc:"1%D15"; Description:"1% 15 days")
    (AccountNum:"1203"; CashDisc:"1%D07"; Description:"1% 7 days")
    (AccountNum:"2212"; CashDisc:"1%D07"; Description:"1% 7 days")
    (AccountNum:"2213"; CashDisc:"1%D07"; Description:"1% 7 days")
    (AccountNum:"2214"; CashDisc:"1%D07"; Description:"1% 7 days")
    *********/
    }

### group by and order by example

The following example shows that the fields in the **group by** clause can be qualified by a table name. There can be multiple **group by** clauses. However, the fields can be qualified by a table name in only one **group by** clause. We recommend that you use table name qualifiers. The **order by** clause follows the same syntax patterns as **group by**. Both clauses, if they are provided, must appear after the **join** (or **from**) clause, and both must appear before any **where** clause that exists on the same **join** clause. We recommend that all **group by**, **order by**, and **where** clauses appear immediately after the last **join** clause.

    CustTable xrecCustTable;
    CashDisc xrecCashDisc;
    struct sut4;
    sut4 = new struct("str AccountNum_Count; str CashDisc; str Description");
    while select count(AccountNum)
        from xrecCustTable
        order by xrecCashDisc.Description
        join xrecCashDisc
            group by xrecCashDisc.CashDiscCode
                where xrecCustTable.CashDisc ==
                    xrecCashDisc.CashDiscCode
                    && xrecCashDisc.Description LIKE "*Days*"
        {
            sut4.value("AccountNum_Count", xrecCustTable.AccountNum );
            sut4.value("CashDisc", xrecCashDisc.CashDiscCode );
            sut4.value("Description", xrecCashDisc.Description );
            info(sut4.toString());
        }
    /*********  Actual Infolog output
    Message (02:45:26 pm)
    (AccountNum_Count:"2"; CashDisc:"0.5%D10"; Description:"")
    (AccountNum_Count:"3"; CashDisc:"0.5%D30"; Description:"")
    (AccountNum_Count:"4"; CashDisc:"1%D07"; Description:"")
    (AccountNum_Count:"1"; CashDisc:"1%D15"; Description:"")
    (AccountNum_Count:"1"; CashDisc:"2%D30"; Description:"")
    (AccountNum_Count:"1"; CashDisc:"3%D10"; Description:"")
    *********/
    }

### select statement that has an outer join

The **select** statement supports filtering an outer join in the **where** clause. In the **join** clause of standard SQL, there is an **on** keyword for filter criteria. However, this keyword isn't supported in X++. An inner join rejects all table rows that don't match a row in the other joined table. However, an outer join includes rows from the first table, even if there is no matching row in the other joined table. Default values are substituted for the data that couldn't be obtained from a matching row in the other joined table. You can filter an outer join at the equivalent of an **on** clause that is part of the **join** clause. For an inner join, the behavior if you filter on an **on** clause is the same as the behavior if you filter on the **where** clause.

#### select statement example

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

    static void SelectOuterJoinExample(Args _args)
    {
        SalesOrder recSalesOrder;
        SalesOrderLine recSalesOrderLine;
        struct struct4;

        struct4 = new struct
            ("int SalesOrderID;"
            + "date DateAdded;"
            + "str SalesOrderLineID;"
            + "int Quantity"
            );
        while
        select
            *
            from
                recSalesOrder
                OUTER JOIN recSalesOrderLine
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
    /*********  Actual Infolog output (with break spaces entered in between each output)
    (SalesOrderID:1;
    DateAdded:2010/1/1;
    SalesOrderLineID:"CC";
    Quantity:66)
    (SalesOrderID:2;
    DateAdded:2010/2/2;
    SalesOrderLineID:"";
    Quantity:0)
    *********/

## while select statements
A **while select** statement is used to handle data. It's the most widely used form of the **select** statement. The **while select** statement loops over many records that meet specific criteria, and can run a statement on each record. Typically, when you use the **while select** statement for data manipulation, you do it in a transaction to ensure data integrity. The results of a **while select** statement are returned in a table buffer variable. If you use a field list in the **select** statement, only those fields are available in the table variable. If you use aggregate functions, such as **sum** or **count**, the results are returned in the fields that you perform the **sum** or **count** over. You can count, average, or sum only integer and real fields. The syntax of a **while select** statement resembles the syntax of a **select** statement, but the statement is preceded by **while select** instead of **select**. The **select** statement itself is run only one time, immediately before the first iteration of the statements in the loop. Any Boolean expressions (such as **iCounter &lt; 1**) that are added to the **while select** are tested only one time. This behavior differs from the behavior of the **while** statement in languages such as C++ and C\#. For example, the following loop can have more than one iteration.

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

### while select example

The following example prints the name reference and telephone number of every customer in the CustTable table whose account number is within a specified range.

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

### while select example

The following example uses the **forUpdate** keyword.

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

### Deleting a set of records

You can use a **while select** statement to loop over a set of records that meet some criteria, and perform an action on each record. In the following example, the statement is used to delete a set of records.

    TableName myXrec;
    while select myXrec where conditions // conditions is a Boolean variable defined elsewhere.
    {
        myXrec.delete();
    }

You can achieve the same effect by using the **delete\_from** keyword.

    TableName myXrec;
    delete_from myXrec where conditions; // conditions is a Boolean variable defined elsewhere.

### select statements on fields

You can use a **select** statement in a lookup on a field. After a **select** statement that fetches a record in a table, you can enter **.fieldName** to reference a field in the table. These **select** statements must be used in expressions. A *normal **select** statement* differs from a *field **select** statement*:

-   The field **select** statement operates directly on a table.
-   The normal **select** statement operates on a table buffer variable.

### select field example

    void selectFieldExamples ()
    {
        // Prints the NameRef field from the selected customer
        print (select CustTable order by AccountStatement).AccountStatement;

        // Uses the balance field from the customer with AccountNum 3000
        if ((select custTable where CustTable.AccountNum == '3000').CreditMax < 50000)
            print "This customer has a credit maximum less than $50,000.";
    }

### Aggregate functions: Differences between X++ and SQL

In industry-standard SQL, a database query can contain *aggregate functions*. Examples include **count(RecID)** and **sum(columnA)**. When an aggregate function is used, but no rows match the **where** clause, a row must be returned to hold the result of the aggregates. The row that is returned shows the value **0** (zero) for the **count** function and **null** for the **sum** function. X++ doesn't support the concept of **null** values for the database. Therefore, in cases where the **sum** function will return **null**, no row is returned to the user. Additionally, every data type has a specific value that is treated as a **null** value in some circumstances.

### index and order by keywords in select statements

You use the **order by** keyword in **select** statements to order the data that is returned. Use the **index hint** keyword to specify the index that should be used in the query and to sort the selected records in the manner that is defined by the index. Indexes optimize the selection of records. To select records in a specific order, combine the **index hint** keyword with an **order by** expression. If you want the output to be sorted in reverse order, use the **reverse** keyword. If a table index has been disabled (that is, if the index's **Enabled** property is set to **No**), the **select** statement that references the index is still valid. However, the database can't use the index as a hint to sort the data, because the index doesn't exist in the database. The following table shows how to use the **index hint** and **order by** keywords in **select** statements.

| Task                                                                                 | Use                                             |
|--------------------------------------------------------------------------------------|-------------------------------------------------|
| Select records when the order isn't significant.                                     | select .. where ...                             |
| Select records when the order is significant.                                        | select .. order by ... where ...                |
| Select records, and force a specific index to be used.                               | select .. index hint ... where ...              |
| Select records when the order is significant, and force a specific index to be used. | select .. index hint ... order by ... where ... |

### index and order by example

The following example shows how to select transactions from the SalesTable table, based on a range of customers and due dates.

    SalesTable salesTable;
        select salesTable
        index hint CustIdx
        order by CustAccount
        where salesTable.CustAccount >= '3000'
            && salesTable.CustAccount <= '4000'
            && salesTable.FixedDueDate >= 12\12\2004
            && salesTable.FixedDueDate <= 05\05\2009;

### index hint

Before you can use **index hint** in queries, you must specify that hints can be used on the server.

1.  Go to **Start** &gt; **Administrative Tools** &gt; **Microsoft Dynamics AX Server Configuration**.
2.  On the **Database Tuning** tab, select **Allow INDEX hints in queries**, and then click **OK**.
3.  When a message box prompts you to restart the Application Object Server (AOS) service, click **Yes**. Index hints won't be enabled until the service is restarted.

When an **index hint** in a **select** statement refers to a non-clustered index, and the **where** clause contains only the fields that are found in a clustered index on the same table, the clustered index is used instead of the index that is specified in the hint. For example, you run **sp\_helpindex InventTable** in SQL Server Management Studio and you see that the InventTable table has a clustered index on the **DataAreaId** and **ItemId** columns, and a non-clustered index on the **DataAreaId**, **ItemProductId**, and **ItemType** columns.

| Index name       | Description                                        | Key columns                         |
|------------------|----------------------------------------------------|-------------------------------------|
| I\_175ITEMIDX    | Clustered, unique, primary key, located on PRIMARY | DATAAREAID, ITEMID                  |
| I\_175PRODUCTIDX | Non-clustered, located on PRIMARY                  | DATAAREAID, ITEMPRODUCTID, ITEMTYPE |

In the following code, the clustered index is used instead of the non-clustered index that is specified by **index hint**.

    static void IndexHint(Args _args)
    {
        InventTable inv;
        select * from inv index hint GroupItemIdx
            where inv.ItemId == 'B-R14';
    }

### Writing a select statement as an expression

You can use a **select** statement as an expression. This type of **select** statement is known as an *expression **select** statement*. A table buffer variable can't be used in an expression **select** statement. The name of the table must be used in the **from** clause. One limitation of expression **select** statements is that the **join** keyword isn't supported in an expression join.

### expression select examples

In the following example, the **select** statement inside the parentheses returns one row. The only column that can be populated with data is the column that is named before the **from** clause in the **select** clause. After the closing parenthesis, the name of that column is used to reference the data value: **).AccountNum;**. This example returns a maximum of one row, because it uses the **firstonly** keyword. However, the value that is assigned to **sAccountNum** is the same, even if the **firstonly** keyword is omitted. The **where** clause in this example serves no purpose except to show that the **where** clause must occur after the **order by** clause. The table name can't be used to qualify a field name in the **order by** clause.

    int64 nRecId, nCount;
    str sAccountNum, sName;
    sAccountNum = (select firstonly AccountNum from CustTable
        order by AccountNum desc
        where 0 == 0 // 'where' must occur after 'order by'. )
        .AccountNum;
    info(strFmt("Test_1.a: %1", sAccountNum));

Here is a simpler way to achieve the same result as the previous example.

    /********* Actual Infolog output
     Test_1.a: 4507Test_1.b: 4507
     *********/

    int64 nRecId, nCount;
    str sAccountNum, sName;
    sAccountNum = (select maxof(AccountNum) from CustTable).AccountNum;
    info(strFmt("Test_1.b: %1", sAccountNum));

The following example includes a **where** clause. In a **where** clause, the table name must be used as a qualifier of the field. Here, the **maxof** aggregate function is used, and the **RecId** field is mentioned in the function. The field that is mentioned in the aggregate function must be the same as the field name that is used to reference the data value after the closing parenthesis. Otherwise, empty data is returned.

    int64 nRecId, nCount;
    str sAccountNum, sName;
    nRecId = (select maxof(RecId) from CustTable
        where CustTable.Blocked == CustVendorBlocked::No)
        .RecId;
    info(strFmt("Test_2.c: %1", nRecId));

    /********* Actual Infolog output
    Test_2.c: 5637144604
    *********/

In the following example, a field name (in this case, **RecId**) is used to reference a data value that isn't a **RecId** value. The **count** aggregate function doesn't return a **RecId** value. Typically, the **RecId** field is used with the **count** function.

    int64 nRecId, nCount;
    str sAccountNum, sName;
    nRecId = (select count(RecId) from CustTable
        where CustTable.Blocked == CustVendorBlocked::No)
        .RecId;
    info(strFmt("Test_2.d: %1", nRecId));

    /********* Actual Infolog output
    Test_2.d: 29
    *********/

The **join** keyword isn't supported in expression **select** statements. The following example shows a subselect. However, expression select **statements** don't support subselects that are equivalent to a standard inner join. Therefore, the following example doesn't compile, because it mentions two tables inside one expression **select** statement (that is, inside the subselect). As this example shows, subselects are supported, but only in a limited manner.

    // This job does not compile.
    static void BadJob(Args _args)
    {
        sName = (select Name from AssetTable
            where AssetTable.AssetId ==
                // Here starts the subselect.
                (select AssetId from AssetTrans
                    where AssetTrans.AssetId ==
                        AssetTable.AssetId // Compiler rejects this line.
                ).AssetId).Name;
        info(strFmt("Test_3: %1", sName));
    }

    /********* Actual Infolog output
    Test_3: CNC-Metal shade
    *********/

## update method
The **update** table method updates the current record with the contents of the buffer. It also updates the appropriate system fields. The **where** clause is optional. When it's used, the **where** clause specifies a condition that **update** tests as it processes each row of the table. Only those rows that test **true** against the condition are updated with the new values. The **update\_recordset** operator is a record set–based operator that updates multiple records at the same time. To override the behavior of **update**, use the **doUpdate** method. The following example selects the custTable table for update. Any records where the value of the **AccountNum** field is equal to **4000** are updated. (In this case, only one record is updated.) The value of the **CreditMax** field is changed to **5000**.

    CustTable custTable;
    ttsBegin;
        select forUpdate custTable
        where custTable.AccountNum == '4000';
        custTable.CreditMax = 5000;
        custTable.update();
    ttsCommit;

## doUpdate method
The **doUpdate** method updates the current record with the contents of the buffer. This method also updates the appropriate system fields. You should use the **doUpdate** method when the **update** method on the table must be bypassed. The syntax for a **doUpdate** table method is **void doUpdate()**. In the following example, the value of the **CreditMax** field is increased by 1,000.

    static void Job1(Args _args)
    {
        CustTable custTable;
        ttsBegin;
        select forUpdate custTable
        where custTable.CreditMax == 3000;
        if (custTable)
        {
            custTable.CreditMax += 1000;
            custTable.doUpdate();
        }
        ttsCommit;
    }

## delete method
The **delete** table method deletes the current record from the database. To use this method, use a **where** clause to specify the rows to delete. One record at a time is then removed from the specified table. The **delete\_from** operator is a record set–based operator that removes multiple records at the same time. The **delete** method can be overridden. For example, you might want to add extra validation before records are deleted. If you override the **delete** method, you can run the original (base) version of the **delete** method by calling the **doDelete** method. Therefore, a call to the **doDelete** method is equivalent to a call to **super()** in the **delete** method. In the following example, all records in the MyTable table that satisfy the criterion in the **where** clause (that is, all records where the value of the **AccountNum** field is equal to **1000**) are deleted from the database. One record is deleted at a time.

    ttsBegin;
    while select forUpdate myTable
        where myTable.AccountNum == '1000'
    {
        myTable.delete();
    }
    ttsCommit;

## doDelete method
Like the **delete** table method, the **doDelete** table method deletes the current record from the database. Use the **doDelete** method if the **delete** table method has been overridden, and you want to run the original (base) version of the **delete** method instead of the overridden version. Therefore, a call to the **doDelete** method is equivalent to a call to **super()** in the **delete** method. The following example deletes all records in the myTable table that have an account number that is more than or equal to **200**.

    ttsBegin;
    while select forUpdate myTable
        where myTable.AccountNum >='200';
    {
        myTable.doDelete();
    }
    ttsCommit;

## insert method
The **insert** method updates one record at a time. To insert multiple records at a time, use array inserts, **insert\_recordset**, or **RecordSortedList.insertDatabase**. To override the behavior of the **insert** method, use the **doInsert** method. The **xRecord .insert** method generates values for the **RecId** field and system fields, and then inserts the contents of the buffer into the database. Here is how the **insert** method works:

-   Only the specified columns of the rows that have been selected by the query are inserted into the named table.
-   The columns of the table that is copied from and the columns of the table that is copied to must be type-compatible.
-   If the columns of both tables match in type and order, column list can be omitted from the **insert** clause.

### insert example: Inserting a new record

The following example inserts a new record into the CustTable table. The **AccountNum** field of the new record is set to **5000**, and the **Name** field is set to **MyCompany**. (Other fields in the record will be blank.)

    CustTable custTable;
    ttsBegin;
    select forUpdate custTable;
    custTable.AccountNum = '5000';
    custTable.insert();
    ttsCommit;

### insert example: Transaction and duplicate key

The following example shows how you can catch a **DuplicateKeyException** exception in the context of an explicit transaction. The exception is thrown when a call to **xRecord .insert** fails because an existing unique value is duplicated. In the **catch** block, your code can either take corrective action or log the error for later analysis. Your code can then continue without losing all the pending work of the transaction. You can't catch a duplicate key exception that is caused by a set-based operation such as **insert\_recordset**. This example depends on two tables: TableNumberA and TableNumberB. Both tables have one mandatory integer field. These fields are named **NumberAKey** and **NumberBKey**, respectively. A unique index is defined on each key field. The TableNumberA table must have at least one record in it.

    static void JobDuplicKeyException44Job(Args _args)
    {
        TableNumberA tabNumA; // Has one record, key = 11.
        TableNumberB tabNumB;
        int iCountTries = 0, iNumberAdjust = 0, iNewKey, ii;
        container ctNotes;
        // Empty the B table.
        delete_from tabNumB;
        // Insert a copy of one record.
        insert_recordset tabNumB (NumberBKey)
        select firstOnly NumberAKey from tabNumA order by NumberAKey asc;
        ttsBegin;
        try
        {
            iCountTries++;
            ctNotes += strFmt("---- Inside the try block, try count is %1. ----", iCountTries);
            while select * from tabNumA order by NumberAKey asc
            {
                tabNumB .clear();
                iNewKey = tabNumA .NumberAKey + iNumberAdjust;
                tabNumB .NumberBKey = iNewKey;
                ctNotes += strFmT ("-- %1 is the key to be tried. --" ,iNewKey);
                tabNumB .insert();
                ctNotes += "-- .insert() successful. --";
                break; // Keeps demo simple.
            }
            ttsCommit;
        }
        catch (Exception ::DuplicateKeyException, tabNumB) // Table is optional.
        {
            ctNotes += "---- Inside the catch block. ----";
            ctNotes += infolog .text();
            if (iCountTries <= 1)
            {
                ctNotes += "-- Will issue retry. --";
                iNumberAdjust = 1;
                retry; // Erases Infolog.
            }
            else
            {
                ctNotes += "-- Aborting the transaction. --";
                ttsAbort;
            }
        }
        for (ii=1; ii <= conLen(ctNotes); ii++)
        {
            info(conPeek(ctNotes ,ii));
        }
    }

    /*********Actual Infolog output
            Message (10:53:13 am)
        ---- Inside the try block, try count is 1. ----
        -- 11 is the key to be tried. --
        ---- Inside the catch block. ----
        Cannot create a record in TableNumberB (TableNumberB).
        The record already exists.
        -- Will issue retry. --
        ---- Inside the try block, try count is 2. ----
        -- 12 is the key to be tried. --
        -- .insert() successful. --
    *********/

## doInsert method
The **doInsert** method generates values for the **RecId** field and other system fields, and then inserts the contents of the buffer into the database. Use this method when the **insert** method on the table must be bypassed. In the following example, a new record is inserted. The **name** field of the record is set to **Warren Langer**, and the **value** field is set to **100**.

    ttsBegin;
    myTable.name = 'Warren Langer';
    myTable.value = 100;
    myTable.doInsert();
    ttsCommit;

## Transactional integrity
If steps aren't taken to help guarantee the integrity of transactions, data corruption could occur. At the very least, you might experience poor scalability with respect to concurrent users on the system. Two internal checking features help guarantee the integrity of transactions: the **forUpdate** check and the **tssLevel** check. A **forUpdate** check helps guarantee that a record can be updated or deleted only if it has first been selected for update. You can select a record for update by using either the **forUpdate** keyword in the **select** statement or the **selectForUpdate** method on tables. A **ttsLevel** check helps guarantee that a record can be updated or deleted only within the same transaction scope where it was selected for update. The following statements are used to help guarantee integrity:

-   **ttsBegin** – This statement marks the beginning of a transaction. It helps guarantee data integrity, and also helps guarantees that all updates that are done until the transaction ends (through **ttsCommit** or **ttsAbort**) are consistent (all or none).
-   **ttsCommit** – This statement marks the successful end of a transaction. It ends and commits a transaction. Microsoft Dynamics 365 for Operations helps guarantee that a transaction that has been committed will be performed according to intentions.
-   **ttsAbort** – This statement lets you explicitly discard all changes in the current transaction. In this case, the database is rolled back to the original state where nothing has been changed. Typically, you use this statement if you've detected that the user wants to break the current job. The **ttsAbort** statement helps guarantee that the database is consistent.

Usually, it's a better idea to use exception handling instead of **ttsAbort**. The **throw** statement automatically aborts the current transaction. As the following example shows, statements between **ttsBegin** and **ttsCommit** can include one or more transaction blocks. In these cases, nothing is actually committed until the successful exit from the final **ttsCommit** statement.

    ttsBegin;
        // Some statements.
    ttsBegin;
        // More statements.
    ttsCommit;
    ttsCommit;

The following example selects a set of records and updates the **NameAlias** field.

    Custtable custTable;
    ttsBegin;
    select forUpdate custTable where custTable.AccountNum == '4000';
    custTable.NameAlias = custTable.Name;
    custTable.update();
    ttsCommit;

### Example of code that is rejected by the two transaction integrity checks

In this example, the first failure occurs because the **forupdate** keyword is missing. The second failure occurs because the transaction scope of the update differs from the transaction scope where the record was selected for update in **ttsCommit**.

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

## Speeding up SQL operations
The following constructs let you insert, update, or delete multiple records. By using these constructs, you reduce communication between the application and the database, and therefore help increase performance. In some situations, record set–based operations can fall back to record-by-record operations.

| Construct         | Description                                                                                                                                                                                                      |
|-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| RecordSortedList  | Insert multiple records in one database trip. Use this construct when you want a subset of data from a specific table, and you want that data to be sorted in an order that doesn't currently exist as an index. |
| RecordInsertList  | Insert multiple records in one database trip. Use this construct when you don't have to sort the data.                                                                                                           |
| insert\_recordset | Copy multiple records directly from one or more tables into another table in one database trip.                                                                                                                  |
| update\_recordset | Update multiple rows in a table in one database trip.                                                                                                                                                            |
| delete\_from      | Delete multiple records from the database in one database trip.                                                                                                                                                  |

## insert\_recordset
The **insert\_recordset** statement copies data directly from one or more source tables into one destination table in one server trip. It's faster to use **insert\_recordset** than an array insert. However, array inserts are more flexible if you want to handle the data before you insert it. **insert\_recordset** is a record set–based operator that performs operations on multiple records at a time. However, it can fall back to record-by-record operations in many situations.

### insert\_recordset syntax

*ListOfFields* in the destination table must match the list of fields in the source tables. Data is transferred in the order in which it appears in the list of fields. Fields in the destination table that aren't present in the list of fields are assigned **0** (zero) values, as in other areas. System fields, such as **RecId**, are assigned transparently by the kernel in the destination table. **insert\_recordset** *DestinationTable* **(** *ListOfFields* **)** **select** *ListOfFields1* **from** *SourceTable* **\[ where** *WhereClause* **\]** **\[ join** *ListOfFields2* **from** *JoinedSourceTable* **\[ where** *JoinedWhereClause* **\]\]**

### Example: Inserting data from another table

In this example, the **myNum** and **mySum** records are retrieved from the anotherTable table and inserted into the myTable table. The records are grouped according to **myNum**, and only **myNum** records that have a value that is less than or equal to **100** are included in the insertion.

    insert_recordset myTable (myNum, mySum)
        select myNum, sum(myValue)
            from anotherTable
            group by myNum
            where myNum <= 100;

### Example: Inserting data from variables

The following example shows that the **insert\_recordset** statement can insert data that is provided in variables. In this example, the **firstonly** keyword is used so that only one row is inserted. Literals, such as **128** or **"this literal string"**, can't be used as a source of data that is inserted.

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

### Example: Inserting data by using a join

The following example shows a join of three tables on an **insert\_recordset** statement that has a subselect. It also shows a **while** **select** statement that has a similar join. A variable is used to supply the inserted value for one column. The **str** variable must be declared, and must have a length that is less than or equal to the maximum length of the corresponding database field. In this example, there is an **insert\_recordset** statement for the tabEmplProj5 table. One of the target fields is named **Description**, and the field's data comes from the local variable **sDescriptionVariable**. The **insert\_recordset** statement succeeds even when the configuration key for the **Description** field is turned off. The system ignores both the **Description** field and the **sDescriptionVariable** variable. Therefore, this code provides an example of *configuration key automation*. Configuration key automation occurs when the system can automatically adjust the behavior of an **insert\_recordset** statement that inserts data into fields that the configuration key is turned off for.

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

## update\_recordset
The **update\_recordset** statement lets you update multiple rows in one trip to the server. Therefore, the power of SQL Server can help improve the performance of some tasks. The ****update\_recordset**** statement resembles **delete\_from** in X++ and **update set** in SQL. It doesn't retrieve each record separately by fetching, changing, and updating, Instead, it works on an SQL-style record set on the database server side. If the **update** method is overridden, the implementation falls back to a classic looping construction, where one record at a time is updated. (This behavior resembles the behavior of **delete\_from** for deletions.) Therefore, the construction works on temporary tables and whole table–cached tables by using the looping construction.

### Example: Update that is based on a calculated value

The following example updates the myTableBuffer table and increments the value of the **field1** field by ten percent in all records in the table.

    MyTable myTableBuffer;
    update_recordset myTableBuffer
    setting field1 = field1 * 1.10;

### Example: Update that uses a where clause

The following example updates all records in the myTable table where the **field1** field has the value **0**. The **field1** field is assigned a new value of **1**. The **field2** field is assigned a value that is the sum of **fieldX** and **fieldY**. This example updates multiple fields at the same time, and it updates only those rows that satisfy the **where** clause.

    MyTable myTableBuffer;
    update_recordset myTableBuffer
    setting
        field1 = 1,
        field2 = fieldX + fieldY
    where field1 == 0;

### Example: Updating joined tables

The following example shows that the **update\_recordset** statement supports joins of several tables. Data from the joined tables can be used to assign values to fields in the table that is being updated.

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

## delete\_from
You can delete multiple records from a database table by using a **delete\_from** statement. This approach can be more efficient and faster than an approach that uses the **xRecord .delete** method in a loop to delete one record at a time. If you've overridden the **delete** method, the system interprets the **delete\_from** statement into code that calls the **delete** method one time for each row that is deleted.

### Example: Efficiently deleting records by using delete\_from

The following example shows an efficient way to delete multiple records.

    static void DeleteMultiRow1aJob(Args _args)
    {
        MyWidgetTable tabWidget;
        delete_from tabWidget
            where tabWidget .quantity <= 100;
    }

#### Example: Inefficiently deleting records by using forUpdate

The following example is inefficient. It issues a separate SQL **delete** call to the database server for every record. The **xRecord** **.delete** method never deletes more than one record per call.

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

### Example: A delete operation that has an inner join

Inner joins aren't supported on the **delete\_from** statement. Therefore, you can't use the unmodified **join** keyword on the **delete\_from** statement. However, you can logically accomplish an inner join by using other techniques. The following example shows the new and old techniques for achieving inner join logic through a sequence of statements.

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

### Example: A delete operation that uses the notexists join keyword

You can use the **notexists join** keyword pair in a **delete\_from** statement. The **delete\_from** statements in the following example are efficient. The **notexists join** clause enables the **delete\_from** statement to delete a specific set of rows. In this example, the **delete\_from** statement removes all parent-order header rows that there are no child-order line rows for. You can also use the **exists join** clause on the **delete\_from** statement.

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

## Maintain fast SQL operations
There are situations where record set–based operations can be converted to slower record-by-record operations. The following table identifies these situations.

| Situation                                                                    | DELETE\_FROM | UPDATE\_RECORDSET | INSERT\_RECORDSET | ARRAY\_INSERT | Use this setting for overrides |
|------------------------------------------------------------------------------|--------------|-------------------|-------------------|---------------|--------------------------------|
| Non-SQL tables                                                               | Yes          | Yes               | Yes               | Yes           | Not applicable                 |
| Delete actions                                                               | Yes          | No                | No                | No            | **skipDeleteActions**          |
| The database log is enabled.                                                 | Yes          | Yes               | Yes               | No            | **skipDatabaseLog**            |
| Overridden method                                                            | Yes          | Yes               | Yes               | Yes           | **skipDataMethods**            |
| Alerts are set up for the table.                                             | Yes          | Yes               | Yes               | No            | **skipEvents**                 |
| The **ValidTimeStateFieldType** property on a table isn't equal to **None**. | Yes          | Yes               | Yes               | Yes           | Not applicable                 |

You can use the settings that are shown in the last column to explicitly skip or ignore one or more factors that adversely affect performance. If, for some reason, one of the previously mentioned SQL operations is downgraded to a record-by-record operation, all the **skip\*** settings are also ignored. For example, in the following code, the **insert** method on the myTable table is run, even though it's explicitly stated that this method should be skipped if a container or memo field is defined for myTable.

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

