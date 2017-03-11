---
# required metadata

title: X++ data selection and manipulation
description: This topic describes the X++ language support for data selection and manipulation.
author: RobinARH
manager: AnnBe
ms.date: 2016-08-27 00 - 35 - 54
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 150273
ms.assetid: 999a5ecf-559b-4d66-8b05-9a8e477e0518
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# X++ data selection and manipulation

This topic describes the X++ language support for data selection and manipulation.

You can use SQL statements either interactively or within source code, to access and retrieve data that is stored in the database. You use the following statements for data manipulation:

-   **select:** selects the data that you want to modify.
-   **insert:** adds one or more new records into a table.
-   **update:** modifies data in existing table records.
-   **delete:** removes existing records from a table.

Before any data can be changed, you must select the data for update for update by using a **select** statement. The **select forUpdate** command selects records exclusively for update. The **insert**, **update**, and **delete** methods perform operations on only one record at a time. The **array insert**, **insert\_recordset**, **RecordInsertList,** and **update\_recordset** statements perform operations on multiple records at a time.

## select statement
The **select** statement fetches or manipulates data from the database. All **select** statements use a table variable to fetch records. This variable must be declared before a **select** statement can be executed. The **select** statement only fetches one record, or field. To fetch additional records, you can use the **next** statement. The **next** statement fetches the next record in the table. If you use **next** without a preceding **select** command, an error occurs. Do not use **next** with the **firstOnly** find option. If you need to traverse a number of records, it is more appropriate to use a **while** **select** statement. The results of a **select** statement are returned in a table buffer variable. If you use a field list in the **select** statement, only those fields are available in the table variable. If you use aggregate functions, such as **sum** or **count**, the results are returned in the fields that you perform the **sum** or **count** over. You can only count, average, or sum the integer and real fields.

## select statement syntax
|                   |     |                                                                                                                                                                                                                                                                                                    |
|-------------------|-----|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| *SelectStatement* | =   | **select** *Parameters*                                                                                                                                                                                                                                                                            |
| *Parameters*      |     | **\[ \[**  *FindOptions*  **\]** **\[**  *FieldList*  **from \] \]** *TableBufferVariable* **\[** *IndexClause* **\]** **\[**  *Options*  **\]** **\[**  *WhereClause*  **\]** **\[**  *JoinClause*  **\]**                                                                                        |
| *FindOptions*     | =   | **crossCompany** | **reverse** | **firstFast** | \[ **firstOnly** | **firstOnly10** | **firstOnly100** | **firstOnly1000** \] | **forUpdate** | **noFetch** | \[**forcePlaceholders** | **forceLiterals**\] | **forceselectorder** | **forceNestedLoop** | **repeatableRead** | **validTimeState** |
| *FieldList*       | =   | *Field*  **{ ,**  *Field*  **}** | **\***                                                                                                                                                                                                                                                          |
| *Field*           | =   | *Aggregate*  **(**  *FieldIdentifier*  **) |**  *FieldIdentifier*                                                                                                                                                                                                                                  |
| *Aggregate*       | =   | **sum** | **avg** | **minof** | **maxof** | **count**                                                                                                                                                                                                                                              |
| *Options*         | =   | **\[ order by** , **group by ,**  *FieldIdentifier*  **\[ asc** | **desc \] { ,**  *FieldIdentifier*  **\[ asc** | **desc \] }\]** | **\[**  *IndexClause*  **\]**                                                                                                                                 |
| *IndexClause*     | =   | **index**  *IndexName* | **index hint**  *IndexName*                                                                                                                                                                                                                                               |
| *WhereClause*     | =   | **where**  *Expression*                                                                                                                                                                                                                                                                            |
| *JoinClause*      | =   | \[**exists** | **notexists** | **outer** \] **join**  *Parameters*                                                                                                                                                                                                                                 |

### Keywords used in the select statement

