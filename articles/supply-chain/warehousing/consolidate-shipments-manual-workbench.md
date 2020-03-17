---
# required metadata

title: Consolidate shipments using shipment consolidation policies
description: This topic provides an overview of functionality that provides use of shipment consolidation policies.
author: GarmMSFT
manager: PJacobse
ms.date: 12/31/2019
ms.topic: use-shipment-consolidation-policies
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: PJacobse
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: v-olbara
ms.search.validFrom: 2019-08-31
ms.dyn365.ops.version: 10.0.6

---

# Consolidate shipments using Shipment consolidation workbench form

[!include [banner](../includes/banner.md)]

*Released in version 10.0.6*

This demo will simulate a scenario where multiple orders are released to warehouse, and they will be consolidated later into shipments in Shipment consolidation workbench. It is assumed that you went through shipment policies configuration scripts (see Scenario 2 at [Configure shipment consolidation policies](../configure-shipment-consolidation-policies.md) for instructions).

Standard Contoso data is used with some additions done during configuration of policies.

## Sales orders creation

The same WHS-enabled warehouse must be used in the following sets of orders unless another warehouse is explicitly mentioned.

Go to **Accounts receivable > Orders > All sales orders** and create sales orders according to information below.

### Order set 1

Create the first sales order.

**Sales order 1**:

- In the **Customer account** field, select **US-001**;
- In the **Mode of delivery** field, select **Airwa-Air**.

Add an order line to the sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

Create the second sales order.

**Sales order 2**:

- In the **Customer account** field, select **US-001**;
- In the **Mode of delivery** field, select **Airwa-Air**.

Add an order line to the sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

Create the third sales order.

**Sales order 3**:

- In the **Customer account** field, select **US-001**;
- In the **Mode of delivery** field, select **10**.

Add two order lines to the sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

**Line 2**:

- In the **Item number** field, select **A0002** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- In the **Mode of delivery** field, select **Airwa-Air**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

### Order set 2

Create two identical sales orders.

**Sales order 1 and 2**:

- In the **Customer account** field, select **US-002**.

Add two order lines to each sales order.

**Line 1**:

- In the **Item number** field, select **D0001** (an item with **Flammable** filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

**Line 2**:

- In the **Item number** field, select **D0002** (an item with **Explosive** filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

### Order set 3

Create two identical sales orders.

**Sales order 1 and 2**:

- In the **Customer account** field, select **US-001**;
- In the **Customer requisition** field, enter **1**.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

Create another two identical sales orders.

**Sales order 3 and 4**:

- In the **Customer account** field, select **US-001**;
- In the **Customer requisition** field, enter **2**.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

### Order set 4

Create two identical sales orders.

**Sales order 1 and 2**:

- In the **Customer account** field, select **US-003**.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

Create another two identical sales orders.

**Sales order 3 and 4**:

- In the **Customer account** field, select **US-004**.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

Create another two identical sales orders.

**Sales order 5 and 6**:

- In the **Customer account** field, select **US-007**.
- In the **Site** field, select **6**.
- In the **Warehouse** field, select **61**.
- In the **Pool** field, select **ShipCons**.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

Create another two identical sales orders.

**Sales order 7 and 8**:

- In the **Customer account** field, select **US-007**;
- In the **Site** field, select **6**.
- In the **Warehouse** field, select **61**.
- Leave **Pool** field empty.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

## Release to warehouse

Using instructions below, release sales orders from all order sets.

To release to warehouse a sales order using **All sales orders** form, follow these steps.

1. Go to **Accounts receivable > Orders > All sales orders**.
1. Find and select desired sales order.
1. On the Action Pane, on the **Warehouse** tab, click **Release to warehouse** to release a sales order.

## Consolidate shipments via Shipment consolidation workbench form

To consolidate shipments using **Shipment consolidation workbench** form, follow these steps.

1. Go to **Warehouse management > Release to warehouse > Shipment consolidation workbench**.
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
