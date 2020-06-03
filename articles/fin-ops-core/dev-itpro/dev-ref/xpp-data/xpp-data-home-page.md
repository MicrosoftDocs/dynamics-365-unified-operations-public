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

You can use SQL statements, either interactively or within source code, to retrieve and modify data that is stored in the database. These topics describe using the [X++ select statement](xpp-select.md). You use the following types of statements for data manipulation:

-   **select** – Select the data to view or modify.
-   **insert** – Add one or more new records to a table. The **insert** statement inserts one record at a time. The **array insert**, **insert\_recordset**, and **RecordInsertList** statements insert multiple records at the same time.
-   **update** – Modify data in existing table records. The **update** statement updates one record at a time. The **update\_recordset** statement updates multiple records at the same time.
-   **delete** – Remove existing records from a table. The **delete** statement deletes one record at a time.

