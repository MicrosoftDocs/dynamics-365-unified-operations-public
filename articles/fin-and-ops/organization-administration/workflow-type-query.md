---
# required metadata

title: Create a query for a workflow type
description: This topic describes how to create a query for a workflow type.
author: RobinARH
manager: AnnBe
ms.date: 06/19/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 202694
ms.assetid: 33349e0d-d8ac-4d20-8f9b-5f85d4e01004
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1

---

# Create a query for a workflow type 

Before you create a workflow type, you must first create a query that will access the table fields for the workflow document. This topic describes how to create a query for a workflow type.

### To create a query for a workflow type


1.  Create a new query by using one of these methods:
    + In the AOT, right-click the **Queries** node, and then click **New Query**. A query group displays under the **Queries** node. Right-click the new query and then click **Rename**. Enter a name for the query.
    + In the **Project** menu, select **Add new item**. In the **Add new item** dialog, select **Query**. Give the query a name and then click **Create**.
1.  Expand the new query, right-click the **Data Sources** node, and then click **New Data Source**. A data source group displays under the **Data Sources** node.
1.  Right-click the new data source group and then click **Properties**.
1.  In the **Properties** sheet, set the **Table** property to the main table for the document type for which you are defining a workflow.
1.  In the AOT, right-click the new query and then click **Save**.

For more information about how to create queries, see [Create queries by using the AOT](https://docs.microsoft.com/en-us/dynamicsax-2012/developer/how-to-create-queries-by-using-the-aot).
