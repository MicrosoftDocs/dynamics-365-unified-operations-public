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

# Consolidate shipments when released to warehouse by automatic release to warehouse of sales orders

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

- **Customer account** = US-001
- **Mode of delivery** = Air

Add an order line to the sales order.

**Line 1**:

- **Item number** = A0001 (an item without filter code 4)
- **Quantity** = 1.00

Create the second sales order.

**Sales order 2**:

- **Customer account** = US-001
- **Mode of delivery** = Air

Add an order line to the sales order.

**Line 1**:

- **Item number** = A0001 (an item without filter code 4)
- **Quantity** = 1.00

Create the third sales order.

**Sales order 3**:

- **Customer account** = US-001
- **Mode of delivery** = 10
- **Customer requisition** = 1

Add two order lines to the sales order.

**Line 1**:

- **Item number** = A0001 (an item without filter code 4)
- **Quantity** = 1.00

**Line 2**:

- **Item number** = A0002 (an item without filter code 4)
- **Quantity** = 1.00
- **Mode of delivery** = 10

### Order set 2

Create two identical sales orders.

**Sales order 1 and 2**:

- **Customer account** = US-002

Add two order lines to each sales order.

**Line 1**:

- **Item number** = D0001 (an item with **Flammable** filter code 4)
- **Quantity** = 1.00

**Line 2**:

- **Item number** = D0002 (an item with **Explosive** filter code 4)
- **Quantity** = 1.00

### Order set 3

Create a new sales order.

**Sales order 1**:

- **Customer account** = US-002

Add two order lines to each sales order.

**Line 1**:

- **Item number** = D0001 (an item with **Flammable** filter code 4)
- **Quantity** = 1.00

**Line 2**:

- **Item number** = D0002 (an item with **Explosive** filter code 4)
- **Quantity** = 1.00

### Order set 4

Create a new sales order.

**Sales order 1**:

- **Customer account** = US-001
- **Customer requisition** = 1

Add an order line to the sales order.

**Line 1**:

- **Item number** = A0001 (an item without filter code 4)
- **Quantity** = 1.00

### Order set 5

Create two identical sales orders.

**Sales order 1 and 2**:

- **Customer account** = US-001
- **Customer requisition** = 2

Add an order line to each sales order.

**Line 1**:

- **Item number** = A0001 (an item without filter code 4)
- **Quantity** = 1.00

Create the third sales order.

**Sales order 3**:

- **Customer account** = US-001
- **Customer requisition** = 1

Add an order line to the sales order.

**Line 1**:

- **Item number** = A0001 (an item without filter code 4)
- **Quantity** = 1.00

### Order set 6

Create two identical sales orders.

**Sales order 1 and 2**:

- **Customer account** = US-003

Add an order line to each sales order.

**Line 1**:

- **Item number** = A0001 (an item without filter code 4)
- **Quantity** = 1.00

Create another two identical sales orders.

**Sales order 3 and 4**:

- **Customer account** = US-004

Add an order line to each sales order.

**Line 1**:

- **Item number** = A0001 (an item without filter code 4)
- **Quantity** = 1.00

Create another two identical sales orders.

**Sales order 5 and 6**:

- **Customer account** = US-007
- **Pool** = ShipCons

Add an order line to each sales order.

**Line 1**:

- **Item number** = A0001 (an item without filter code 4)
- **Quantity** = 1.00

Create another two identical sales orders.

**Sales order 7 and 8**:

- **Customer account** = US-007
- **Pool** = None

Add an order line to each sales order.

**Line 1**:

- **Item number** = A0001 (an item without filter code 4)
- **Quantity** = 1.00

## Automatic release to warehouse of sales orders

In order to simplify the process of releasing specific set of sales orders to warehouse, follow these steps.

1. Go to **Warehouse management > Release to warehouse > Automatic release of sales order**.
1. In the **Quantity to release** field, select **All**.
1. Expand **Records to include** FastTab and click **Filter** to set up query for sales orders to be used.
1. Click **Add** and select **Sales order** in the **Field** field.
1. In the **Criteria** field, enter sales order numbers from desired order set.
1. Click **OK**.
1. Click **OK** to launch automatic release to warehouse procedure.

___
In order to simplify the process, it’s possible to use **Automatic release of sales orders** periodic operation with quantity set to **“All”**, and **Wave template** set to disable automatic processing.

Query should be used adding orders by sales order ID.
___
To review created or updated shipment, follow these steps.

1. Go to **Warehouse management > Shipments > All shipments**.
1. Find and select required shipment.

Release to warehouse each of created set of orders and verify shipments that are created or updated as a result of shipment consolidation according to expected results provided below.

### Release sales order from Order set 1

Expected result:

- Four shipments are created:
  - First three shipments use **Policy 1** (see [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md));
  - The fourth shipment (without **Air** mode of delivery) use **Policy 3**.

### Release sales order from Order set 2

Expected result:

- Three shipments are created:
  - First shipment combines **Flammable** items;
  - The other two shipments contain **Explosive** items.

### Release sales order from Order set 3

Expected result:

- One existing shipment is updated:
  - A line with **Flammable** item is added;
- One new shipment is created:
  - The shipment contains **Explosive** item.

### Release sales order from Order set 4

Expected result:

- One existing shipment (where **Customer requisition** = 1) is updated:
  - All lines are added.

### Release sales order from Order set 5

Expected result:

- One existing shipment (where **Customer requisition** = 1) is updated:
  - Sales order 3 (with **Customer requisition** = 1) is added;
- One new shipment is created:
  - Sales order 1 and 2 are grouped into one shipment.

### Release sales order from Order set 6

Expected result:

- Three shipments are created:
  - Two orders for **US-003** customer are grouped into one shipment using **Policy 4**;
  - Two orders for **US-004** customer are grouped into one shipment using **Policy 4**;
  - Four orders for **US-007** customer are grouped into one shipment using **Policy 5**.

## Related articles and demo scripts

- [About shipment consolidation policies](../warehousing/about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md)
- [Consolidate shipments](../warehousing/consolidate-shipments.md)
