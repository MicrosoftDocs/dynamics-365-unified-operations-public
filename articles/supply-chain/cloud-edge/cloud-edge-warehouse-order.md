---
# required metadata

title: Warehouse orders used as part of for cloud and edge scale units
description: This topic provides information about the warehouse order capability used as part of the warehouse scale unit workload.
author: perlynne
manager: tfeyr
ms.date: 11/11/2020
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
ms.search.validFrom: 2020-11-20
ms.dyn365.ops.version: 10.0.16
---

# Warehouse orders for cloud and edge warehouse management scale unit workloads

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

> [!WARNING]
> Not all business functionality is fully supported in the public preview when workload scale units are used. Be sure to use only the processes that this topic explicitly describes as supported.

## Warehouse orders

Warehouse orders are only used as part of deployments using warehouse management workloads for cloud and edge scale units ([Warehouse management workloads for cloud and edge scale units](cloud-edge-workload-warehousing.md)).

Warehouse orders are used as part of the warehouse management processing, for example as part of an inbound purchase order warehouse app registration of physical inventory on-hand.
With a hub and scale unit warehouse deployment, the warehouse orders will get created as part of the **Release to warehouse** process for purchase order lines containing a scale unit warehouse and items enabled to use warehouse management processes.

The **Release to warehouse** process is done from the hub:

**Procurement and sourcing > Purchase orders > All purchase orders > Warehouse > Actions > Release to warehouse**.

You can view the related **Warehouse order lines** directly from **Purchase order lines > Warehouse > Warehouse order lines** or view all the lines from **Warehouse management > Inquiries and reports > Warehouse order lines**.

As part of the **Release to warehouse** process the purchase order inventory transactions will get linked to warehouse orders and thereby locked for getting updated by the hub. In case a release to warehouse was done by a mistake or another reason for wanting to reverse the creation of warehouse order lines, a request to cancel the selected warehouse order lines can be done from the Warehouse order lines page by using the option **Cancel warehouse order lines**. Note that the request will be denied for lines that are either already pending cancellation or actively being processed at a warehouse running its workload on a scale unit.

As part of the **Warehouse order lines** view you can monitor the inbound receiving progress in the **Quantity left to receive** column. To view the details related to the actual Warehouse app recorded data you open **Warehouse management >  Warehouse > Warehouse order** or directly filtered from the **Warehouse order lines**.

