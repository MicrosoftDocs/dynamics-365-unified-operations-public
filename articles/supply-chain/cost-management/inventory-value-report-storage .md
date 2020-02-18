---
# required metadata

title: Inventory value report storage
description: This feature provides you the ability to execute the Inventory value report and make the output accessible in a form in Dynamics 365 Finance and Operations. 
author: AndersGirke
manager: AnnBe
ms.date: 02/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: aevengir
ms.search.validFrom: 2020-02-18
ms.dyn365.ops.version: Release 10.0.9
---

# Inventory value report storage

This feature provides you the ability to execute the Inventory value report and make the output accessible in a form in Dynamics 365 Finance and Operations. The form dynamically adjust columns and aggregate balances depending on the Inventory value report layout configured. All your current Inventory value report configurations can be used. Additionally a new data entity Inventory value report has been provided which enables export of a specific inventory value report execution to a format like Excel or PDF.

> [!NOTE]
> This new way of executing the inventory value report is beneficial in cases where the output contains a large number of lines. Example Requesting Inventory Ending balance by Item, Site and Warehouse in case you have 50.000 items and 300 Stores created as Warehouses.

- A new menu item **Cost management > Inquiries and reports > Inventory value report storage** has been introduced. 
- Click New to initiate a report execution. A new field **Process Identifier – Name** is visible, enter a unique name for your report. 
- Select the report **Identification – ID** and filters as required. The report execution is enforced to run in batch. 
- Once the batch job completes the output of report execution is inserted in the form **Inventory value report storage**. Click **View details** to see the output as specified in the layout.

> [!NOTE]
> The form will not include subtotals defined in the report layout. General ledger balances will not be part of output even in case defined in the report layout. Reconciliation to General ledger has be done using Trial balance 

A new data entity Inventory value report is introduced. Provides you the ability to export the Inventory value report output of a specific report by applying a filter on **Process Identifier – Name** to any format supported by Data management.