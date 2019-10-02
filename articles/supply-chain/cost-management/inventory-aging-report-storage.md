---
# required metadata

title: Inventory aging report
description: 
author: AndersGirke
manager: AnnBe
ms.date: 02/10/2019
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
ms.search.validFrom: 2019-01-10
ms.dyn365.ops.version: 

---

# Inventory aging report storage

This feature provides you the ability to execute the Inventory aging report and make the output accessible in a form and chart in Dynamics 365 Finance and Operations. The form dynamically adjust columns and aggregate balances depending on the Inventory aging report layout configured. The chart provides a visual overview and support filtering and drill back to details. Additionally a new data entity Inventory aging report has been provided which enables export of a specific inventory aging report execution to a format like Excel or PDF. 

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



