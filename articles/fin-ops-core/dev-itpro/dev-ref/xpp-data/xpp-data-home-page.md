---
# required metadata

title: X++ data selection and manipulation overview
description: This topic describes select statements in the X++ language.
author: robinarh
manager: AnnBe
ms.date: 11/08/2019
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

You can use SQL statements, either interactively or within source code, to retrieve and modify data that is stored in the database. You can use the **select** statement for these tasks:

- [Select data](xpp-select.md): Select the data to view or modify.

    - [select statement](xpp-select-statement.md): Fetches records.

- [Insert data](xpp-insert.md): Add one or more new records to a table. You can use these statement to insert records:

    - [insert](xpp-insert.md#insert-method) and [do_insert](xpp-insert.md#insert-method) methods: Insert one record at a time.
    - [array insert](xpp-insert.md#array-insert-method), [insert\_recordset](xpp-insert.md#insert-statement), [RecordInsertList](xpp-insert.md#record-insert-list-method), and [RecordSortedList.insertDatabase](xpp-insert.md#insert-database-method) methods: Insert multiple records at the same time.

- [Update data](xpp-update.md): Modify data in existing table records.
    - [update](xpp-update.md#update-statement) statement: Updates one record at a time.
    - [update\_recordset](xpp-update.md#update-recordset-statement) statement: Updates multiple records at the same time.

- [Delete data](xpp-delete.md): Remove existing records from a table.

    - [delete](xpp-delete.md#delete-method) and [doDelete](xpp-delete.md#do-delete-method) methods: Delete one record at a time.
    - [delete\_recordset](xpp-delete.md#delete-recordset-statement) statement: Deletes multiple records at the same time.

You can also use the [SysDa classes](../sysda.md) to retrieve and modify data. The extensible SysDa API provides almost all the data access possibilities that are available in X++.
