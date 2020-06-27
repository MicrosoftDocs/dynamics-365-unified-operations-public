---
# required metadata

title: Update data
description: This topic describes the update method and the doUpdate method in the X++ language.
author: RobinARH
manager: AnnBe
ms.date: 06/16/2020
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

# Update data

[!include [banner](../../includes/banner.md)]

You can use SQL statements, either interactively or within source code, to update one or more rows in a table stored in the database.

+ **[update method](#update-method)**: Updates the current record with the contents of the buffer. It also updates the appropriate system fields.
+ **[doUpdate method](#do-update-method)**: Updates one row at a time.
+ **[update\_recordset statement](#update-recordset-statement)**: Updates multiple records in one database trip. By using the **update\_recordset** statement, you reduce communication between the application and the database, and therefore help increase performance. In some situations, record set–based operations can fall back to record-by-record operations. For more information, see [Conversion of operations from set-based to record-by-record](xpp-data-perf.md).

## <a id="update-method"></a>update method

The **update** method updates the current record with the contents of the buffer. It also updates the appropriate system fields. The optional **where** clause specifies a condition that **update** tests as it processes each row of the table. Only those rows that test **true** against the condition are updated with the new values.

The following example selects the **CustTable** table for update. Only records where the value of the **AccountNum** field is equal to **4000** are updated. Because there is no call to **next** and it is not a **select while** statement, only one record is updated. The value of the **CreditMax** field is changed to **5000**.

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

To override the behavior of **update**, use the **doUpdate** method. The **doUpdate** method updates the current record with the contents of the buffer. This method also updates the appropriate system fields. You should use the **doUpdate** method when the **update** method on the table must be bypassed. The syntax for a **doUpdate** table method is **void doUpdate()**.

> [!WARNING]
> Calling **doUpdate** skips all logic, including database event handlers (for example **onUpdating** and  **onUpdated**), chain-of-command  **onUpdate()**, and the **update()** call itself. It's generally considered bad practice to use **doUpdate** and it's not recommended.



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

The **update\_recordset** operator is a record set–based operator that updates multiple records in one trip to the server. Therefore, the power of SQL Server can help improve the performance of some tasks. The ****update\_recordset**** statement resembles **delete\_from** in X++ and **update set** in SQL. It doesn't retrieve each record separately by fetching, changing, and updating. Instead, it works on an SQL-style record set on the database server side. If the **update** method is overridden, the implementation falls back to a classic looping construction, where one record at a time is updated. (This behavior resembles the behavior of **delete\_from** for deletions.) Therefore, the construction works on temporary tables and whole table–cached tables by using the looping construction.

The following example updates the **CustTable** table and increments the value of the **CreditMax** column by **1000** for records where the **CreditMax** is greater than **0**.

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
