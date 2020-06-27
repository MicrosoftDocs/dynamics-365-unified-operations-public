---
# required metadata

title: Conversion of operations from set-based to record-by-record
description: This topic describes how to speed up SQL operations in the X++ language.
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

# Conversion of operations from set-based to record-by-record

You can use the following statements and methods to improve performance by reducing communication between the application and the database:

- [delete_from](xpp-delete.md#delete-from-statement)
- [update_recordset](xpp-update.md#update-recordset-statement)
- [insert_recordset](xpp-insert.md#insert-recordset-statement)
- [RecordSortedList.insertDatabase](../system-classes/recordsortedlist-class.md#method-insertdatabase)
- [RecordInsertList.insertDatabase](../system-classes/recordinsertlist-class.md#method-insertdatabase)

There are situations where these record set–based operations can be converted to slower record-by-record operations. The following table identifies these situations.

|    | delete\_from | update\_recordset | insert\_recordset | RecordSortedList<br>RecordInsertList | Used to override |
|----|--------------|-------------------|-------------------|--------------------------------------|------------------|
Non-SQL tables | Yes | Yes | Yes | Yes | Not applicable
Delete actions | Yes | No | No | No | **skipDeleteActions**
The database log is enabled | Yes | Yes | Yes | No | **skipDatabaseLog**
Overridden method | Yes | Yes | Yes | Yes | **skipDataMethods**
Alerts are set up for the table | Yes | Yes | Yes | No | **skipEvents**
The **ValidTimeStateFieldType** property on a table isn't equal to None | Yes | Yes | Yes | Yes | Not applicable

You can use the settings that are shown in the **Used to override** column to explicitly skip or ignore one or more factors that adversely affect performance. If for some reason, one of the previously mentioned SQL operations is downgraded to a record-by-record operation, all the **skip\*** settings are also ignored. For example, in the following code, the **insert** method on the myTable table is run, even though it's explicitly stated that this method should be skipped if a container or memo field is defined for myTable.

```xpp
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
```
