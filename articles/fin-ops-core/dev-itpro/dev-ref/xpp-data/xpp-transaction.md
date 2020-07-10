---
# required metadata

title: X++ transactional integrity
description: This topic describes transactional integrity in the X++ language.
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
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 150273
ms.assetid: 999a5ecf-559b-4d66-8b05-9a8e477e0518
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.version: AX 7.0.0
ms.search.validFrom: 2016-02-28

---

# Transactional integrity

[!include [banner](../../includes/banner.md)]

This topic describes transactional integrity in the X++ language.

If you don't take steps to help guarantee the integrity of transactions, data corruption can occur. At the very least, you might experience poor scalability with respect to concurrent users on the system. Two internal checking features help guarantee the integrity of transactions: the **forUpdate** check and the **tssLevel** check. A **forUpdate** check helps guarantee that a record can be updated or deleted only if it has first been selected for update. You can select a record for update by using either the **forUpdate** keyword in the **select** statement or the **selectForUpdate** method on the table. A **ttsLevel** check helps guarantee that a record can be updated or deleted only within the same transaction scope where it was selected for update. The following statements are used to help guarantee integrity:

- **ttsBegin** – This statement marks the beginning of a transaction. It helps guarantee data integrity, and also helps guarantees that all updates that are done until the transaction ends (through **ttsCommit** or **ttsAbort**) are consistent (all or none).
- **ttsCommit** – This statement marks the successful end of a transaction. It ends and commits a transaction. The Finance and Operations app helps guarantee that a transaction that has been committed will be performed according to intentions.
- **ttsAbort** – This statement lets you explicitly discard all changes in the current transaction. In this case, the database is rolled back to the original state where nothing has been changed. Typically, you use this statement if you've detected that the user wants to break the current job. The **ttsAbort** statement helps guarantee that the database is consistent.

Usually, it's a better idea to use exception handling instead of **ttsAbort**. The **throw** statement automatically aborts the current transaction. As the following example shows, statements between **ttsBegin** and **ttsCommit** can include one or more transaction blocks. In these cases, nothing is committed until the successful exit from the final **ttsCommit** statement.

```xpp
ttsBegin;
    // Some statements.
    ttsBegin;
        // More statements.
    ttsCommit;
ttsCommit;
```

The following example selects a set of records and updates the **CustGroup** field. This code will throw an exception if the **select** statement doesn't return any records.

```xpp
Custtable custTable;
ttsBegin;
    select forUpdate custTable where custTable.AccountNum == '5000';
    custTable.CustGroup = '1';
    custTable.update();
ttsCommit;
```

## Example of code rejected by the forupdate check

In this example, the first failure occurs because the **forupdate** keyword is missing. 

```xpp
ttsBegin;
    select myTable; // Rejected by the forUpdate check.
    mytable.myField = 'xyz';
    myTable.update();
ttsCommit;
```

## Example of code rejected by the tsslevel check

In this example, the failure occurs because the transaction scope of the update differs from the transaction scope where the record was selected for update in **ttsCommit**.

```xpp
ttsBegin;
    select forUpdate * from myTable;
    myTable.myField = 'xyz';
ttsCommit;

ttsBegin;
    myTable.update(); // Rejected by the ttsLevel check.
ttsCommit;
```
