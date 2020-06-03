---
# required metadata

title: Update data
description: This topic describes the update method and the doUpdate method in the X++ language.
author: RobinARH
manager: AnnBe
ms.date: 06/18/2019
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

[!include [banner](../includes/banner.md)]

This topic describes the update method and the doUpdate method in the X++ language. 

## forUpdate keyword

The `forUpdate` keyword selects records for update only. Depending on the underlying database, the records might be locked for other users.

The following example 

```xpp
ttsBegin; 
while select forUpdate ledgerJournalTrans
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
```




## update method
The **update** table method updates the current record with the contents of the buffer. It also updates the appropriate system fields. The **where** clause is optional. When it's used, the **where** clause specifies a condition that **update** tests as it processes each row of the table. Only those rows that test **true** against the condition are updated with the new values. The **update\_recordset** operator is a record set–based operator that updates multiple records at the same time. To override the behavior of **update**, use the **doUpdate** method. The following example selects the custTable table for update. Any records where the value of the **AccountNum** field is equal to **4000** are updated. (In this case, only one record is updated.) The value of the **CreditMax** field is changed to **5000**.

```xpp
CustTable custTable;
ttsBegin;
    select forUpdate custTable
    where custTable.AccountNum == '4000';
    custTable.CreditMax = 5000;
    custTable.update();
ttsCommit;
```

## doUpdate method
The **doUpdate** method updates the current record with the contents of the buffer. This method also updates the appropriate system fields. You should use the **doUpdate** method when the **update** method on the table must be bypassed. The syntax for a **doUpdate** table method is **void doUpdate()**. In the following example, the value of the **CreditMax** field is increased by 1,000.

```xpp
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
```