| Keyword               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **asc**               | An option on the **order by** or **group by** clause to specify an ascending sort. If neither asc or desc is specified, then the sort is ascending.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **avg**               | Returns the average of the fields.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **count**             | Rreturns the number of records.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| **crossCompany**      | Returns data for all companies that the user is authorized to read from. A **container** can be added to reduce the number of companies involved.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **desc**              | An option on the **order by** or **group by** clause to specify a descending sort. If neither asc or desc is specified, then the sort is ascending.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **exists**            | A method that returns a Boolean value and a **join** clause.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **firstFast**         | A priority hint. The first row appears more quickly but the total return time for this option might be slower. The **firstFast** hint is automatically issued from all forms.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **firstOnly**         | Speeds up the fetch by returning only the first row.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **firstOnly10**       | The same as **firstOnly**, except returns 10 rows instead of one.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **firstOnly100**      | The same as **firstOnly**, except returns 100 rows instead of one.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **firstOnly1000**     | The same as **firstOnly**, except returns 1000 rows instead of one.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **forceLiterals**     | Instructs the kernel to reveal the actual values that are used in **where** clauses to the Microsoft SQL Server database at the time of optimization. **forceLiterals** and **forcePlaceholders** are mutually exclusive. You should not to use the **forceLiterals** keyword in **select** statements, because it could expose code to an SQL injection security threat.                                                                                                                                                                                                                                                                                                                      |
| **forceNestedLoop**   | Forces the Microsoft SQL Server database to use a nested-loop algorithm to process a particular SQL statement containing a join algorithm. This means that a record from the first table is fetched before any records from the second table are fetched. Typically, other join algorithms, such as hash-joins and merge-joins, would be considered. This keyword is often combined with the **forceSelectOrder** keyword.                                                                                                                                                                                                                                                                     |
| **forcePlaceholders** | Instructs the kernel not to reveal the actual values used in **where** clauses to the SQL Server database at the time of optimization. This is the default in all statements that are not **join** statements.The advantage of using this keyword is that the kernel can reuse the access plan for other similar statements with other search values. The disadvantage is that the access plan is computed without taking into consideration that data distribution might not be even. The access plan is an on-average access plan. **forcePlaceholders** and **forceLiterals** are mutually exclusive.                                                                                       |
| **forceSelectOrder**  | Forces the SQL Server database to access the tables in a join in the specified order. If two tables are joined, the first table in the statement is always accessed first. This keyword is often combined with **forceNestedLoop.**                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **forUpdate**         | Selects records exclusively for update. Depending on the underlying database, the records may be locked for other users.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| **group by**          | Instructs the database to group selected records by fields.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| **index**             | Instructs the database to sort the selected records as defined by the index.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **index hint**        | Gives the database a hint to use this index to sort the selected records as defined by the index. The database can ignore the hint. A wrong index hint can have a big performance impact. Index hints should only be applied to SQL statements that do not have dynamic **where** clauses or **order by** clauses, and where the effect of the hint can be verified.                                                                                                                                                                                                                                                                                                                           |
| **join**              | Used to join tables on a column that is common to both tables. The join criteria are specified in where clause because there is no **on**. Reduces the number of SQL statements that are needed if you want to loop through a table and update transactions in a related table. For example, if you process 500 records in a table, and want to update related records in another table, and use a nested **while select** to do this, there will be 501 trips to the database. If you use a **join**, there will be a single trip to the database.                                                                                                                                            |
| **maxof**             | Returns the maximum of the fields.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **minof**             | Returns the minimum of the fields.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **noFetch**           | Indicates that no records are to be fetched at present. This is typically used when the result of the select is passed on to another application object, for example, a query that performs the actual fetch.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **notExists**         | Is chosen only if there are no posts.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **optimisticLock**    | Forces a statement to run with optimistic concurrency control even if a different value is set on the table.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **order by**          | Instructs the database to sort the selected records by fields in **order by** list.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **outer**             | Returns all rows from the first-named table, including rows that have no match in the second-named table. This is a left outer join, although there is no **left**. There is no right outer join.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **pessimisticLock**   | Forces a statement to run with pessimistic concurrency control even if a different value is set on the table.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **repeatableRead**    | Specifies that no other transactions can modify data that has been read by logic inside the current transaction, until after the current transaction completes. An explicit transaction completes at either **ttsAbort** or at the outermost **ttsCommit**. For a stand-alone **select** statement, the transaction duration is the duration of **select** command. However, the database sometimes enforces the equivalent of **repeatableRead** in individual **select** statements even without this keyword appearing in your code (depending on how the database decides to scan the tables). For more information, see the documentation for the underlying relational database product. |
| **reverse**           | Records are returned in reverse order.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **sum**               | Returns the sum of the fields. Can be used to sum all accounts, order lines, and so on.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **validTimeState**    | Filters rows from a table that has its **ValidTimeStateFieldType** property set to a value other than **None.**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

