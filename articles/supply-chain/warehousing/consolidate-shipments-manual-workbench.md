---
# required metadata

title: Consolidate shipments by using the shipment consolidation workbench
description: This article presents a scenario where multiple orders are released to the warehouse and then consolidated into shipments later by using the shipment consolidation workbench.
author: Mirzaab
ms.date: 08/09/2022
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench, WHSShipConsolidationSetShipment
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: mirzaab
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: 10.0.6

---

# Consolidate shipments by using the shipment consolidation workbench

[!include [banner](../includes/banner.md)]

This article presents a scenario where multiple orders are released to the warehouse and then consolidated into shipments later by using the shipment consolidation workbench.

## Make demo data available

The scenario in this article references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to **USMF** before you begin.

## Set up shipment consolidation policies and product filters

The scenario that is described here assumes that you've already turned on the feature, done the exercises in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md), and created the policies and other records that are described there. Be sure to do those exercises before you continue with this scenario.

## Turn the manual shipment consolidation feature on or off

To use manual shipment consolidation, it must be turned on for your system. As of Supply Chain Management version 10.0.29, it's turned on by default. As of Supply Chain Management version 10.0.32, this feature is mandatory and can't be turned off. If you're running a version older than 10.0.32, then admins can turn this functionality on or off by searching for the *Manual shipment consolidation* feature in the [**Feature management** workspace](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

You must also turn on the *Consolidate shipment* feature before you can create policies (as of Supply Chain Management version 10.0.29, the feature is mandatory and can't be turned off). For more information, see [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md).

## Create the sales orders for this scenario

Start by creating a collection of sales orders that you can work with. You must work with a warehouse that is enabled for advanced warehouse (WMS) processes. Unless a different warehouse is explicitly mentioned, that same warehouse must be used for each of the following sets of orders.

Go to **Accounts receivable \> Orders \> All sales orders**, and create a collection of sales orders that have the settings that are described in the following subsections.

### Create order set 1

#### Sales orders 1-1 and 1-2

1. Create two identical sales orders that have the following settings:

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
    - **Mode of delivery:** *Airwa-Air*

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

## Release the orders to the warehouse

Follow these steps to release each sales order that you created for this scenario to the warehouse.

1. Go to **Accounts receivable \> Orders \> All sales orders**.
1. Find and select the sales order to release.
1. On the Action Pane, on the **Warehouse** tab, select **Actions \> Release to warehouse** to release the selected sales order.
1. Repeat this procedure for every other sales order that you created for this scenario.

## Consolidate the shipments by using the shipment consolidation workbench

1. Go to **Warehouse management \> Release to warehouse \> Shipment consolidation workbench**.
1. On the Action Pane, select **Edit query**.
1. In the query editor dialog box, on the **Range** tab, select **Add** to add a row that has the following settings to the grid:

    - **Table:** *Sales orders*
    - **Field:** *Sales order*
    - **Criteria:** Enter a comma-separated list of the sales order numbers for each order set that you created for this scenario.

1. Select **OK** to save your query and close the dialog box.
1. On the Action Pane, select **Consolidate shipments**.
1. Select all the shipments, and then, on the Action Pane, select **Consolidate**.

## Verify the shipments

The following procedure lets you verify the shipments that have been created or updated as a result of shipment consolidation. Use it to review each order set that you created for this scenario, and then review the subsections that follow to make sure that you've obtained the expected results.

1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Find and select the required shipment.
1. If a consolidation policy was used when the shipment was created or updated, you should see it in the **Shipment consolidation policy** field.

### Related shipments for order set 1

Two shipments should have been created:

- The first shipment contains three lines and was created by using the *CustomerMode* shipment consolidation policy.
- The second shipment, which doesn't use the *Airways* transportation mode of delivery, was created by using the *CustomerOrderNo* shipment consolidation policy.

### Related shipments for order set 2

Three shipments should have been created:

- The first shipment contains *Flammable* items.
- Each of the other two shipments contains one line that has the *Explosive* item.

### Related shipments for order set 3

Two shipments should have been created:

- The first shipment contains order lines from the sales order where the **Customer requisition** field is set to *1*.
- The second shipment contains order lines from sales order where the **Customer requisition** field is set to *2*.

### Related shipments for order set 4

Four shipments should have been created:

- Lines from two orders for customer *US-003* were grouped into one shipment by using the *Order pool* shipment consolidation policy.
- Lines from two orders for customer *US-004* were grouped into one shipment by using the *Order pool* shipment consolidation policy.
- Lines from sales orders 4-5 and 4-6 for customer *US-007* were grouped into one shipment by using the *Order pool* shipment consolidation policy.
- Lines from sales orders 4-7 and 4-8 for customer *US-007* were grouped into one shipment by using the *CrossOrder* shipment consolidation policy.

## Additional resources

- [Shipment consolidation policies overview](about-shipment-consolidation-policies.md)
- [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]