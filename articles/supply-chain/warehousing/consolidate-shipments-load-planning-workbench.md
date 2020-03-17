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
ms.dyn365.ops.version: 10.0.3

---

# Consolidate shipments using Release to warehouse from Load planning workbench form

[!include [banner](../includes/banner.md)]

*Released in version 10.0.4*

This scenario will simulate a scenario where multiple orders are released to warehouse within the same Load, and they will be consolidated into shipments automatically. It is assumed that you went through shipment policies configuration scripts (see Scenario 2 at [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md) for instructions).

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

## Release to warehouse of sales orders via Load planning workbench form

Using instructions below, create a load for each set of orders and release it to warehouse.

To release to warehouse sales orders from specific order set using **Load planning workbench** form, follow these steps.

1. Go to **Warehouse management > Loads > Load planning workbench**.
1. In the upper section, click **Sales lines**.
1. Find and select all sales order lines from required order set.
1. On the Action Pane, on the **Supply and demand** tab, click **To new load** to add selected order lines to a new Load.
1. In the **Load template ID** field, select a load template, for example, **Stnd Load Template** and click **OK**.
1. In the bottom section of the **Load planning workbench** form, find and select created load.
1. Click **Release > Release to warehouse** to release load to warehouse.

## Shipment verification

To review created or updated shipment, follow these steps.

1. Go to **Warehouse management > Shipments > All shipments**.
1. Find and select required shipment.
1. If consolidation policy is used during shipment creation or update it can be found in the **Shipment consolidation policy** field.

Using instructions above, verify shipments that are created or updated as a result of shipment consolidation according to expected results provided below.

### Release Order set 1 within one load

Expected result:

- Two shipments are created:
  - The first shipment contains three lines and is created using **CustomerMode** shipment consolidation policy;
  - The second shipment (without **Airways** transportation mode of delivery) is created using **CustomerOrderNo** shipment consolidation policy.

### Release Order set 2 within one load

Expected result:

- Three shipments are created:
  - The first shipment contains **Flammable** items;
  - Each of the other two shipments contains one line with **Explosive** item.

### Release Order set 3 within one load

Expected result:

- Two shipments are created:
  - The first shipment contains order lines from sales order with **1** customer requisition;
  - The second shipment contains order lines from sales order with **2** customer requisition;

### Release Order set 4 within one load

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
