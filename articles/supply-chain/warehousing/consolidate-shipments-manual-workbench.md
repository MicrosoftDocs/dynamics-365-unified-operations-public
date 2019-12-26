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

# Consolidate shipments using shipment consolidation policies

[!include [banner](../includes/banner.md)]

# Released in version 10.0.3

## Shipment consolidation workbench

This scenario will simulate a scenario where multiple orders are released to warehouse, and they will be consolidated into shipments in Shipment consolidation workbench, and assumes that you went through shipment policies configuration scripts (see Scenario 2 at [Configure shipment consolidation policies](../configure-shipment-consolidation-policies.md) for instructions).

Standard Contoso data is used with some additions done during configuration of policies.

### Sales orders

The warehouse must be used the same (WHS-enabled) in the following sets of orders unless another warehouse is explicitly mentioned:

**Order set 1**:

Create a new sales order:
-	Customer = US-001
-	Mode of delivery = Air

For this sales order:

- Add a line for item A0001, quantity 1 (an item without filter code 4).
- Reserve the order line.

Create a second sales order:

- Customer = US-001
- Mode of delivery = Air

For this sales order:

- Add a line for item A0001, quantity 1 (an item without filter code 4).
- Reserve the order line.

Create a third sales order:

- Customer = US-001
- Mode of delivery = 10

For this sales order:

- Add a line for item A0001, quantity 1 (an item without filter code 4).
- Add a second line for item A0002, quantity 1 (an item without filter code 4). Specify Mode of delivery = Air.
- Reserve the order lines.

**Order set 2**:

Create 3 new sales orders:

- Customer = US-002

For each order:
-	Add a line for item D0001, quantity 1 (an item with filter code 4 Flammable).
-	Add a second line for item D0002, quantity 1 (an item with filter code 4 Explosive).
- Reserve the order lines.

**Order set 3**:

Create 2 new sales orders:
- Customer = US-001
- Customer requisition = 1

Create 2 new sales orders:
- Customer = US-001
- Customer requisition = 2

For each order of the above:
-	Add a line for item A0001, quantity 1 (an item without filter code 4).
- Reserve the order line.

**Order set 4**:

Create 2 new sales orders:
-	Customer = US-003

Create 2 new sales orders:
-	Customer = US-004

Create 2 new sales orders:
-	Customer = US-007
-	Pool = “Consolidate”

Create 2 new sales orders:
-	Customer = US-007
-	Pool = None

For each order of the above:
-	Add a line for item A0001, quantity 1 (an item without filter code 4).
- Reserve the order line.

### Release to warehouse

Release all sales orders manually by clicking on Release to warehouse button on All sales orders form (separately for each order).

### Shipment consolidation workbench

Open the **Shipment consolidation workbench** form and click **Propose shipments**

1.	Orders from Order set 1:
  - Expected result: 4 shipments, where first 3 will use Policy 1, while the last one (without “Air”) will use Policy 3.
2.	Orders from Order set 2:
  - Expected result: 3 shipments, where the first 1 will combine “Flammable” items, and the other two will contain “Explosive” items
3.	Orders from Order set 3:
  - Expected result: 2 orders will be grouped into 1 shipment with requisition “1”. 2 other orders will be grouped into 1 shipment with requisition “2”

4.	Orders from Order set 4
  - Expected result: orders for customers US-003 and US-004 will be grouped into 2 shipments respectively but using the same Policy 4. Orders for US-007 customer will be grouped into 1 shipment with Policy 5.

# Related articles and demo scripts

- [About shipment consolidation policies](../about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](../configure-shipment-consolidation-policies.md)
