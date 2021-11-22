---
title: While select statement
description: This topic describes while select statements in the X++ language.
author: tonyafehr
ms.date: 06/16/2020
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
ms.dyn365.ops.version: AX 7.0.0
ms.search.validFrom: 2016-02-28
---

# While select statement

[!include [banner](../../includes/banner.md)]

A **while select** statement is used to handle data. It's the most widely used form of the **select** statement. The **while select** statement loops over many records that meet specific criteria, and can run a statement on each record. The syntax of a **while select** statement resembles the syntax of a **select** statement, but the statement is preceded by **while select** instead of **select**.

+ Typically, when you use the **while select** statement for data manipulation, you use it in a transaction to ensure data integrity.
+ The results of the **while select** statement are returned in a table buffer variable.
+ If you use a field list in the **select** statement, only those fields are available in the table variable.
+ If you use aggregate functions, such as **sum** or **count**, the results are returned in the fields that you perform the **sum** or **count** over. You can count, average, or sum only integer and real fields.
+ The **select** statement itself is run only one time, immediately before the first iteration of the statements in the loop.
+ Any Boolean expressions that are added to the **while select** statement (for example, **iCounter &lt; 1**) are tested only one time. This behavior differs from the behavior of the **while** statement in languages such as C++ and C\#. For example, the following loop can have more than one iteration.

    ```xpp
    int iCounter = 0;
    BankAccountTable xrecBAT;

    while select * from xrecBAT
        where iCounter < 1
    {
        iCounter++;
        info(strFmt("%1 , %2", iCounter, xrecBAT.AccountID));
    }
    ```

The following example prints the **AccountNum** and **SalesGroup** values of every customer in the CustTable table whose account number is within a specified range.

```xpp
CustTable custTable;

while select custTable
    order by custTable.AccountNum
    where  custTable.AccountNum >= '4010' && custTable.AccountNum <= '4100'
{
    info(strFmt("%1 , %2", custTable.AccountNum, custTable.SalesGroup));
}
```


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]