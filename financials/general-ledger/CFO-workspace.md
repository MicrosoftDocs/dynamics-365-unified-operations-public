---
# required metadata

title: Add financial dimensions to the CFO workspace
description: This article describes how to add financial dimensions to the CFO workspace for the ledger and budget reports. 
author: aolson
manager: AnnBe
ms.date: 08/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 14091
ms.assetid: c64eed1d-df17-448e-8bb6-d94d63b14607
ms.search.region: Global
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Add financial dimensions to the CFO workspace

[!include[banner](../includes/banner.md)]
This article describes how to add financial dimensions to the CFO workspace for the ledger and budget reports. The CFO workspace has an **Overview** and **Financial** tab. The reports on these two pages are backed by the LedgerActivityMeasure and the  BudgetActivityMeasure. With the Dynamics 365 for Finance and Operations,Enterprise edition July release, there is a relation between the two measures with the DimensionCombinationEntity to enable you to select dimensions.

1.  In Dynamics 365 for Finance and Operations, Enterprise edition, refresh the **LedgerActivityMeasure** and the **BudgetActivityMeasure** on the **Entity Store** page.

2.  In Visual Studio, go to **Application Explorer** and search for ‘**LedgerCFO’**.

3.  Find the **LedgerCFOWorkspacePBIX** under **Resources** and open it.

4.  When it opens in PowerBI desktop, click **Get Data**, choose **SQL Server database**, click **Connect**.

5.  Enter the Server name and type **AxDW** as the Database. Select **DirectQuery** > **OK**.

6.  Search for and select **LedgerActivityMeasure\_DimensionCombination**, click **Load**.

**Tip**: Rename the table in the Fields list to Financial dimensions so it’s easy to identify.

7.  Click **Manage Relationships** and then click **New**.

8.  Select **General Ledger Activities** from the first drop down, click **LedgerDimension**.

9.  In the second drop-down, select **LedgerActivityMeasure\_DimensionCombination**, or Financial Dimensions if you renamed it. Click the header **DimensionCombinationRECID**.

10. In the **Cardinality** field, select **Many to One**.

11.  Change the **Cross filter direction** to be **Single**.

12.  Select both **Make this relationship active** and **Assume referential integrity**, click **OK** and then click **Close**.

[! Create relationship](./media/Create-relationship.png)](./media/Create-relationship.png)

13.  In the **Fields** list, you see the table and available financial dimensions. Drag the financial dimensions you want to the Report level filters.

14.  **Save** your changes.

15.  Back in the AOT, right click your project and select to **Synchronize**.

16.  **Build** your project and then open the application to view the results.

[!Workspace.png](./media/workspace.png)
