---
title: Consolidate shipments manually by using the Consolidate shipments page
description: Learn about a scenario where multiple orders are released to the warehouse and then consolidated later by using the Consolidate shipments page.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 05/12/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench
---

# Consolidate shipments manually by using the Consolidate shipments page

[!include [banner](../includes/banner.md)]

This article presents a scenario where multiple orders are released to the warehouse and then consolidated later by using the **Consolidate shipments** page.

## Make demo data available

The scenario in this article references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to **USMF** before you begin.

## Set up shipment consolidation policies and product filters

The scenario that is described here assumes that you've already turned on the feature, done the exercises in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md), and created the policies and other records that are described there. Be sure to do those exercises before you continue with this scenario.

## Create the sales orders for this scenario

Start by creating a collection of sales orders that you can work with. You must work with a warehouse that is enabled for advanced warehouse (WMS) processes. Unless a different warehouse is explicitly mentioned, that same warehouse must be used for each of the following sets of orders.

Go to **Accounts receivable \> Orders \> All sales orders**, and create a collection of sales orders that have the settings that are described in the following subsections.

### Create sales orders 1 and 2

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-007*
    - **Pool:** *ShipCons*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.

### Create sales orders 3 and 4

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-007*
    - **Pool:** Leave this field blank.

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.

## Release the orders to the warehouse

Follow these steps to release each sales order that you created for this scenario to the warehouse.

1. Go to **Accounts receivable \> Orders \> All sales orders**.
1. Find and select the sales order to release.
1. On the Action Pane, on the **Warehouse** tab, select **Actions \> Release to warehouse** to release the selected sales order.
1. Repeat this procedure for every other sales order that you created for this scenario.

## Consolidate shipments

1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Find and select a shipment that was created when sales order 1 was released to the warehouse. (Its **Shipment consolidation policy** field should be set to *Order pool*.)
1. On the Action Pane, on the **Shipments** tab, select **Shipments \> Consolidate shipments**.
1. Verify the shipments that are suggested for consolidation. Only one shipment that has the same policy should be suggested for consolidation.
1. Close the **Shipment consolidation** page.
1. Find and select a shipment that was created when sales order 3 was released to the warehouse. (Its **Shipment consolidation policy** field should be set to *Default*.)
1. On the Action Pane, on the **Shipments** tab, select **Shipments \> Consolidate shipments**.
1. Verify that no shipments are suggested for consolidation.
1. Select **Show filters**.
1. In the **Filters** pane, remove the **Order number** filter, and then select **Apply**.
1. Verify the shipments that are suggested for consolidation. Only one shipment that has the same policy should be suggested for consolidation.

## Related information

- [Shipment consolidation policies overview](about-shipment-consolidation-policies.md)
- [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]