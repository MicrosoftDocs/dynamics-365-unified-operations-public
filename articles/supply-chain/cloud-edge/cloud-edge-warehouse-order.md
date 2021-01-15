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

*Warehouse orders* are a type of order that was created to support hub and scale unit warehouse deployments. They enable you to receive inventory when running a warehouse workload on a scale unit. They are currently only used together with purchase orders. Warehouse orders are used as part of warehouse management processing, such as when using the warehouse app to register physical inventory on-hand while processing an inbound purchase order. Warehouse orders are created as part of the *Release to warehouse* process that is available for purchase orders that specify a scale unit warehouse and items enabled to use warehouse management processes.

> [!IMPORTANT]
> Warehouse orders are only available on deployments using [warehouse management workloads for cloud and edge scale units](cloud-edge-workload-warehousing.md)).

## Create a warehouse order

To create a warehouse order:

1. Sign in to Supply Chain Management running on the hub. (You must initiate the *Release to warehouse* process while singed in on the hub.)
1. Go to **Procurement and sourcing > Purchase orders > All purchase orders**.
1. On the Action Pane, open the **Warehouse** tab and, from the **Actions** group, select **Release to warehouse**.
1. You can view the related warehouse order lines by selecting a line in the **Purchase order lines** section of the purchase order and then, on the toolbar, selecting **Warehouse > Warehouse order lines**. You can view all the lines by going to **Warehouse management > Inquiries and reports > Warehouse order lines**.

## Cancel a warehouse order

As part of the *Release to warehouse* process, purchase order inventory transactions are linked to warehouse orders and are thereby locked from being updated by the hub. If you released to warehouse by mistake, or if you have some other reason to reverse the creation of warehouse order lines, you can request to cancel warehouse order lines.

To cancel warehouse order lines:

1. Sign in to Supply Chain Management running on the hub.
1. Go to **Warehouse management > Inquiries and reports > Warehouse order lines**.
1. Select the relevant line.
1. On the Action Pane, select **Cancel warehouse order lines**.
    > [!NOTE]
    > The cancel-line request will be denied for lines that are either already pending cancellation or actively being processed at a warehouse running its workload on a scale unit.

## Monitor a warehouse order

As part of the **Warehouse order lines** view, you can monitor the inbound receiving progress in the **Quantity left to receive** column. To view the details related to work done using warehouse app, do one of the following:

- Go to **Warehouse management > Inquiries and reports > Warehouse order lines** and use the filter to find the lines you are looking for.
- Go to **Procurement and sourcing > Purchase orders > All purchase orders**. Open the relevant purchase order and then select one or more lines in the **Purchase order lines** section. On the **Purchase order lines** toolbar, select **Warehouse > Warehouse receipt entries**.
