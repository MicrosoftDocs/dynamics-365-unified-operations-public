---
# required metadata

title: Compare item price storage
description: Compare item price storage. 
author: AndersGirke
manager: AnnBe
ms.date: 12/12/2019
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: CostAdminWorkspace, CostAnalysisWorkspace  
# ROBOTS:
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: aevengir
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: AX 7.0.0

---

# Compare item price storage

[!include [banner](../includes/banner.md)]

In Microsoft Dynamics 365 Supply Chain Management, you can run an **Compare item price** report and make the output available as a form. In the form, columns and aggregate balances are dynamically adjusted, depending on the layout that is configured. Additionally, a data entity that is named **Compare item price** lets you export the results of an **Compare item price** report run to a format such as a Microsoft Excel file or a PDF file.
This method of running the **Compare item price** report is helpful in cases where the output contains many lines. For example, the output will contain many lines if you have more than 40,000 items holding a pending item price in the Costing version.


## Run a compare item price report

1.	Go to **Cost management > Inquiries and reports > Compare item price storage**.
2.	Select **New**.
3.	In the **Process Identifier – Name** field, enter a unique name for the report.
4.	Define the layout of the report, and filter it as you require.
Note: Report execution is always done in a batch job.
5.	After the batch job is completed, the output is shown on the **Compare item price storage** page.
6.	To view the output as a form that has a traditional grid layout, select **View details**. 

The **Compare item price** data entity lets you export the output of an **Compare item price** report by applying a filter for the **Process Identifier – Name** and **Execution time** to any format that Data management supports.

## Compare item price storage

This feature provides you the ability to execute the Compare item price report and make the output accessible in a form in Dynamics 365 Finance and Operations. The form dynamically adjust columns and aggregate balances depending on . The chart provides a visual overview and support filtering and drill back to details. Additionally a new data entity Inventory aging report has been provided which enables export of a specific inventory aging report execution to a format like Excel or PDF. 

Note: This new way of executing the inventory aging report is beneficial in cases where the output contains a large number of lines. 
Example Requesting Inventory aging by Item, Site and Warehouse in case you have 50.000 items and 300 Stores created as Warehouses. 

-	A new menu item **Cost management – Inquiries and reports – Inventory aging report storage** has been introduced. 
-	Click **New** to initiate a report execution. A new field **Process Identifier – Name** is visible, enter a unique name for your report. 
-	Select the report **Identification – ID** and filters as required. The report execution is enforced to run in batch. 
-	Once the batch job completes the output of report execution is inserted in the form **Inventory aging report storage**. 
-	Click **View details** to see the output as specified in the layout in a traditional grid
-	Click **View chart** to see the output as specified in an aggregated chart 

Note: The form will not include subtotals defined in the report layout.  

A new data entity **Inventory aging report** is introduced. Provides you the ability to export the Inventory aging report output of a specific report by applying a filter on **Process Identifier – Name** to any format supported by Data management.

