---
title: Select data
description: This topic describes select statements in the X++ language.
author: tonyafehr
ms.date: 08/27/2021
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
ms.dyn365.ops.version: AX 7.0.0
ms.search.validFrom: 2016-02-28
---

# Select data

[!include [banner](../../includes/banner.md)]

The **select** statement fetches or manipulates data from the database.

+ All **select** statements use a table variable to fetch records. This variable must be declared before a **select** statement can be run.
+ The **select** statement fetches only one record, or field. To fetch or traverse multiple records, you can use the **next** statement or the **[while select](xpp-while-select.md)** statement.

    + The **next** statement fetches the next record in the table. If no **select** statement precedes the **next** statement, an error occurs. If you use a **next** statement, don't use the **firstOnly** find option.
    + It's more appropriate to use a **while select** statement to traverse multiple records.

+ The results of a **select** statement are returned in a table buffer variable.
+ If you use a field list in the **select** statement, only those fields are available in the table variable.

The following example fetches all the columns in the first row of the CustTable table and prints the value in the **AccountNum** column of that row.

```xpp
CustTable custTable;
select firstonly custTable; //this is a short notation for 'select firstonly * from custTable;'  
info("AccountNum: " + custTable.AccountNum);
```

The following example prints the value in the **AccountNum** column of each row in the CustTable table.

```xpp
CustTable custTable;
while select custTable
{
    info("AccountNum: " + custTable.AccountNum);
}
```

The following example prints the value in the **AccountNum** column of the first two rows that are returned by the **select** statement.

```xpp
CustTable custTable;
select custTable;
info("AccountNum: " + custTable.AccountNum);

next custTable;
info("AccountNum: " + custTable.AccountNum);
```

For more examples, see [Select statement](xpp-select-statement.md).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
