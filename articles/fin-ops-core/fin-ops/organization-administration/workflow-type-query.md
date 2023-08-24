---
title: Create a query for a workflow type
description: This article describes how to create a query for a workflow type.
author: josaw1
ms.date: 06/19/2019
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: twheeloc
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: Platform update 1
ms.custom: 202694
ms.assetid: 33349e0d-d8ac-4d20-8f9b-5f85d4e01004
---

# Create a query for a workflow type 

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

Before you create a workflow type, you must create a query that will access the table fields for the workflow document. This article describes how to create a query for a workflow type.

## Create a query for a workflow type

1. Follow one of these steps to create a new query:

    + In Application Explorer, right-click the **Queries** node, and then select **New Query**. A query group appears under the **Queries** node. Right-click the new query, and then select **Rename**. Enter a name for the query.
    + On the **Project** menu, select **Add new item**. In the **Add new item** dialog box, select **Query**. Enter a name for the query, and then select **Create**.

2. Expand the new query, right-click the **Data Sources** node, and then select **New Data Source**. A data source group appears under the **Data Sources** node.
3. Right-click the new data source group, and then select **Properties**.
4. On the **Properties** sheet, set the **Table** property to the main table for the document type that you're defining a workflow for.
5. In the Application Object Tree (AOT), right-click the new query, and then select **Save**.

For more information about how to create queries, see [Create queries by using the AOT](/dynamicsax-2012/developer/how-to-create-queries-by-using-the-aot).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
