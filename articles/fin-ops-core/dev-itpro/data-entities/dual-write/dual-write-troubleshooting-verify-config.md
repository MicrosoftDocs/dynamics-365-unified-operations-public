---
# required metadata

title: Verify that dual-write is configured in Finance and Operations apps and Common Data Service
description: This topic explains how you can determine whether dual-write is configured in Finance and Operations apps and in Common Data Service.
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
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-03-16

---

# Verify that dual-write is configured in Finance and Operations apps and Common Data Service

[!include [banner](../../includes/banner.md)]



This topic provides troubleshooting information for dual-write integration between Finance and Operations apps and Common Data Service. Specifically, it explains how you can determine whether dual-write is configured in Finance and Operations apps and in Common Data Service.

## Verify that dual-write is configured in a Finance and Operations app

To determine whether the errors that you see when you try to save records for update come from dual-write, first verify that dual-write is configured.

+ If you have admin privileges in the Finance and Operations app, go to **Workspaces \> Data management**, and select the **Dual-write** tile. If the details of the linked environments and the list of entity maps that are running are shown, dual-write is configured.

    ![Verifying the Finance and Operations app connection when you have admin privileges](media/verify_fin_ops_1.png)

+ If you don't have admin privileges, you will receive an error message, *Unable to write data to entity \<entity name\>*. In the example in the following illustration, you can't create a customer record in the Finance and Operations app, because dual-write is configured, but the customer group and payment terms reference data don't exist in Common Data Service.

    ![Verifying the Finance and Operations app connection when you don't have admin privileges](media/verify_fin_ops_2.png)

For information about how to fix issues when you create data in Finance and Operations apps, see [Troubleshoot live synchronization issues](dual-write-troubleshooting-live-sync.md).

## Verify that dual-write is configured in Common Data Service

When you create data, if you see the **Company** field on pages in Common Data Service, dual-write is configured.

![Verifying the Common Data Service connection](media/verify_cds.png)

For information about how to fix issues when you create data in Common Data Service, see [Troubleshoot live synchronization issues](dual-write-troubleshooting-live-sync.md).

For information about how to view error details if you encounter any errors while you create data in Common Data Service, see [Enable and view the plug-in trace log in Common Data Service to view error details](dual-write-troubleshooting.md#enable-and-view-the-plug-in-trace-log-in-common-data-service-to-view-error-details).