#### Keyword code examples

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
    while select ledgerTable    join ledgerTrans
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
The following examples demonstrate how you can use the **select** statement.

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
     
    // Customer with higest account number
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

### join code example

This code example shows how an inner **join** can be performed as part of an SQL **select** statement. The example also shows an order by clause that has each field qualified by a table name. This enables you to control how the retrieved records are sorted by using only one order by clause.

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

### group by and order by code example

This code example shows that the fields in the **group by** clause can be qualified with a table name. There can be multiple **group by** clauses instead of just one. The fields can be qualified by table name in only one **group by** clause. Use of table name qualifiers is recommended. The **order by** clause follows the same syntax patterns that group by follows. If provided, both clauses must appear after the **join** (or **from**) clause, and both must appear before the **where** clause that might exist on the same **join**. It is recommended that all group by and order by and **where** clauses appear immediately after the last **join** clause.

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

### select statement with an outer join

The **select** statement supports filtering an **outer join** in the **where** clause. In the **join** clause of standard SQL there is an **on** keyword for filter criteria, but that isn't supported in X++. An inner join rejects all table rows that fail to match a row in the other joined table. But an outer join includes rows from the first table even though there is no matching row in the other joined table. Default values are substituted for the data that could not be obtained from a matching row in the other joined table. You can filter an outer join at the equivalent of an **on** clause that is part of the **join** clause. For an inner join there is no behavioral difference between filtering on an **on** clause versus on the **where** clause.

#### select statement code example

This code example is based on two tables. The field types and example data are included. There is a 1-to-many relationship between the **SalesOrder** parent table and the **SalesOrderLine** child table. There are 0 or more rows in the **SalesOrderLine** table for each row in the **SalesOrder** table. There are two rows in the **SalesOrder** table.

| **SalesOrderID** (integer, primary key) | **DateAdded** (date) |
|-----------------------------------------|----------------------|
| 1                                       | 2010-01-01           |
| 2                                       | 2010-02-02           |

The **SalesOrderLine** table contains a foreign key field, named **SalesOrderID**, that references the primary key column of the **SalesOrder** table. The **SalesOrderID** value **2** does not occur in the data for **SalesOrderLine** table.

| **SalesOrderLineID** (string, primary key) | **Quantity** (integer) | **SalesOrderID** (integer, foreign key) |
|--------------------------------------------|------------------------|-----------------------------------------|
| AA                                         | 32                     | 1                                       |
| BB                                         | 67                     | 1                                       |
| CC                                         | 66                     | 1                                       |

The code example has a **select** statement that reads the tables which are described in the previous section. The **select** statement includes a left **outer join** clause. The join criteria and the data filter are both on the **where** clause. The output from the code example is also in this section. The second record in the output has a **SalesOrderID** value of 2. That value of 2 is not present in the **SalesOrderLine** table. Therefore, some of the fields in the second record have default values, namely 0 for an integer and a zero length string for a string.

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
**while select** statements are used to handle data. They are the most widely used form of the select statement. **while select** loops over many records (meeting certain criteria) and can execute a statement on each record. When you perform data manipulation by using the **while select** statement, you would typically do this in a transaction to ensure data integrity. The results of a **while select** statement are returned in a table buffer variable. If you use a field list in the **select** statement, only those fields are available in the table variable. If you use aggregate functions such as **sum** or **count**, the results are returned in the fields you perform the **sum** or **count** over. You can only count, average, or sum the integer and real fields. The syntax of a **while select** statement resembles that of a **select** statement except that it is preceded by **while select** instead of **select**. The **select** statement itself is executed only one time, immediately before the first iteration of the statements in the loop. Any Boolean expressions (such as **iCounter &lt; 1**) added to the **while select** are tested only one time. This differs from how the **while** statement behaves in languages such as C++ and C\#. For example, the following loop could iterate more than one time.

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

### while select code example

This prints the name reference and telephone number of customers in **CustTable** who have an account number within a specified range.

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

### while select Code Example

This code example uses the **forUpdate** keyword.

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

