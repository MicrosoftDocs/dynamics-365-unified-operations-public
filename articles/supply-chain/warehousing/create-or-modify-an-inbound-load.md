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

This article explains how to create or modify an inbound load. You can use a purchase order or an inbound shipment order to create an inbound load either automatically or manually. You can also modify an existing inbound load by adding more lines or updating the quantities, for example.

For more information about how to use the inbound load process with transportation planning, see [Transportation management overview](../transportation/transportation-management-overview.md).

## Automatically create inbound loads for new purchase orders

To set up your system so that it automatically creates an inbound load for each new purchase order, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Warehouse management parameters**.
1. On the **Loads** tab, set the **Automatically create at purchase order entry** option to *Yes*.

An inbound load is now automatically created each time that you [create a purchase order](../procurement/tasks/create-purchase-order.md).

## Automatically create inbound loads for new inbound shipment orders

To set up your system so that it automatically creates inbound loads for new inbound shipment orders, based on the source system, order type, and/or account, follow these steps.

1. Go to **Warehouse management** \> **Setup** \> **Source systems**.
1. On the **Source systems** page, you should have one record for each external system that submits inbound shipment orders to Microsoft Dynamics 365 Supply Chain Management. Follow one of these steps:

    - To add a new source system, select **New** on the Action Pane.
    - To edit an existing source system, select it in the list pane, and then select **Edit** on the Action Pane.

1. For the new or selected source system, select the **Inbound shipment order policies** FastTab. The grid might have several rows to define policies for each of several order types and/or accounts. Alternatively, the grid might have just one row that applies to all order types and accounts. Use the toolbar on the FastTab to add or remove rows in the grid as required.
1. For each row where you want to automatically create inbound loads, set the **Load synchronization policy** field to *Full synchronization*.

An inbound load is now automatically created each time that you [import and process an inbound shipment order](wms-only-mode-overview.md) for the relevant source system, order type, and account.

## <a name="create-an-inbound-load-manually"></a>Manually create an inbound load from order lines

To manually create an inbound load, you must have at least one order line that isn't already assigned to a load.

1. Go to **Warehouse management** \> **Loads** \> **Inbound load planning workbench**.
1. Use the filter options at the top of the page to find the order lines that you want to assign to a load.
1. Select the **Purchase order lines** or **Inbound shipment order lines** tab, depending on the type of order lines that you're looking for.
1. Mark each order line that you want to assign to a load.
1. On the Action Pane, on the **Supply and demand** tab, select **To new load**.
1. In the **Load template assignment** dialog box, set the **Load template ID** field to the load template that you want to use.
1. Select **OK**.

## Create inbound loads when you import advanced shipping notices

The system automatically creates loads when you import [advanced shipping notices (ASNs)](import-asn-data-entity.md).
