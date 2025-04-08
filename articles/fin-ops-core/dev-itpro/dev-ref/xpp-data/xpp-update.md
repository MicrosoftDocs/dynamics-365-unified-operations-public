---
title: Update data
description: Learn about the update and doUpdate methods in the X++ language, including an outline and examples of the update_recordset statement.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 06/16/2020
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Update data

[!include [banner](../../includes/banner.md)]

You can use SQL statements, either interactively or in source code, to update one or more rows in a table that is stored in the database.

+ **[update method](#update-method)** – Update the current record with the contents of the buffer. Also update the appropriate system fields.
+ **[doUpdate method](#do-update-method)** – Update one row at a time.
+ **[update\_recordset statement](#update-recordset-statement)** – Update multiple records in one database trip. By using the **update\_recordset** statement, you reduce communication between the application and the database. Therefore, you help increase performance. In some situations, record set–based operations can fall back to record-by-record operations. For more information, see [Conversion of operations from set-based to record-by-record](xpp-data-perf.md).

## <a id="update-method"></a>update method

The **update** method updates the current record with the contents of the buffer. It also updates the appropriate system fields. The optional **where** clause specifies a condition that the **update** method tests as it processes each row of the table. Only those rows that test **true** against the condition are updated with the new values.

The following example selects the CustTable table for update. Only records where the value of the **AccountNum** field equals **4000** are updated. Because there is no call to **next**, and this example doesn't use a **select while** statement, only one record is updated. The value of the **CreditMax** field is changed to **5000**.

```xpp
CustTable custTable;
ttsBegin;
    select forUpdate custTable
        where custTable.AccountNum == '4000';
    custTable.CreditMax = 5000;
    custTable.update();
ttsCommit;
```

## <a id="do-update-method"></a>doUpdate method

To override the behavior of the **update** method, use the **doUpdate** method. The **doUpdate** method updates the current record with the contents of the buffer. It also updates the appropriate system fields. You should use the **doUpdate** method when the **update** method on the table must be bypassed. The syntax for a **doUpdate** table method is **void doUpdate()**.

> [!WARNING]
> A call to **doUpdate** skips all logic, including database event handlers (for example **onUpdating** and **onUpdated**), chain-of-command **onUpdate()**, and the **update()** call itself. It's generally considered bad practice to use **doUpdate**, and we don't recommend that you use it.

```xpp
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
```

## <a id="update-recordset-statement"></a>update\_recordset statement

The **update\_recordset** operator is a record set–based operator that updates multiple records in one trip to the server. Therefore, the power of Microsoft SQL Server can help improve the performance of some tasks. The **update\_recordset** statement resembles **delete\_from** in X++ and **update set** in SQL. It doesn't retrieve each record separately by fetching, changing, and updating. Instead, it works on an SQL-style record set on the database server side. If the **update** method is overridden, the implementation falls back to a classic looping construction, where one record at a time is updated. (This behavior resembles the behavior of **delete\_from** for deletions.) Therefore, the construction works on temporary tables and whole table–cached tables by using the looping construction.

The following example updates the CustTable table and increments the value in the **CreditMax** column by **1000** for records where the **CreditMax** value is more than **0** (zero).

```xpp
CustTable custTable;
ttsBegin;
update_recordset custTable
    setting CreditMax = custTable.CreditMax + 1000
    where custTable.CreditMax > 0;
ttsCommit;
```

The following example updates multiple columns.

```xpp
CustTable custTable;
ttsBegin;
update_recordset custTable
    setting
        CreditMax = custTable.CreditMax + 1000,
        AccountStatement = CustAccountStatement::Always
    where custTable.CreditMax > 0;
ttsCommit;
```

The following example shows that the **update\_recordset** statement supports joins of several tables. Data from the joined tables can be used to assign values to fields in the table that is being updated.

```xpp
TableEmployee tabEmpl;
TableDepartment tabDept;
TableProject tabProj;
update_recordset tabEmpl
    setting
        currentStatusDescription = tabDept.DeptName + ", " + tabProj .ProjName
join tabDept
    where tabDept.DeptId == tabEmpl.DeptId
join tabProj
    where tabProj.ProjId == tabEmpl .ProjId;
```


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
