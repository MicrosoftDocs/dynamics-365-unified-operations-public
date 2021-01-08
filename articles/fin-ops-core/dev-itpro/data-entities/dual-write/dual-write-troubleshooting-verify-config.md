---
# required metadata

title: Verify that dual-write is configured in Finance and Operations apps and Dataverse
description: This topic explains how you can determine whether dual-write is configured in Finance and Operations apps and in Dataverse.
author: RamaKrishnamoorthy 
manager: AnnBe
ms.date: 03/16/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-03-16

---

# Verify that dual-write is configured in Finance and Operations apps and Dataverse

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]



This topic provides troubleshooting information for dual-write integration between Finance and Operations apps and Dataverse. Specifically, it explains how you can determine whether dual-write is configured in Finance and Operations apps and in Dataverse.

## Verify that dual-write is configured in a Finance and Operations app

To determine whether the errors that you see when you try to save rows for update come from dual-write, first verify that dual-write is configured.

+ If you have admin privileges in the Finance and Operations app, go to **Workspaces \> Data management**, and select the **Dual-write** tile. If the details of the linked environments and the list of table maps that are running are shown, dual-write is configured.

    ![Verifying the Finance and Operations app connection when you have admin privileges](media/verify_fin_ops_1.png)

+ If you don't have admin privileges, you will receive an error message, *Unable to write data to entity \<entity name\>*. In the example in the following illustration, you can't create a customer row in the Finance and Operations app, because dual-write is configured, but the customer group and payment terms reference data don't exist in Dataverse.

    ![Verifying the Finance and Operations app connection when you don't have admin privileges](media/verify_fin_ops_2.png)

For information about how to fix issues when you create data in Finance and Operations apps, see [Troubleshoot live synchronization issues](dual-write-troubleshooting-live-sync.md).

## Verify that dual-write is configured in Dataverse

When you create data, if you see the **Company** column on pages in Dataverse, dual-write is configured.

![Verifying the Dataverse connection](media/verify_cds.png)

For information about how to fix issues when you create data in Dataverse, see [Troubleshoot live synchronization issues](dual-write-troubleshooting-live-sync.md).

For information about how to view error details if you encounter any errors while you create data in Dataverse, see [Enable and view the plug-in trace log in Dataverse to view error details](dual-write-troubleshooting.md#enable-view-trace).
