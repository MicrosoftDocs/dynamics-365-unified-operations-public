---
# required metadata

title: Consolidate shipments using the shipment consolidation workbench
description: This topic provides a scenario where multiple orders are released to warehouse, and then consolidated into shipments later using the shipment consolidation workbench.
author: GarmMSFT
manager: tfehr
ms.date: 05/01/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: v-olbara
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: 10.0.6

---

# Consolidate shipments using the shipment consolidation workbench

[!include [banner](../includes/banner.md)]

This topic provides a scenario where multiple orders are released to warehouse, and then consolidated into shipments later using the shipment consolidation workbench.

## Enable demo data

Each of the scenarios in this topic reference values and records included in the standard demo data provided for Supply Chain Management. If you'd like to run the exercises using the values provided here, be sure to work on an environment with the demo data installed, and set the legal entity to **USMF** before you begin.

## Set up shipment consolidation policies and product filters

The scenario described here assumes that you have already enabled the feature, done the exercises, and created the policies and other records described in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md). Please do those exercises before continuing with this scenario.

## Enable the manual shipment consolidation feature

Before you can use the manual shipment consolidation feature, it must be enabled on on your system. Administrators can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the feature status and enable it if needed. Here, the feature is listed as:

- **Module** - *Warehouse management*
- **Feature name** - *Manual shipment consolidation*

As mentioned in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md), you must also enable the *Consolidate shipment* feature before you can create the policies, but you should have done that already.

## Create the sales orders for this scenario

Start by creating a collection of sales orders that you can work with. You must work with a warehouse that is enabled for advanced warehouse (WMS) processes, and the same warehouse must be used for each of the following sets of orders unless another warehouse is explicitly mentioned.

Go to **Accounts receivable \> Orders \> All sales orders** and create a collection of sales orders with the settings described in the following subsections.

### Create order set 1

#### Sales orders 1-1 and 1-2

Create two identical sales orders with the following settings:

- **Customer account** - *US-001*
- **Mode of delivery** - *Airwa-Air*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

#### Sales order 1-3

- **Customer account** - *US-001*
- **Mode of delivery** - *10*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.
- Add a second order line with the following settings:
  - **Item number** - *A0002* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - **Mode of delivery** - *Airwa-Air*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

### Create order set 2

#### Sales orders 2-1 and 2-2

Create two identical sales orders with the following settings:

- **Customer account** - *US-002*
- **Mode of delivery** - *Airwa-Air*
- Add an order line with the following settings:
  - **Item number** - *M9200* (an item with its **Code 4** filter set to *Flammable*)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.
- Add a second order line with the following settings:
  - **Item number** - *M9201* (an item with its **Code 4** filter set to *Explosive*)
  - **Quantity** - *1.00*
  - **Mode of delivery** - *Airwa-Air*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.


### Create order set 3

#### Sales orders 3-1 and 3-2

Create two identical sales orders with the following settings:

- **Customer account** - *US-001*
- **Customer requisition** - *1*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

#### Sales orders 3-3 and 3-4

Create two identical sales orders with the following settings:

- **Customer account** - *US-001*
- **Customer requisition** - *2*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

### Create order set 4

#### Sales orders 4-1 and 4-2

Create two identical sales orders with the following settings:

- **Customer account** - *US-003*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

#### Sales orders 4-3 and 4-4

Create two identical sales orders with the following settings:

- **Customer account** - *US-004*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

#### Sales orders 4-5 and 4-6

Create two identical sales orders with the following settings:

- **Customer account** - *US-007*
- **Site** - *6*.
- **Warehouse** - *61*.
- **Pool** - *ShipCons*.
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

#### Sales orders 4-7 and 4-8

Create two identical sales orders with the following settings:

- **Customer account** - *US-007*
- **Site** - *6*.
- **Warehouse** - *61*.
- **Pool** - (Leave empty)
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

## Release to warehouse

Release to warehouse each of the sales orders you created for this scenario by doing the following:

1. Go to **Accounts receivable \> Orders \> All sales orders**.
1. Find and select the target sales order.
1. On the action pane, open the **Warehouse** tab and select **Actions \> Release to warehouse** to release the selected sales order.
1. Repeat this procedure for each sales order you created for this scenario.

## Consolidate the shipments using the shipment consolidation workbench

Do the following to consolidate shipments using the shipment consolidation workbench:

1. Go to **Warehouse management \> Release to warehouse \> Shipment consolidation workbench**.
1. Select **Edit query** on the action pane.
1. The query editor pane opens. On the **Range** tab, select **Add** to add a new row to the table and make the following settings for it:
    - **Table** - *Sales orders*
    - **Field** - *Sales order*
    - **Criteria** - Enter the sales order numbers for each of the order sets you created for this scenario (as a comma-separated list).
1. Select **OK** to save your query and close the pane.
1. Select **Consolidate shipments** on the action pane.
1. Select all of the shipments and then select **Consolidate** on the action pane.

## Verify the shipments

The following procedure will let you verify shipments that have been created or updated as a result of shipment consolidation. Use it to review each of the order sets that you created for this scenario and then review the subsections that follow to check whether you have obtained the expected results.

1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Find and select the required shipment.
1. If a consolidation policy was used when the shipment was created or updated, you will be able to see it in the **Shipment consolidation policy** field.

### Order set 1 related shipments

Two shipments should have been created:

- The first shipment contains three lines and was created using the *CustomerMode* shipment consolidation policy.
- The second shipment (without the *Airways* transportation mode of delivery) was created using the *CustomerOrderNo* shipment consolidation policy.

### Order set 2 related shipments

Three shipments should have been created:

- The first shipment contains *Flammable* items.
- Each of the other two shipments contains one line with an *Explosive* item.

### Order set 3 related shipments

Two shipments should have been created:

- The first shipment contains order lines from the sales order with **Customer requisition** = *1*.
- The second shipment contains order lines from sales order with **Customer requisition** = *2*.

### Order set 4 related shipments

Four shipments should have been created:

- Lines from two orders for customer *US-003* were grouped into one shipment using the *Order pool* shipment consolidation policy.
- Lines from two orders for customer *US-004* were grouped into one shipment using the *Order pool* shipment consolidation policy.
- Lines from sales orders 4-5 and 4-6 for customer *US-007* were grouped into one shipment using the *Order pool* shipment consolidation policy.
- Lines from sales orders 4-7 and 4-8 for customer *US-007* were grouped into one shipment using the *CrossOrder* shipment consolidation policy.

## Additional resources

- [About shipment consolidation policies](../about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](../configure-shipment-consolidation-policies.md)
- [Consolidate shipments](../warehousing/consolidate-shipments.md)
