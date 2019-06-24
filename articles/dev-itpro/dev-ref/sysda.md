---
# required metadata

title: Query using the SysDA API
description: This topic explains how to create extensible queries by using the SysDA API. 
author: RobinARH
manager: AnnBe
ms.date: 06/24/2019
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
ms.custom: 72211
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.0

---

# Query using the SysDA API

[!include [banner](../includes/banner.md)]

This topic explains how to create extensible queries by using the SysDA API. 
The SysDA API lets you create queries that perform like X++ query statments and are extensible like queries. X++ query statements are not extensible. If you want to add a new range, join, or field to your query, then you need to convert your statement to a query. While queries work fine, they have their own limitations:

+ Queries are slower than query statements. Even when the resulting TSQL is the same, queries need more compute to prepare the TSQL. The execution time in SQL server is of course the same (which often overshadows the overhead).
This is the reason we avoid converting select statements to queries in performance critical paths.
+ Queries have a limited set of capabilities. For example, `delete_from` is not supported. `update_recordset` and `insert_recordset` are partly supported by using some arcane static methods on **SysQuery**.

