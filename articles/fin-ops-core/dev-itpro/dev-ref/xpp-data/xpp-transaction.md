---
title: X++ transactional integrity
description: Learn about transactional integrity in the X++ language, including examples of code that ar rejected by the forUpdate and ttsBegin checks.
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

# X++ transactional integrity

[!include [banner](../../includes/banner.md)]

This article describes transactional integrity in the X++ language.

If you don't take steps to ensure the integrity of transactions, data corruption can occur. At the very least, you might experience poor scalability with respect to concurrent users on the system. Two internal checking features help ensure the integrity of transactions: the **forUpdate** check and the **ttsLevel** check.

- A **forUpdate** check helps ensure that a record can be updated or deleted only if it has first been selected for update. You can select a record for update by using either the **forUpdate** keyword in the **select** statement or the **selectForUpdate** method on the table.
- A **ttsLevel** check helps ensure that a record can be updated or deleted only in the same transaction scope where it was selected for update.

The following statements are used to help ensure integrity:

- **ttsBegin** – This statement marks the beginning of a transaction. It helps ensure data integrity and also helps ensure that all updates that are done until the transaction ends (through **ttsCommit** or **ttsAbort**) are consistent.
- **ttsCommit** – This statement marks the successful end of a transaction. It ends and commits a transaction. The finance and operations app ensures that a transaction that has been committed will be performed according to intentions.
- **ttsAbort** – This statement lets you explicitly discard all changes in the current transaction. In this case, the database is rolled back to the original state, where nothing has been changed. Typically, you use this statement if you've detected that the user wants to break the current job. The **ttsAbort** statement helps ensure that the database is consistent.

Usually, it's a better idea to use exception handling instead of **ttsAbort**. The **throw** statement automatically aborts the current transaction. As the following example shows, statements between **ttsBegin** and **ttsCommit** can include one or more transaction blocks. In these cases, nothing is committed until a successful exit from the final **ttsCommit** statement occurs.

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

## Example of code that is rejected by the forUpdate check

In this example, the first failure occurs because the **forUpdate** keyword is missing. 

```xpp
ttsBegin;
    select myTable; // Rejected by the forUpdate check.
    mytable.myField = 'xyz';
    myTable.update();
ttsCommit;
```

## Example of code that is rejected by the ttsLevel check

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


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
