---
# required metadata

title: Consolidate shipments using the shipment consolidation workbench
description: This topic provides a scenario where multiple orders are released to warehouse, and then consolidated into shipments later using the shipment consolidation workbench.
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
ms.search.validFrom: 2019-08-31
ms.dyn365.ops.version: 10.0.6

---

# Consolidate shipments using the shipment consolidation workbench

[!include [banner](../includes/banner.md)]

This topic provides a scenario where multiple orders are released to warehouse, and then consolidated into shipments later using the shipment consolidation workbench.

## Enable demo data

Each of the scenarios in this topic reference values and records included in the standard demo data provided for Supply Chain Management. If you'd like to run the exercises using the values provided here, be sure to work on an environment with the demo data installed, and set the legal entity to **USMF** before you begin.

## Set up shipment consolidation policies and product filters

The scenario described here assumes that you have already done the exercises and created the records described in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md). Please do those exercises before continuing with this scenario.

## Create the sales orders for this scenario

Start by creating a collection of sales orders that you can work with. You must work with a warehouse that is enabled for advanced warehouse (WHS) processes, and the same warehouse must be used for each of the following sets of orders unless another warehouse is explicitly mentioned. <!-- KFM: The original didn't mention warehouses. Should I remove that again? -->

Go to **Accounts receivable \> Orders \> All sales orders** and create a collection of sales orders with the settings described in the following subsections.

## Sales orders creation

The same WHS-enabled warehouse must be used in the following sets of orders unless another warehouse is explicitly mentioned.

Go to **Accounts receivable > Orders > All sales orders** and create sales orders according to information below.

### Create order set 1

#### Sales orders 1-1 and 1-2

Create two identical sales orders with the following settings: <!-- KFM: These were described separately but were otherwise identical, so I combined them. Was it the intention that they be identical? -->

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

<!-- KFM: Continue from here -->

## Consolidate the shipments using the shipment consolidation workbench

To consolidate shipments using **Shipment consolidation workbench** form, follow these steps.

1. Go to **Warehouse management \> Release to warehouse \> Shipment consolidation workbench**.
1. Click **Edit query**.
1. Click **Add** to add a new criteria line.
1. In the **Table** field, select **Sales orders**.
1. In th **Field** field, select **Sales order**.
1. In the **Criteria** field, enter sales order numbers from all order sets.
1. Click **OK**.
1. Click **Consolidate shipments**.
1. Select all the shipments and click **Consolidate**.

## Shipment verification

To review created or updated shipment, follow these steps.

1. Go to **Warehouse management > Shipments > All shipments**.
1. Find and select required shipment.
1. If consolidation policy is used during shipment creation or update it can be found in the **Shipment consolidation policy** field.

Using instructions above, verify shipments that are created or updated as a result of shipment consolidation according to expected results provided below.

### Order set 1 related shipments

Expected result:

- Two shipments are created:
  - The first shipment contains three lines and is created using **CustomerMode** shipment consolidation policy;
  - The second shipment (without **Airways** transportation mode of delivery) is created using **CustomerOrderNo** shipment consolidation policy.

### Order set 2 related shipments

Expected result:

- Three shipments are created:
  - The first shipment contains **Flammable** items;
  - Each of the other two shipments contains one line with **Explosive** item.

### Order set 3 related shipments

Expected result:

- Two shipments are created:
  - The first shipment contains order lines from sales order with **1** customer requisition;
  - The second shipment contains order lines from sales order with **2** customer requisition;

### Order set 4 related shipments

Expected result:

- Three shipments are created:
  - Lines from two orders for **US-003** customer are grouped into one shipment using **Order pool** shipment consolidation policy;
  - Lines from two orders for **US-004** customer are grouped into one shipment using **Order pool** shipment consolidation policy;
  - Lines from sales orders 5 and 6 for **US-007** customer are grouped into one shipment using **Order pool** shipment consolidation policy;
  - Lines from sales orders 7 and 8 for **US-007** customer are grouped into one shipment using **CrossOrder** shipment consolidation policy.

## Related articles and demo scripts

- [About shipment consolidation policies](../about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](../configure-shipment-consolidation-policies.md)
- [Consolidate shipments](../warehousing/consolidate-shipments.md)
