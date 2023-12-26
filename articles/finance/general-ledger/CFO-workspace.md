---
# required metadata

title: Add financial dimensions to the CFO workspace
description: This article explains how to add financial dimensions to the CFO workspace, so that they can be used for the ledger and budget reports. 
author: aprilolson
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: July 2017 update

---

# Add financial dimensions to the CFO workspace

[!include [banner](../includes/banner.md)]

This article explains how to add financial dimensions to the Chief Financial Officer (CFO) workspace, so that they can be used for the ledger and budget reports. The CFO workspace has an **Overview** tab and a **Financial** tab. The reports on these two tabs are backed by two measures: LedgerActivityMeasure and BudgetActivityMeasure. There is a relation between those two measures and the DimensionCombinationEntity entity. Therefore, you can select dimensions.

1. In Finance, on the **Entity Store** page, update the **LedgerActivityMeasure** and the **BudgetActivityMeasure** measures.
2. In Microsoft Visual Studio, open Application Explorer, and search for **LedgerCFO**.
3. Under **Resources**, open **LedgerCFOWorkspacePBIX**.
4. When the resource opens in Microsoft Power BI desktop, select **Get Data**, select **SQL Server database**, and then select **Connect**.
5. Enter the server name, and enter **AxDW** as the database. Select **DirectQuery**, and then select **OK**.
6. Search for and select **LedgerActivityMeasure\_DimensionCombination**, and then select **Load**.

    > [!TIP]
    > In the **Fields** list, rename the table **Financial dimensions**, so that it's easy to identify.

7. Select **Manage Relationships**, and then select **New**.
8. In the first field, select **General Ledger Activities**, and then select **LedgerDimension**.
9. In the second field, select **LedgerActivityMeasure\_DimensionCombination** (or **Financial dimensions** if you renamed the table). Select the  **DimensionCombinationRECID** header.
10. In the **Cardinality** field, select **Many to One**.
11. Change the **Cross filter direction** value to **Single**.
12. Select both **Make this relationship active** and **Assume referential integrity**, select **OK**, and then select **Close**.

    [![Create a relationship.](./media/Create-relationship.png)](./media/Create-relationship.png)

13. In the **Fields** list, you should see the table and the available financial dimensions. Drag the financial dimensions that you want to the report-level filters.
14. Save your changes.
15. In the Application Object Tree (AOT), right-click your project, and then select **Synchronize**.
16. Build your project, and then open the application to view the results.

    [![Completed workspace.](./media/workspace.png)](./media/workspace.png)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