You can use a **while select** statement to loop over a set of records that meet some criteria and perform an action on each record. One such action is to **delete** a set of records. For example:

    TableName myXrec;    
    while select myXrec where conditions  // conditions is a Boolean variable defined elsewhere.
    {      
        myXrec.delete();    
    }

You can achieve the same effect using the **delete\_from** keyword.

    TableName myXrec;    
    delete_from myXrec where conditions;  // conditions is a Boolean variable defined elsewhere.

### select statements on fields

You can use a **select** statement in a lookup on a field. Following a **select statement** that fetches a record in a table, you can write **.fieldName** to reference a field in the table. These **select** statements must be used in expressions. There is a difference between a **normal** **select** statement and a **field select** statement:

-   The **field select** statement operates directly on a table.
-   The **normal select** statement operates on a table buffer variable.

### select field code example

    void selectFieldExamples ()
    {
        // Prints the NameRef field from the selected customer
        print (select CustTable order by AccountStatement).AccountStatement;
     
        // Uses the balance field from the customer with AccountNum 3000
        if ((select custTable where CustTable.AccountNum == '3000').CreditMax < 50000)
          print "This customer has a credit maximum less than $50,000.";
    }

### Aggregate functions: differences between X++ and SQL

In industry standard SQL, a database query can contain **aggregate functions**. Examples of such functions include **count(RecID)** and **sum(columnA)**. When an aggregate function is used but no rows match the **where** clause, a row must be returned to hold the result of the aggregates. The one returned row shows the value 0 (zero) for the **count** function, and shows **null** for the **sum** function. X++ does not support the concept of null values for the database. Therefore, when the **sum** function would return null, no row is returned to the user. Also, each data type has a specific value that is treated like a null value in certain circumstances.

### index and order by keywords in select statements

You use the **order by** keyword in your **select** statements to order the data that's returned. Use the **index** hint keywords to specify that a particular index should be used in the query and to sort the selected records as defined by the index. Indexes optimize the selection of records. Combine the index hint keyword with an order by expression to select records in a specific order. If you want the sorted output in reverse order, use the **reverse** keyword. If a table index has been disabled by setting the index's **Enabled** property to No, the **select** statement that references the index is still valid. However, the database can't use the index as a hint for how to sort the data, because the index doesn't exist in the database. The following table is an overview of how to use the index hint and order by keywords in **select** statements.

| Task                                                                                 | Use                                                             |
|--------------------------------------------------------------------------------------|-----------------------------------------------------------------|
| Select records where the order isn't significant.                                    | **select ..** **where ...**                                     |
| Select records where the order is significant.                                       | **select ..** **order by ...** **where ...**                    |
| Select records and force a specific index to be used.                                | **select ..** **index hint ...** **where ...**                  |
| Select records where the order is significant and force a specific index to be used. | **select ..** **index hint ...** **order by ...** **where ...** |

### index and order by code example

To select the transactions from the salestable based on a range of customers and due dates, use the following code.

    SalesTable salesTable;
        select salesTable
        index hint CustIdx
        order by CustAccount
        where salesTable.CustAccount >= '3000'
              && salesTable.CustAccount <= '4000'
              && salesTable.FixedDueDate >= 12\12\2004
              && salesTable.FixedDueDate <= 05\05\2009;

### index hint

To use **index hint** in queries you must first specify the use of hints on the server using the following procedure.

1.  Open Start &gt; Administrative Tools &gt; Microsoft Dynamics AX Server Configuration and select the Database Tuning tab.
2.  Select Allow INDEX hints in queries and click OK.
3.  A message box prompting you to restart the AOS service appears. Click Yes to restart the AOS service. Index hints won't be enabled until the service is restarted.

When an **index hint** in a **select** statement refers to a non-clustered index and the **where** clause contains only the fields that are found in a clustered index on the same table, the clustered index is used instead of the index specified in the hint. For example, if you run **sp\_helpindex InventTable** in SQL Server Management Studio, you see that the **InventTable** has a clustered index on the **DataAreaId** and **ItemId** columns and a non-clustered index on the **DataAreaId, ItemProductId,** and **ItemType** columns.

| Index name       | Description                                       | Key columns                         |
|------------------|---------------------------------------------------|-------------------------------------|
| I\_175ITEMIDX    | Clustered, unique, primary key located on PRIMARY | DATAAREAID, ITEMID                  |
| I\_175PRODUCTIDX | Nonclustered located on PRIMARY                   | DATAAREAID, ITEMPRODUCTID, ITEMTYPE |

