---
# required metadata

title: Consolidate shipments using release to warehouse from the load planning workbench
description: This topic presents a scenario where multiple orders are released to warehouse within the same load, and they will be consolidated into shipments automatically.
author: GarmMSFT
manager: tfehr
ms.date: 04/20/2020
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
ms.search.validFrom: 2029-04-20
ms.dyn365.ops.version: 10.0.3

---

# Consolidate shipments using release to warehouse from the load planning workbench

[!include [banner](../includes/banner.md)]

This topic presents a scenario where multiple orders are released to warehouse within the same load, and they will be consolidated into shipments automatically.

## Enable demo data

Each of the scenarios in this topic reference values and records included in the standard demo data provided for Supply Chain Management. If you'd like to run the exercises using the values provided here, be sure to work on an environment with the demo data installed, and set the legal entity to **USMF** before you begin.

## Set up shipment consolidation policies and product filters

The scenario described here assumes that you have already done the exercises and created the records described in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md). Please do those exercises before continuing with this scenario.

## Create the sales orders for this scenario

Start by creating a collection of sales orders that you can work with. You must work with a warehouse that is enabled for advanced warehouse (WHS) processes, and the same warehouse must be used for each of the following sets of orders unless another warehouse is explicitly mentioned.

Go to **Accounts receivable \> Orders \> All sales orders** and create a collection of sales orders with the settings described in the following subsections.

### Create order set 1

#### Sales order 1-1

- **Customer account** - *US-001*
- **Mode of delivery** - *Airwa-Air*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

#### Sales order 1-2

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
- Add an order line with the following settings:
  - **Item number** - *D0001* (an item with its **Code 4** filter set to *Flammable*)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.
- Add a second order line with the following settings:
  - **Item number** - *D0002* (an item with its **Code 4** filter set to *Explosive*)
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
- **Site** - *6*
- **Warehouse** - *61*
- **Pool** - *ShipCons*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

#### Sales orders 4-7 and 4-8

Create two identical sales orders with the following settings:

- **Customer account** - *US-007*
- **Site** - *6*
- **Warehouse** - *61*
- **Pool** - (leave empty)
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

## Use the load planning workbench to create loads and release to warehouse

Do the following to create a load for each of the order sets you created and then release it to warehouse:

1. Go to **Warehouse management \> Loads \> Load planning workbench**.
1. Open the **Sales lines** tab.
1. Find and select all of the sales order lines from one of the order sets you created for this scenario.
1. On the action pane, open the **Supply and demand** tab and the select **Add \> To new load** to add the selected order lines to a new Load.
1. The **Load template assignment** pane opens. In the **Load template ID** field, select a load template, such as the *Stnd Load Template*.
1. Select **OK** to close the **Load template assignment** pane. 
1. In the **Loads** section, find and select the load you just created.
1. Select **Release \> Release to warehouse** to release the selected load to the warehouse.
1. Repeat this procedure for each of the four order sets you created for this scenario.

## Verify Shipments

The following procedure will let you verify shipments that have been created or updated as a result of shipment consolidation. Use it to review each of the order sets that you created for this scenario and then review the subsections that follow to check whether you have obtained the expected results.

1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Find and select the required shipment.
1. If a consolidation policy was used when the shipment was created or updated, you will be able to see it in the **Shipment consolidation policy** field.

### Release order set 1 within one load

Two shipments should have been created:

- The first shipment contains three lines and was created using the *CustomerMode* shipment consolidation policy;
- The second shipment (which doesn't use the *Airways* transportation mode of delivery) was created using the *CustomerOrderNo* shipment consolidation policy.

### Release order set 2 within one load

Three shipments should have been created:

- The first shipment contains the *Flammable* items;
- Each of the other two shipments contains one line with an *Explosive* item.

### Release order set 3 within one load

Two shipments should have been created:

- The first shipment contains order lines from the sales order with **Customer requisition** *1*.
- The second shipment contains order lines from sales order with **Customer requisition** *2*.

### Release order set 4 within one load

Three shipments should have been created:

- Lines from two orders for **Customer account** *US-003* are grouped into one shipment using the *Order pool* shipment consolidation policy.
- Lines from two orders for **Customer account** *US-004* are grouped into one shipment using the *Order pool* shipment consolidation policy.
- Lines from sales orders 4-5 and 4-6 for **Customer account** *US-007* are grouped into one shipment using the *Order pool* shipment consolidation policy.
- Lines from sales orders 7 and 8 for **Customer account** *US-007* are grouped into one shipment using the *CrossOrder* shipment consolidation policy.

## Related topics and scenarios

- [About shipment consolidation policies](../about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](../configure-shipment-consolidation-policies.md)
- [Consolidate shipments](../warehousing/consolidate-shipments.md)
