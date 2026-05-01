---
title: Conversion of operations from set-based to record-by-record
description: Learn how to speed up SQL operations in the X++ language, including a table that defines what to delete, update, and override for various situations.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 03/31/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Conversion of operations from set-based to record-by-record

To improve performance and reduce communication between the application and the database, use the following statements and methods:

- [delete_from](xpp-delete.md#delete-from-statement)
- [update_recordset](xpp-update.md#update-recordset-statement)
- [insert_recordset](xpp-insert.md#insert-recordset-statement)
- [RecordSortedList.insertDatabase](/dotnet/api/dynamics.ax.application#method-insertdatabase)
- [RecordInsertList.insertDatabase](/dotnet/api/dynamics.ax.application#method-insertdatabase)

In some situations, converting these record set–based operations to record-by-record operations can slow performance. The following table identifies these situations.

| Situation | `delete_from` | `update_recordset` | `insert_recordset` | `RecordSortedList`, `RecordInsertList` | Used to override |
|---|--------------|-------------------|-------------------|--------------------------------------|------------------|
| Non-SQL tables | Yes | Yes | Yes | Yes | Not applicable |
| Delete actions | Yes | No | No | No | **skipDeleteActions** |
| The database log is enabled. | Yes | Yes | Yes | No | **skipDatabaseLog** |
| Overridden method | Yes | Yes | Yes | Yes | **skipDataMethods** |
| Alerts are set up for the table. | Yes | Yes | Yes | No | **skipEvents** |
| The **ValidTimeStateFieldType** property on a table is set to a value other than **None**. | Yes | Yes | Yes | Yes | Not applicable |

Use the **skip\*** settings in the "Used to override" column to explicitly skip or ignore one or more factors that adversely affect performance. If the previously mentioned SQL operations downgrade to record-by-record operations, all the **skip\*** settings are ignored. In the following example code, the **insert** method on the `myTable` table runs, even though the code explicitly states that this method should be skipped if a container or memo field is defined for `myTable`.

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


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
