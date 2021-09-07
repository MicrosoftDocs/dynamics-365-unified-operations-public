---
title: Warehouse orders for cloud and edge scale units
description: This topic provides information about the warehouse order capability that is used as part of the warehouse scale unit workload.
author: perlynne
ms.date: 04/22/2021
ms.topic: article
ms.search.form: WHSWarehouseOrderLine, WHSWarehouseReceiptEntry, PurchTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2021-04-13
ms.dyn365.ops.version: 10.0.19
---

# Warehouse orders for cloud and edge scale units

[!include [banner](../includes/banner.md)]

> [!WARNING]
> Not all business functionality is fully supported in the public preview when scale unit workloads are used. If you're using scale units, be sure to use only those processes that this topic explicitly describes as supported.

## What are warehouse orders?

*Warehouse orders* are a type of order used to support hub and scale unit warehouse deployments. They let you receive and ship inventory when you're running a warehouse workload on a scale unit.

Warehouse orders are used as part of both inbound and outbound warehouse management processing. They are created as part of the *Release to warehouse* process, which gets initialized on the hub.
For the inbound processing the warehouse mobile app is used to register physical on-hand inventory during processing of inbound orders, this is available for purchase and production orders that specify a scale unit warehouse and items that are enabled to use warehouse management processes.
The outbound warehouse orders are used as part of the shipment waving process  for transfer and sales orders.

> [!IMPORTANT]
> Warehouse orders are available only in deployments that use [warehouse management workloads for cloud and edge scale units](cloud-edge-workload-warehousing.md).

## Create an inbound warehouse order

To create an inbound warehouse order for a purchase order process, follow these steps.

1. Sign in to the instance of Microsoft Dynamics 365 Supply Chain Management that is running on the hub. (You must initiate the *Release to warehouse* process while you're signed in on the hub.)
1. Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**.
1. On the Action Pane, on the **Warehouse** tab, in the **Actions** group, select **Release to warehouse**.
1. To view the related warehouse order lines, open the relevant purchase order, select a line in the **Purchase order lines** section, and then, on the toolbar, select **Warehouse \> Warehouse order lines**. To view all the lines, go to **Warehouse management \> Inquiries and reports \> Warehouse order lines**.

You can also trigger the *Release to warehouse* process from a batch job by going to **Warehouse management > Release to warehouse > Automatic release of purchase orders**. When setting up the batch job, you can select specific purchase order lines based on a query. A typical scenario would be to set up a recurrent batch job that releases all the confirmed purchase order lines expected to arrive the next day.

## Cancel a warehouse order

As part of the *Release to warehouse* process, purchase order inventory transactions are linked to warehouse orders and locked from being updated by the hub. If you released to the warehouse by mistake, or if you have some other reason to reverse the creation of warehouse order lines, you can request to cancel warehouse order lines.

To cancel warehouse order lines, follow these steps.

1. Sign in to the Supply Chain Management instance that is running on the hub.
1. Go to **Warehouse management \> Inquiries and reports \> Warehouse order lines**.
1. Select the relevant line.
1. On the Action Pane, select **Cancel warehouse order lines**.

> [!NOTE]
> The request to cancel lines will be denied for any lines that are already pending cancellation or that are actively being processed at a warehouse that is running its workload on a scale unit.

## Monitor a warehouse order

In the **Warehouse order lines** view, you can monitor the progress of inbound receiving by reviewing the values in the **Quantity left to receive** column. To view details that are related to work that is done by using the Warehouse Management mobile app, follow one of these steps.

- Go to **Warehouse management \> Inquiries and reports \> Warehouse order lines**, and use the filter to find the lines that you're looking for.
- Go to **Procurement and sourcing \> Purchase orders \> All purchase orders**, and open the relevant purchase order. In the **Purchase order lines** section, select one or more lines, and then, on the toolbar, select **Warehouse \> Warehouse receipt entries**.

[!INCLUDE [cloud-edge-privacy-notice](../../includes/cloud-edge-privacy-notice.md)]


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
