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

# Consolidate shipments when released to warehouse by Automatic release of sales orders

[!include [banner](../includes/banner.md)]

*Released in version 10.0.3*

This demo will simulate a scenario where multiple orders are released to warehouse within the same automated release to warehouse periodic procedure, and they will be consolidated into shipments automatically based on rules defined as shipment consolidation policies (see [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md) for instructions).

During the demo, you will create sets of sales orders, release to warehouse each of these sets and review shipments that will be created or updated during shipment consolidation according to configured policies.  

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
- In the **Quantity** field, enter **1.00**.

Create the second sales order.

**Sales order 2**:

- In the **Customer account** field, select **US-001**;
- In the **Mode of delivery** field, select **Airwa-Air**.

Add an order line to the sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4)
- In the **Quantity** field, enter **1.00**.

Create the third sales order.

**Sales order 3**:

- In the **Customer account** field, select **US-001**;
- In the **Mode of delivery** field, select **10**;
- In the **Customer requisition** field, enter **1**.

Add two order lines to the sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**.

**Line 2**:

- In the **Item number** field, select **A0002** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- In the **Mode of delivery** field, select **Airwa-Air**.

### Order set 2

Create two identical sales orders.

**Sales order 1 and 2**:

- In the **Customer account** field, select **US-002**.

Add two order lines to each sales order.

**Line 1**:

- In the **Item number** field, select **D0001** (an item with **Flammable** filter code 4);
- In the **Quantity** field, enter **1.00**.

**Line 2**:

- In the **Item number** field, select **D0002** (an item with **Explosive** filter code 4);
- In the **Quantity** field, enter **1.00**.

### Order set 3

Create a new sales order.

**Sales order 1**:

- In the **Customer account** field, select **US-002**.

Add two order lines to each sales order.

**Line 1**:

- In the **Item number** field, select **D0001** (an item with **Flammable** filter code 4);
- In the **Quantity** field, enter **1.00**.

**Line 2**:

- In the **Item number** field, select **D0002** (an item with **Explosive** filter code 4);
- In the **Quantity** field, enter **1.00**.

### Order set 4

Create a new sales order.

**Sales order 1**:

- In the **Customer account** field, select **US-001**;
- In the **Customer requisition** field, enter **1**.

Add an order line to the sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**.

### Order set 5

Create two identical sales orders.

**Sales order 1 and 2**:

- In the **Customer account** field, select **US-001**
- In the **Customer requisition** field, enter **2**.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**.

Create the third sales order.

**Sales order 3**:

- In the **Customer account** field, select **US-001**;
- In the **Customer requisition** field, enter **1**.

Add an order line to the sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**.

### Order set 6

Create two identical sales orders.

**Sales order 1 and 2**:

- In the **Customer account** field, select **US-003**.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**.

Create another two identical sales orders.

**Sales order 3 and 4**:

- In the **Customer account** field, select **US-004**.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**.

Create another two identical sales orders.

**Sales order 5 and 6**:

- In the **Customer account** field, select **US-007**.
- In the **Pool** field, select **ShipCons**.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**.

Create another two identical sales orders.

**Sales order 7 and 8**:

- In the **Customer account** field, select **US-007**;
- Leave **Pool** field empty.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**.

## Automatic release to warehouse of sales orders

In order to simplify the process of releasing specific set of sales orders to warehouse, follow these steps.

First, update the wave template that will be used during releasing.

1. Go to **Warehouse management > Setup > Waves > Wave template**.
1. In the **Wave template type** field, select **Shipping**.
1. Find and select wave template that is associated with a warehouse that was used in the order sets. For example, if **24** warehouse was used, select **24 Shipping Default** wave template.
1. Click **Edit** and select **No** in the **Process wave at release to warehouse** field.

Then, perform release to warehouse.

1. Go to **Warehouse management > Release to warehouse > Automatic release of sales orders**.
1. In the **Quantity to release** field, select **All**.
1. Expand **Records to include** FastTab and click **Filter** to set up query for sales orders to be used.
1. Click **Add** and select **Sales order** in the **Field** field.
1. In the **Criteria** field, enter sales order numbers from desired order set.
1. Click **OK**.
1. Click **OK** to launch automatic release to warehouse procedure.

To review created or updated shipment, follow these steps.

1. Go to **Warehouse management > Shipments > All shipments**.
1. Find and select required shipment.
1. If consolidation policy is used during shipment creation or update it can be found in the **Shipment consolidation policy** field.

Now, using instructions above, release to warehouse each of created set of orders and verify shipments that are created or updated as a result of shipment consolidation according to expected results provided below.

### Release sales orders from Order set 1

Expected result:

- Four shipments are created:
  - The first three shipments created using **CustomerMode** shipment consolidation policy;
  - The fourth shipment (without **Airways** transportation mode of delivery) is created using **CustomerOrderNo** shipment consolidation policy.

### Release sales orders from Order set 2

Expected result:

- Three shipments are created:
  - The first shipment contains **Flammable** items;
  - Each of the other two shipments contains one line with **Explosive** item.

### Release sales orders from Order set 3

Expected result:

- One existing shipment is updated (the one that is created as a result of order set 2 release to warehouse):
  - A line with **Flammable** item is added;
- One new shipment is created:
  - The shipment contains **Explosive** item.

### Release sales orders from Order set 4

Expected result:

- One existing shipment (where **Customer requisition** = 1) is updated:
  - One line is added.

### Release sales orders from Order set 5

Expected result:

- One existing shipment (where **Customer requisition** = 1) is updated:
  - Line from sales order 3 (with **Customer requisition** = 1) is added;
- One new shipment is created:
  - Lines from sales orders 1 and 2 are grouped into one shipment.

### Release sales orders from Order set 6

Expected result:

- Three shipments are created:
  - Lines from two orders for **US-003** customer are grouped into one shipment using **Order pool** shipment consolidation policy;
  - Lines from two orders for **US-004** customer are grouped into one shipment using **Order pool** shipment consolidation policy;
  - Lines from four orders for **US-007** customer are grouped into one shipment using **CrossOrder** shipment consolidation policy.

## Related articles and demo scripts

- [About shipment consolidation policies](../warehousing/about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md)
- [Consolidate shipments](../warehousing/consolidate-shipments.md)