In the following code the clustered index will be used instead of the non-clustered index specified by **index hint**.

    static void IndexHint(Args _args)
    {
        InventTable inv;
        
        select * from inv index hint GroupItemIdx 
            where inv.ItemId == 'B-R14';
    }

### Write a select statement as an expression

You can use a **select** statement as an expression. This is called an **expression select**. A table buffer variable cannot be used in an expression select statement. The name of the table must be used in the **from** clause. One limitation of expression selects is that the **join** keyword is not supported in an expression join.

### expression select code examples

The **select** statement inside the parentheses returns one row. The only column that can be populated with data is the column that is named in the **select** clause before the **from** clause. The name of that one column is used after the closing parenthesis to reference the data value: **).AccountNum;**.This test case returns a maximum of one row because it uses the **firstonly** keyword. However, the value that is assigned to **sAccountNum** is the same even if the **firstonly** keyword is omitted.The **where** clause in this example serves no purpose other than to show that the **where** clause must occur after the **order by** clause. The table name cannot be used to qualify a field name in the **order by** clause.

    int64 nRecId, nCount;
    str sAccountNum, sName;

    sAccountNum = (select firstonly AccountNum from CustTable 
        order by AccountNum desc 
        where 0 == 0 // 'where' must occur after 'order by'. )
        .AccountNum; 
    info(strFmt("Test_1.a: %1", sAccountNum));

This is a simpler way to achieve the same result as the previous example. /\*\*\*\*\*\*\*\*\* Actual Infolog output Test\_1.a: 4507Test\_1.b: 4507 \*\*\*\*\*\*\*\*\*/

        
    int64 nRecId, nCount;
    str sAccountNum, sName;

    sAccountNum = (select maxof(AccountNum) from CustTable).AccountNum; 
    info(strFmt("Test_1.b: %1", sAccountNum));

The following example includes a **where** clause. In a **where** clause, the table name must be used as a qualifier of the field.Here the **maxof** aggregate function is used, and the field **RecId** is mentioned in the function. The field that is mentioned in the aggregate function must be the same field name that is used to reference the data value after the closing parenthesis. Otherwise, empty data is returned.

    int64 nRecId, nCount;
    str sAccountNum, sName;

    nRecId = (select maxof(RecId) from CustTable 
        where CustTable.Blocked == CustVendorBlocked::No)
        .RecId; 
    info(strFmt("Test_2.c: %1", nRecId));
    /********* Actual Infolog output
    Test_2.c: 5637144604
    *********/

The following example demonstrates that a field name, here **RecId**, is used to reference a data value that is not a **RecId**. The **count** aggregate function does not return a **RecId** value. The **RecId** field is ordinarily used with the **count** function.

    int64 nRecId, nCount;
    str sAccountNum, sName;

    nRecId = (select count(RecId) from CustTable 
        where CustTable.Blocked == CustVendorBlocked::No)
        .RecId; 
    info(strFmt("Test_2.d: %1", nRecId));
    /********* Actual Infolog output
    Test_2.d: 29
    *********/

The **join** keyword is not supported in expression selects. The following example demonstrates a subselect. But expression selects do not support subselects that are equivalent to a standard inner join. For instance, the following code example does not compile. The problem is that it mentions two tables inside one expression select, namely inside the subselect. This code example shows that a subselect is supported, but only in a limited way.

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
The **update** table method updates the current record with the contents of the buffer. It also updates the appropriate system fields. The **where** clause is optional. When used, the **where** clause specifies a condition for **update** to test while processing each row of the table. Only those rows that test **true** against the condition are updated with the new values. **update\_recordset** is a record-set based operator that updates multiple records at once. To override the behavior of **update**, use the doUpdate method. The example selects the table **custTable** for update. Any records with the AccountNum equal to 4000 are updated (in this case only one). The **CreditMax** field is changed to 5000.

    CustTable custTable;
        ttsBegin;
          select forUpdate custTable
          where custTable.AccountNum == '4000'; 
          custTable.CreditMax = 5000; 
          custTable.update(); 
        ttsCommit;

## doUpdate method
The **doUpdate** method updates the current record with the contents of the buffer. This method also updates the appropriate system fields. The **doUpdate** method should be used when the update method on the table is to be bypassed. The syntax for a **doUpdate** table method is **void doUpdate()** In the following example, **CreditMax** is increased by 1000.

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
The **delete** table method deletes the current record from the database. To use this method, specify which rows are to be deleted by using a **where** clause. Records are then removed, one at a time, from the specified table. **delete\_from** is a record-set–based operator, which simultaneously removes multiple records. The **delete** method can be overridden, for example, to add extra validation before records are deleted. If you override the **delete** method, the original version of the **delete** method can be executed instead by calling the **doDelete** method. It is equivalent to calling **super()** in the **delete** method; **doDelete** executes the base version of the **delete** method. In the following example, all the records in the **MyTable** table that satisfy the **where** clause criterion (any record with an Account number equal to 1000) are deleted from the database. These records are deleted one at a time.

    ttsBegin;
    while select forUpdate myTable
        where myTable.AccountNum == '1000'
    {
        myTable.delete();
    }
    ttsCommit;

## doDelete method
The **doDelete** table method works similar to the **delete** table method because it deletes the current record from the database. Use the **doDelete** method if the delete table method has been overridden, and you want to use the original version of the **delete** method. The **doDelete** method executes the base version of the **delete** method instead of the overridden version, which is equivalent to executing **super() **in the **delete** method. This code example deletes all records in the myTable table that have an account number that is greater than or equal to 200.

    ttsBegin;
    while select forUpdate myTable
        where myTable.AccountNum >='200';
    {
        myTable.doDelete();
    }
    ttsCommit;

## insert method
The **insert** method updates one record at a time. To insert multiple records at a time, use array inserts, **insert\_recordset**, or **RecordSortedList.insertDatabase**. To override the behavior of the **insert** method, use the **doInsert** method. The **xRecord .insert** method generates values for **RecId** and system fields, and then inserts the contents of the buffer into the database. The method operated as follows:

-   Only the specified columns of those rows selected by the query are inserted into the named table.
-   The columns of the table being copied from and those of the table being copied to must be type compatible.
-   If the columns of both tables match in type and order, the column-list may be omitted from the **insert** clause.

### insert code example: insert a new record

The following code example inserts a new record into the **CustTable** table, with the **AccountNum** set to 5000 and the **Name** set to MyCompany (other fields in the record will be blank).

    CustTable custTable;
    ttsBegin;
    select forUpdate custTable;
    custTable.AccountNum = '5000';
    custTable.insert();
    ttsCommit;

### insert code example: transaction and duplicate key

The following example shows how you can catch a **DuplicateKeyException** in the context of an explicit transaction. The exception is thrown when a call to **xRecord .insert** fails because of a duplication of an existing unique value. In the catch block, your code can take corrective action, or it can log the error for later analysis. Then your code can continue without losing all the pending work of the transaction. You cannot catch a duplicate key exception caused by a set based operation such as **insert\_recordset**. This example depends on two tables **TableNumberA** and **TableNumberB**. Each has one mandatory Integer field, named **NumberAKey** and **NumberBKey** respectively. Each of these key fields has a unique indexed defined on it. The **TableNumberA** table must have at least one record in it.

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
The **doInsert** method generates values for the **RecId** field and other system fields, and then inserts the contents of the buffer into the database. This operation is used when the insert method on the table is to be bypassed. In the following example, a new record is inserted with the name **Warren Langer** in the name field and the value 100 in the value field.

    ttsBegin;
    myTable.name = 'Warren Langer';
    myTable.value = 100;
    myTable.doInsert();
    ttsCommit;

## Transactional integrity
If the **integrity of transactions** is not ensured, it may lead to data corruption, or, at best, poor scalability with reference to concurrent users on the system. There are two internal checking features to help ensure the integrity of transactions: the **forUpdate** check and the **tssLevel** check. A **forUpdate check** ensures that no record can be updated or deleted if the record has not first been selected for update. A record can be selected for update, either by using the **forUpdate** keyword in the **select** statement, or by using the **selectForUpdate** method on tables. A **ttsLevel check** ensures that no record can be updated or deleted except from within the same transaction scope as it was selected for update. Integrity is ensured by using the following statements:

-   **ttsBegin**: marks the beginning of a transaction. This ensures data integrity, and guarantees that all updates performed until the transaction ends (by **ttsCommit** or **ttsAbort**) are consistent (all or none).
-   **ttsCommit**: marks the successful end of a transaction. This ends and commits a transaction. Dynamics 365 for Operations guarantees that a committed transaction will be performed according to intentions.
-   **ttsAbort**: allows you to explicitly discard all changes in the current transaction. As a result, the database is rolled back to the initial state where nothing will have been changed. Typically, you will use this if you have detected that the user wants to break the current job. Using **ttsAbort** ensures that the database is consistent.

It is usually better to use exception handling instead of **ttsAbort**. The **throw** statement automatically aborts the current transaction. Statements between **ttsBegin** and **ttsCommit** may include one or more transaction blocks as shown in the following example. In such cases, nothing is actually committed until the successful exit from the final **ttsCommit**.

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

### Examples of code rejected by the two transaction integrity checks

In this example, the first failure is because the **forupdate** keyword is missing. The second failure is because the update is in another transaction scope rather than the one that the record was selected in **ttsCommit** for update.

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
The following constructs allow you to insert, update, or delete multiple records. Using these constructs reduces communication between the application and the database, and it increases performance. In some situations, record-set operations can fall back to record-by-record operations.

| Construct             | Description                                                                                                                                                                                                                                   |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **RecordSortedList**  | Allows you to insert multiple records in one database trip. Use the **RecordSortedList** construct when you want a subset of data from a particular table, and when you want it sorted in an order that does not currently exist as an index. |
| **RecordInsertList**  | Allows you to insert multiple records in one database trip. Use the **RecordInsertList** construct when you do not need to sort the data.                                                                                                     |
| **insert\_recordset** | Allows you to copy multiple records from one or more tables directly into another table on a single database trip.                                                                                                                            |
| **update\_recordset** | Allows you to update multiple rows in a table on a single database trip.                                                                                                                                                                      |
| **delete\_from**      | Allows you to delete multiple records from the database on a single database trip.                                                                                                                                                            |

## insert\_recordset
**insert\_recordset** copies data from one or more tables directly into one resulting destination table on a single server trip. Using **insert\_recordset** is faster than using an array insert. However, array inserts are more flexible if you want to handle the data before you insert it. **insert\_recordset** is a record-set-based operator, which performs operations on multiple records at a time. However, it can fall back to record-by-record operations in many situations.

### insert\_recordset Syntax

The *ListOfFields* in the destination table must match the list of fields in the source tables. Data is transferred in the order that it appears in the list of fields. Fields in the destination table that are not present in the list of fields are assigned zero-values as in other areas. System fields, including **RecId**, are assigned transparently by the kernel in the destination table. **insert\_recordset**  *DestinationTable*  **(**  *ListOfFields*  **)** **select**  *ListOfFields1*  **from**  *SourceTable*  **\[ where**  *WhereClause*  **\]** **\[ join**  *ListOfFields2*  **from**  *JoinedSourceTable* **\[ where**  *JoinedWhereClause*  **\]\]**

### Code example: insert data from another table

The records, **myNum** and **mySum**, are retrieved from the table **anotherTable** and inserted into the table **myTable**. The records are grouped according to **myNum**, and only the **myNum** records with a value less than or equal to 100 are included in the insertion.

    insert_recordset myTable (myNum, mySum)
        select myNum, sum(myValue) 
            from anotherTable 
            group by myNum 
            where myNum <= 100;

### Code example: insert data from variables

This code example shows that the **insert\_recordset** statement can insert data that is provided in variables. In this example, the keyword **firstonly** is used so that only one row is inserted. Literals, such as **128** or **"this literal string"**, cannot be used as a source of data to be inserted.

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

### Code example: insert data using a join

The following code example shows a **join** of three tables on an **insert\_recordset** statement that has a sub-**select**. Also, a **while** **select** statement with a similar join is shown. A variable is used to supply the inserted value for one column. The **str** variable must be declared with a length that is less than or equal to the maximum length of the corresponding database field. In this example, there is an **insert\_recordset** statement for **tabEmplProj5**. One of the target fields is named **Description**, and the field's data comes from the local variable **sDescriptionVariable**. When the configuration key for the **Description** field is turned off, the **insert\_recordset** still succeeds. The system ignores both the **Description** field and the variable **sDescriptionVariable**. This is an example of **configuration key automation**. Configuration key automation is when the system can automatically adjust the behavior of an **insert\_recordset** statement that inserts into fields that have their configuration key turned off.

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
The **update\_recordset** statement enables you to update multiple rows in a single trip to the server. This means that certain tasks may have improved performance by using the power of the SQL server. ****update\_recordset**** resembles **delete\_from** in X++ and **update set** in SQL. It works on the database server-side on an SQL-style record-set, instead of retrieving each record separately by fetching, changing, and updating. If the **update** method is overridden, the implementation falls back to a classic looping construction, updating records one by one just as **delete\_from** does for deletions. This also means that the construction works on temporary tables, and whole-table-cached tables by using the looping construction.

### Code example: update based on a calculated value

This example updates the table **myTableBuffer** and increments the value in **field1** by ten percent in all records in the table.

    MyTable myTableBuffer;
    update_recordset myTableBuffer
    setting field1 = field1 * 1.10;

### Code example: update using a where clause

This example updates the table **myTable** in all records where **field1** has the value 0. **field1** is assigned the new value 1; **field2** is assigned the value of the sum of **fieldX** and **fieldY**. This example updates multiple fields at the same time, and it updates only those rows that satisfy the **where** clause.

    MyTable myTableBuffer;
    update_recordset myTableBuffer
    setting
        field1 = 1,
        field2 = fieldX + fieldY
    where field1 == 0;

### Code example: updating joined tables

This example shows that the **update\_recordset** statement supports the joining of several tables. Data from the joined tables can be used to assign values to fields in the table that is being updated.

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
You can delete multiple records from a database table by using a **delete\_from** statement. This can be more efficient and faster than deleting one record at a time by using the **xRecord .delete** method in a loop. If you have overridden the delete method, the system interprets the **delete\_from** statement into code that calls the **delete** method one time for each row that is deleted.

### Code example: efficiently delete records using delete\_from

The following code example is an efficient way to delete multiple records.

    static void DeleteMultiRow1aJob(Args _args)
    {
        MyWidgetTable tabWidget;
        
        delete_from tabWidget
            where tabWidget .quantity <= 100;
    }

#### Code example: inefficiently delete records using forUpdate

The following code example is inefficient. It issues a separate SQL delete call to the database server for each record. The **xRecord** **.delete** method never deletes more than one record per call.

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

### Code example: delete with an inner join

Inner joins are not supported on the **delete\_from** statement. Therefore you cannot use the unmodified **join** keyword on the **delete\_from** statement. However, there are other ways to logically accomplish an inner join. This example shows the new and old techniques for achieving inner join logic through a sequence of statements.

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

### Code example: delete with notexists join keyword

You can use the **notexists join** keyword pair in a **delete\_from** statement. The **delete\_from** statements in the following code example are efficient. The **notexists join** clause enables the **delete\_from** statement to delete a specific set of rows. In this example the **delete\_from** statement removes all the parent order header rows for which there are no child order line rows. You can also use the **exists join** clause on the **delete\_from** statement.

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
There are situations where record-set operations can be converted to slower record-by-record operations. The following table identifies these situations.

|                                                               | DELETE\_FROM | UPDATE\_RECORDSET | INSERT\_RECORDSET | ARRAY\_INSERT | Use ... to override   |
|---------------------------------------------------------------|--------------|-------------------|-------------------|---------------|-----------------------|
| Non-SQL tables                                                | Yes          | Yes               | Yes               | Yes           | Not applicable        |
| Delete actions                                                | Yes          | No                | No                | No            | **skipDeleteActions** |
| Database log enabled                                          | Yes          | Yes               | Yes               | No            | **skipDatabaseLog**   |
| Overridden method                                             | Yes          | Yes               | Yes               | Yes           | **skipDataMethods**   |
| Alerts set up for table                                       | Yes          | Yes               | Yes               | No            | **skipEvents**        |
| ValidTimeStateFieldType property not equal to None on a table | Yes          | Yes               | Yes               | Yes           | Not applicable        |

You may explicitly skip or ignore one or more things that would adversely impact performance by using the items shown in the far right column. If for some reason one of the previously mentioned SQL operations is downgraded to a record-by-record operation, all of the **skip…** settings are also ignored. For example, the **insert** method on **myTable** is executed in the following example even though it is explicitly stated that this method should be skipped if **myTable** has a container or memo field defined.

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

