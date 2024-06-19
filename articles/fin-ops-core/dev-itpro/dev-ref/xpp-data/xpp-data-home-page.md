---
title: X++ data selection and manipulation overview
description: Access links to topics about X++ data selection and manipulation, including information about SQL statement timeouts.
author: josaw1
ms.author: josaw
ms.topic: overview
ms.date: 09/28/2022
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ data selection and manipulation overview

[!include [banner](../../includes/banner.md)]

You can use SQL statements, either interactively or in source code, to retrieve and modify data that is stored in the database. You can use the **select** statement and API methods for these tasks:

- [Select data](xpp-select.md): Select the data to view or modify.

    - **[select](xpp-select-statement.md) statement** – Fetch records.

- [Insert data](xpp-insert.md): Add one or more new records to a table.

    - **[insert](xpp-insert.md#insert-method) and [doInsert](xpp-insert.md#do-insert-method) methods** – Insert one record at a time.
    - **[insert\_recordset](xpp-insert.md#insert-recordset-statement), [RecordInsertList.insertDatabase](/dotnet/api/dynamics.ax.application#method-insertdatabase), and [RecordSortedList.insertDatabase](/dotnet/api/dynamics.ax.application#method-insertdatabase) methods** – Insert multiple records at the same time.

- [Update data](xpp-update.md): Modify the data in existing table records.

    - **[update](xpp-update.md#update-method) and [doUpdate](xpp-update.md#do-update-method) methods** – Update one record at a time.
    - **[update\_recordset](xpp-update.md#update-recordset-statement) statement** – Update multiple records at the same time.

- [Delete data](xpp-delete.md): Remove existing records from a table.

    - **[delete](xpp-delete.md#delete-method) and [doDelete](xpp-delete.md#do-delete-method) methods** – Delete one record at a time.
    - **[delete\_from](xpp-delete.md#delete-from-statement) statement** – Delete multiple records at the same time.

Here are some other statements that you will use in data access:

- [while select](xpp-while-select.md) statement
- [select](xpp-select-expression.md) expression
- [next](xpp-select.md) statement

[Transactional integrity](xpp-transaction.md) helps prevent data corruption and improve scalability.

The [Conversion of operations from set-based to record-by-record](xpp-data-perf.md) article provides information about how you can use the record set–based statements and methods more efficiently.

You can also use the [SysDa classes](../sysda.md) to retrieve and modify data. The extensible SysDa API provides almost all the data access possibilities that are available in X++.

The **executeQueryWithParameters** API can help [mitigate a SQL injection attack](../query-with-parameters.md).

For information about using joins, see [Common misconception about Exists and Notexists joins](https://community.dynamics.com/365/financeandoperations/b/peter-s-x-developer-blog/posts/common-misconception-about-exists-and-notexists-joins).

## SQL statement timeout

All of the SQL statements listed above have a timeout set per statement, depending on the session type that issues them.  

- **Interactive** session - 30 minutes.
- **Non-interactive (batch, services, OData)** - 3 hours. 

When a statement times out due to blocking or a larger than anticipated data volume or query plan issue, an exception of type **Exception::Timeout** will be thrown with the message *A time-out occurred in the database while the query was executing.* X++ allows a handle timeout exception and retry based on this exception. You can override the default timeout by calling [queryTimeout API](/dotnet/api/microsoft.dynamics.ax.xpp.common.querytimeout).

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
