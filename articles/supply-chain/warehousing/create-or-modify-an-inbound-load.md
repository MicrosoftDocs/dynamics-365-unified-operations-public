---
title: Create or modify an inbound load
description: This article explains how to create or modify an inbound load.
author: perlynne
ms.author: perlynne
ms.reviewer: kamaybac
ms.search.form: WHSInboundShipmentOrder, WHSInboundLoadPlanningWorkbench, WHSParameters
ms.topic: how-to
ms.date: 08/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Create or modify an inbound load

This article explains how to create or modify an inbound load. You can use a purchase order or an inbound shipment order to create an inbound load automatically or manually. You can also modify an existing inbound load by, for example, adding more lines or updating the quantities.

For more information about how to use the inbound load process with transportation planning, see [Transportation management overview](../transportation/transportation-management-overview.md).

## Create inbound loads automatically for new purchase orders

To set your system to automatically create an inbound load for each new purchase order, follow these steps:

1. Go to **Warehouse management \> Setup \> Warehouse management parameters**.
1. Open the **Loads** tab.
1. Set **Automatically create at purchase order entry** to *Yes*.

Now, an inbound load is created automatically each time you [create a purchase order](../procurement/tasks/create-purchase-order.md).

## Create inbound loads automatically for new inbound shipment orders

To set your system to create inbound loads automatically for new inbound shipment orders (based on source system, order type, and/or account), follow these steps:

1. Go to **Warehouse management \> Setup \> Source systems**.
1. You should have one record here for each external system that submits inbound shipment orders to Supply Chain Management. Do one of the following steps:
    - To add a new source system, select **New** on the Action Pane.
    - To edit an existing source system, select it on the list pane and then select **Edit** on the Action Pane.
1. For your new or selected source system, expand the **Inbound shipment order policies** FastTab. The grid here might have several rows to establish policies for each of several order types and/or accounts, or you might have just one row that applies to all types and accounts. Use the FastTab toolbar to add or remove rows in the grid as needed.
1. For each row where you'd like to automatically create inbound loads, set **Load synchronization policy** to *Full synchronization*.

Now, an inbound load is created automatically each time you [import and process an inbound shipment order](warehouse-management-only-mode.md#simple-inbound-shipment-order-message-example) for the relevant source system, order type, and account.

## Create an inbound load manually from order lines

To manually create an inbound load, you must have at least one order line not already assigned to a load. Follow these steps:

1. Go to **Warehouse management \> Loads \> Inbound load planning workbench**
1. Use the filter options at the top of the page to find the order lines you want to assign to a load.
1. Select the tab for the type of order lines you're looking for (**Purchase order lines** or **Inbound shipment order lines**).
1. Mark each order line that you would like to assign to a load.
1. On the Action Pane, open the **Supply and demand** tab and then select **To new load**
1. The **Load template assignment** dialog opens. set **Load template ID** to the load template you want to use.
1. Select **OK**.

## Create inbound loads when importing advanced shipping notices (ASNs)

The system automatically creates loads when you import [advanced shipping notices (ASNs)](import-asn-data-entity.md).
