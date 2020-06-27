---
# required metadata

title: X++ data selection and manipulation overview
description: This topic describes select statements in the X++ language.
author: robinarh
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

# X++ data selection and manipulation overview

[!include [banner](../../includes/banner.md)]

You can use SQL statements, either interactively or within source code, to retrieve and modify data that is stored in the database. You can use the **select** statement and API methods for these tasks:

- [Select data](xpp-select.md): Select the data to view or modify.

    - [select statement](xpp-select-statement.md): Fetches records.

- [Insert data](xpp-insert.md): Add one or more new records to a table.

    - [insert](xpp-insert.md#insert-method) and [doInsert](xpp-insert.md#do-insert-method) methods: Insert one record at a time.
    - [insert\_recordset](xpp-insert.md#insert-recordset-statement), [RecordInsertList.insertDatabase](../system-classes/recordinsertlist-class.md#method-insertdatabase), and [RecordSortedList.insertDatabase](../system-classes/recordsortedlist-class.md#method-insertdatabase) methods: Insert multiple records at the same time.

- [Update data](xpp-update.md): Modify data in existing table records.

    - [update](xpp-update.md#update-method) and [doUpdate](xpp-update.md#do-update-method) methods: Update one record at a time.
    - [update\_recordset](xpp-update.md#update-recordset-statement) statement: Updates multiple records at the same time.

- [Delete data](xpp-delete.md): Remove existing records from a table.

    - [delete](xpp-delete.md#delete-method) and [doDelete](xpp-delete.md#do-delete-method) methods: Delete one record at a time.
    - [delete\_from](xpp-delete.md#delete-from-statement) statement: Deletes multiple records at the same time.

Other statements that you'll use in data access are:

- [while select](xpp-while-select.md) statement.
- [select expression](xpp-select-expression.md).
- [next](xpp-select.md) statement.

[Transactional integrity](xpp-transaction.md) helps prevent data corruption and help improve scalability.

[Conversion of operations from set-based to record-by-record](xpp-data-perf.md) provides additional information on using the recordset-based statements and methods efficiently.

You can also use the [SysDa classes](../sysda.md) to retrieve and modify data. The extensible SysDa API provides almost all the data access possibilities that are available in X++.
