---
# required metadata

title: Warehouse orders for cloud and edge scale units
description: This topic provides information about the warehouse order capability used as part of the warehouse scale unit workload.
author: perlynne
manager: tfeyr
ms.date: 01/14/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSWarehouseOrderLine, WHSWarehouseReceiptEntry, PurchTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.search.industry: SCM
ms.author: perlynne
ms.search.validFrom: 2021-01-14
ms.dyn365.ops.version: 10.0.17
---

# Warehouse orders for cloud and edge scale units

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

> [!WARNING]
> Not all business functionality is fully supported in the public preview when scale unit workloads are used. If you are using scale units, be sure to use only those processes that this topic explicitly describes as supported.

## What are warehouse orders?

*Warehouse orders* are used as part of warehouse management processing, such as when using the warehouse app to register physical inventory on-hand while processing an inbound purchase order. <!-- KFM: I think we should expand this intro to tell a bit more about what a warehouse order is and how it differs from a sales order, purchase order,  work ID, etc. (as relevant). -->

With a hub and scale unit warehouse deployment, warehouse orders will get created as part of the *Release to warehouse* process for purchase order lines that specify a scale unit warehouse and items enabled to use warehouse management processes.

> [!IMPORTANT]
> Warehouse orders are only available on deployments using [warehouse management workloads for cloud and edge scale units](cloud-edge-workload-warehousing.md)).

## Create a warehouse order

To create a warehouse order:

1. Sign in to Supply Chain Management running on the hub. (You must initiate the *Release to warehouse* process while singed in on the hub.)
1. Go to **Procurement and sourcing > Purchase orders > All purchase orders**.
1. On the Action Pane, open the **Warehouse** tab and, from the **Action** group, select **Release to warehouse**.
1. You can view the related warehouse order lines by selecting a line in the **Purchase order lines** section of the purchase order and then, on the toolbar, selecting **Warehouse > Warehouse order lines**. You can view all the lines by going to **Warehouse management > Inquiries and reports > Warehouse order lines**.

<!-- KFM: I couldn't confirm the above procedure because I don't see most of those pages or commands. That is probably because I don't have C+E enabled. I changed these formulations, so please take an extra look to be sure this is still accurate. -->

## Cancel a warehouse order

As part of the *Release to warehouse* process, purchase order inventory transactions are linked to warehouse orders and are thereby locked from being updated by the hub. If you released to warehouse by mistake, or if you have some other reason to reverse the creation of warehouse order lines, you can request to cancel warehouse order lines.

To cancel warehouse order lines:

1. Sign in to Supply Chain Management running on the hub. <!-- KFM: Is this true, or does it not matter where we sign in? -->
1. Go to **Warehouse management > Inquiries and reports > Warehouse order lines**.
1. Select the relevant line.
1. Select **Cancel warehouse order lines**. <!-- KFM: Where is this, on the Action Pane? -->
    > [!NOTE]
    > The cancel-line request will be denied for lines that are either already pending cancellation or actively being processed at a warehouse running its workload on a scale unit.

## Monitor a warehouse order

As part of the **Warehouse order lines** view, you can monitor the inbound receiving progress in the **Quantity left to receive** column. To view the details related to work done using warehouse app, do one of the following:

- Go to **Warehouse management >  Warehouse > Warehouse order** and then find and open the relevant work order.
- Go to **Warehouse management > Inquiries and reports > Warehouse order lines** and use the filter to find the lines you are looking for.
- Go to **Procurement and sourcing > Purchase orders > All purchase orders**. Open the relevant purchase order and then select a line in the **Purchase order lines** section. On the **Purchase order lines** toolbar, select **Warehouse > Warehouse receipt entries**.

<!-- KFM: Please confirm the above list. The original was a little confusing, and I can't see any of these items on my environment, which isn't C+E. -->
