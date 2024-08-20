---
title: Consolidate shipments by releasing to warehouse from the outbound load planning workbench
description: Learn about a scenario where multiple orders are released to the warehouse in the same load and are then automatically consolidated into shipments.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 05/12/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench, WHSOutboundLoadPlanningWorkbench
---

# Consolidate shipments by releasing to warehouse from the outbound load planning workbench

[!include [banner](../includes/banner.md)]

This article presents a scenario where multiple orders are released to the warehouse in the same load and are then automatically consolidated into shipments.

## Make demo data available

The scenario in this article references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to **USMF** before you begin.

## Set up shipment consolidation policies and product filters

The scenario that is described here assumes that you've already turned on the feature, done the exercises in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md), and created the policies and other records that are described there. Be sure to do those exercises before you continue with this scenario.

## Create the sales orders for this scenario

Start by creating a collection of sales orders that you can work with. You must work with a warehouse that is enabled for advanced warehouse (WMS) processes. Unless a different warehouse is explicitly mentioned, that same warehouse must be used for each of the following sets of orders.

Go to **Accounts receivable \> Orders \> All sales orders**, and create a collection of sales orders that have the settings that are described in the following subsections.

### Create order set 1

#### Sales order 1-1

1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Mode of delivery:** *Airwa-Air*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.

#### Sales order 1-2

1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Mode of delivery:** *Airwa-Air*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.

#### Sales order 1-3

1. Create a sales order that has the following settings:

    - **Customer account:** *US-001*
    - **Mode of delivery:** *10*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.
1. Add a second order line that has the following settings:

    - **Item number:** *A0002* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*
    - **Mode of delivery:** *Airwa-Air*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the second order line.

### Create order set 2

#### Sales orders 2-1 and 2-2

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-002*

1. Add an order line that has the following settings:

    - **Item number:** *M9200* (an item where the **Code 4** filter is set to *Flammable*)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.
1. Add a second order line that has the following settings:

    - **Item number:** *M9201* (an item where the **Code 4** filter is set to *Explosive*)
    - **Quantity:** *1.00*
    - **Mode of delivery:** *Airwa-Air*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the second order line.

### Create order set 3

#### Sales orders 3-1 and 3-2

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-001*
    - **Customer requisition:** *1*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.

#### Sales orders 3-3 and 3-4

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-001*
    - **Customer requisition:** *2*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.

### Create order set 4

#### Sales orders 4-1 and 4-2

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-003*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.

#### Sales orders 4-3 and 4-4

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-004*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.

#### Sales orders 4-5 and 4-6

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-007*
    - **Site:** *6*
    - **Warehouse:** *61*
    - **Pool:** *ShipCons*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.

#### Sales orders 4-7 and 4-8

1. Create two identical sales orders that have the following settings:

    - **Customer account:** *US-007*
    - **Site:** *6*
    - **Warehouse:** *61*
    - **Pool:** Leave this field blank.

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.

## Use the Outbound load planning workbench to create loads and release them to the warehouse

Follow these steps to create a load for each order set that you created for this scenario and then release it to the warehouse.

1. Go to **Warehouse management \> Loads \> Outbound load planning workbench**.
1. On the **Sales lines** tab, find and select all the sales order lines from one of the order sets that you created for this scenario.
1. On the Action Pane, on the **Supply and demand** tab, select **Add \> To new load** to add the selected order lines to a new Load.
1. In the **Load template assignment** dialog box, in the **Load template ID** field, select a load template, such as *Stnd Load Template*.
1. Select **OK** to close the dialog box. 
1. In the **Loads** section, find and select the load that you just created.
1. Select **Release \> Release to warehouse** to release the selected load to the warehouse.
1. Repeat this procedure for the other three order sets that you created for this scenario.

## Verify the shipments

The following procedure lets you verify the shipments that have been created or updated as a result of shipment consolidation. Use it to review each order set that you created for this scenario, and then review the subsections that follow to make sure that you've obtained the expected results.

1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Find and select the required shipment.
1. If a consolidation policy was used when the shipment was created or updated, you should see it in the **Shipment consolidation policy** field.

### Release order set 1 in one load

Two shipments should have been created:

- The first shipment contains three lines and was created by using the *CustomerMode* shipment consolidation policy.
- The second shipment, which doesn't use the *Airways* transportation mode of delivery, was created by using the *CustomerOrderNo* shipment consolidation policy.

### Release order set 2 in one load

Three shipments should have been created:

- The first shipment contains the *Flammable* items.
- Each of the other two shipments contains one line that has the *Explosive* item.

### Release order set 3 in one load

Two shipments should have been created:

- The first shipment contains order lines from the sales order where the **Customer requisition** field is set to *1*.
- The second shipment contains order lines from sales order where the **Customer requisition** field is set to *2*.

### Release order set 4 in one load

Four shipments should have been created:

- Lines from two orders for customer account *US-003* were grouped into one shipment by using the *Order pool* shipment consolidation policy.
- Lines from two orders for customer account *US-004* were grouped into one shipment by using the *Order pool* shipment consolidation policy.
- Lines from sales orders 4-5 and 4-6 for customer account *US-007* were grouped into one shipment by using the *Order pool* shipment consolidation policy.
- Lines from sales orders 4-7 and 4-8 for customer account *US-007* were grouped into one shipment by using the *CrossOrder* shipment consolidation policy.

## Related information

- [Shipment consolidation policies overview](about-shipment-consolidation-policies.md)
- [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]