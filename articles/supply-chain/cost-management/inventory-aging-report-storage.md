---
# required metadata

title: Inventory aging report
description: This topic describes the functionality providing the ability to execute the "Inventory aging report" and make the output accessible in a form and chart.
author: AndersGirke
manager: AnnBe
ms.date: 11/11/2019
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

# Inventory aging report

In Dynamics 365 Supply Chain Management, you can run an "Inventory aging" report and make the output accessible as a form and chart. The form dynamically adjust columns and aggregate balances depending on the configured layout. The chart provides a visual overview and supports filtering and the ability to drill into details. Additionally, a data entity inventory aging report enables export of the results of an inventory aging report run to a format like Excel or PDF. 

This method of executing the inventory aging report is helpful in cases where the output contains a large number of lines. For example, a large number of lines would be created if you requested inventory aging by item, site, and warehouse in a scenario where you have 50,000 items and 300 stores created as warehouses. 

## Run an inventory aging report

1. Go to **Cost management > Inquiries and reports > Inventory aging report storage**. 
1. Click **New** to initiate a report execution. In the **Process Identifier – Name** field, enter a unique name for your report. 
1.	Select the **Identification – ID** report and filter as needed. The report execution is enforced to run in batch. 
1. Once the batch job completes, the output is inserted on the **Inventory aging report storage** page. 
1. Click **View details** to see the output in a traditional grid layout.
1.Click **View chart** to see the output in an aggregated chart 

> [!NOTE]
> The form will not include subtotals defined in the report layout.  

The data entity **Inventory aging report** provides you the ability to export the inventory aging report output by applying a filter on **Process Identifier – Name** to any format supported by Data management.



