---
title: Delete data
description: Learn about the delete and doDelete methods in the X++ language, including X++ code examples to run various methods.
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

# Delete data

[!include [banner](../../includes/banner.md)]

You can use SQL statements, either interactively or in source code, to delete one or more rows from tables that are stored in the database.

+ **[delete method](#delete-method)** – Delete one row at a time.
+ **[doDelete method](#do-delete-method)** – Delete one row at a time.
+ **[delete\_from statement](#delete-from-statement)** – Delete multiple rows at the same time. By using the **delete\_from** statement, you reduce communication between the application and the database. Therefore, you help increase performance. In some situations, this set-based operation can fall back to a record-by-record operation. For more information, see [Conversion of operations from set-based to record-by-record](xpp-data-perf.md).

## <a id="delete-method"></a>delete method

The **delete** method deletes the current record from the database. To use this method, use a **where** clause to specify the rows to delete. One record at a time is then removed from the specified table.

The **delete** method can be overridden. For example, you might want to add extra validation before records are deleted. If you override the **delete** method, you can run the original (base) version of the **delete** method by calling the **doDelete** method. Therefore, a call to the **doDelete** method is equivalent to a call to **super()** in the **delete** method.

In the following example, all records in the NameValuePair table that satisfy the **where** clause (that is, all records where the value of the **Name** field equals **Name1**) are deleted from the database. One record is deleted at a time.

```xpp
ttsBegin;
    NameValuePair nameValuePair;

    while select forUpdate nameValuePair
        where nameValuePair.Name == 'Name1'
    {
        nameValuePair.delete();
    }
ttsCommit;
```

The following example deletes records from the LedgerJournalTrans table and updates the associated number sequence.

```xpp
int counter = 0;
str _journalNum = '';
str _voucher = '';
LedgerJournalTrans ledgerJournalTrans;
LedgerJournalTable ledgerJournalTable;

ttsBegin;
    while select forUpdate ledgerJournalTrans
        index hint NumVoucherIdx
        where ledgerJournalTrans.journalNum == _journalNum
            && ledgerJournalTrans.voucher == _voucher
    {
        ledgerJournalTrans.doDelete();
        counter++;
    }

    if (counter && ledgerJournalTable.journalType != LedgerJournalType::Periodic)
    {
        NumberSeq::release(ledgerJournalTable.voucherSeries, _voucher);
    }
ttsCommit;
```

## <a id="do-delete-method"></a>doDelete method

Like the **delete** table method, the **doDelete** table method deletes the current record from the database. Use the **doDelete** method if the **delete** table method has been overridden, and you want to run the original (base) version of that method instead of the overridden version. Therefore, a call to the **doDelete** method is equivalent to a call to **super()** in the **delete** method.

> [!WARNING]
> A call to **doDelete** skips all logic, including database event handlers (for example, **onDeleting** and **onDeleted**), chain-of-command **onDelete()**, and the **delete()** call itself. It's generally considered bad practice to use **doDelete**, and we don't recommend that you use it.

## <a id="delete-from-statement"></a>delete\_from statement

The **delete\_from** operator is a record set–based operator that removes multiple records at the same time. This approach can be more efficient and faster than an approach that uses the **delete** method in a loop to delete one record at a time. If you've overridden the **delete** method, the system interprets the **delete\_from** statement into code that calls the **delete** method one time for each row that is deleted.

The following example deletes all records in the NameValuePair table where the value in the **Name** column is **Name1**.

```xpp
NameValuePair nameValuePair;
delete_from nameValuePair where nameValuePair.Name == 'Name1';
```

In contrast to the previous example, the following example is inefficient, because it issues a separate SQL **delete** call to the database server for each record. The **delete** method never deletes more than one record per call.

```xpp
// Example of inefficient code.
MyWidgetTable tabWidget; // extends xRecord.
ttsBegin;
    while select forUpdate tabWidget
        where tabWidget .quantity <= 100
    {
        tabWidget.delete();
    }
ttsCommit;
```

### A delete operation that has an inner join

Inner joins aren't supported on the **delete\_from** statement. Therefore, you can't use the unmodified **join** keyword on the **delete\_from** statement. However, you can logically perform an inner join by using other techniques.

The following example shows the recommended way to use the **delete\_from** method and inner joins. This example is relatively efficient. It issues a separate **delete\_from** statement for each loop iteration. However, each **delete\_from** statement can delete multiple records (a subset of all the records that the job deletes).

```xpp
MyWidgetTable tabWidget; // extends xRecord.
ttsBegin;
while select from tabGalaxy
    where tabGalaxy .isTrusted == 0
{
    delete_from tabWidget
        where tabWidget .GalaxyRecId == tabGalaxy .RecId;
}
ttsCommit;
```

### A delete operation that uses the notexists join keyword

You can use the **notexists join** keyword pair in a **delete\_from** statement. The **delete\_from** statements in the following example are efficient. The **notexists join** clause enables the **delete\_from** statement to delete a specific set of rows. In this example, the **delete\_from** statement removes all parent-order header rows that there are no child-order line rows for. You can also use the **exists join** clause on the **delete\_from** statement.

```xpp
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
        info(strFmt("Before: OHeader:  OH_Info==%1 , RecId==%2"
            ,tabOHeader .OH_Info ,tabOHeader .RecId));
    }
    while select tabOLine
        order by OL_Data
    {
        info(strFmt("Before: OLine:  OL_Data==%1 , OrderHeaderRecId==%2"
            ,tabOLine .OL_Data ,tabOLine .OrderHeaderRecId));
    }
    // Delete_From NotExists Join, to remove from the
    // parent table all order headers without children.
    delete_from tabOHeader
        notexists join tabOLine
            where tabOHeader .RecId ==
                tabOLine .OrderHeaderRecId;
    info(strFmt("%1 is the number of childless OHeader records deleted."
        ,tabOHeader.rowCount()));
    // After the delete notexists.
    // Display all parent, and then all child rows.
    info("- - - - - - - - - - - - - - -");
    while select tabOHeader
        order by OH_Info
    {
        info(strFmt("After: OHeader:  OH_Info==%1 , RecId==%2"
            ,tabOHeader .OH_Info ,tabOHeader .RecId));
    }
    while select tabOLine
        order by OL_Data
    {
        info(strFmt("After: OLine:  OL_Data==%1 , OrderHeaderRecId==%2"
            ,tabOLine .OL_Data ,tabOLine .OrderHeaderRecId));
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
```


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
