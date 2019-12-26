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

## Consolidate shipments when released to warehouse by automatic release to warehouse of sales orders

This demo will simulate a scenario where multiple orders are released to warehouse within the same automated release to warehouse periodic procedure, and they will be consolidated into shipments automatically based on rules defined as shipment consolidation policies (see [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md) for instructions).

Standard Contoso data is used with some additions done during configuration of policies.

### Sales orders

The warehouse must be used the same (WHS-enabled) in the following sets of orders unless another warehouse is explicitly mentioned:

**Order set 1**:

Create a new sales order:
-	Customer = US-001
-	Mode of delivery = Air

For this sales order:

- Add a line for item A0001, quantity 1 (an item without filter code 4).

Create a second sales order:

- Customer = US-001
- Mode of delivery = Air

For this sales order:

- Add a line for item A0001, quantity 1 (an item without filter code 4).

Create a third sales order:

- Customer = US-001
- Mode of delivery = 10
- Customer requisition = 1

For this sales order:

- Add a line for item A0001, quantity 1 (an item without filter code 4).
- Add a second line for item A0002, quantity 1 (an item without filter code 4). Specify Mode of delivery = Air.

**Order set 2**:

Create 2 new sales orders:

- Customer = US-002

For each order:
-	Add a line for item D0001, quantity 1 (an item with filter code 4 Flammable).
-	Add a second line for item D0002, quantity 1 (an item with filter code 4 Explosive).

**Order set 3**:

Create 1 new sales order:
- Customer = US-002

For the order above:

-	Add a line for item D0001, quantity 1 (an item with filter code 4 Flammable).
-	Add a second line for item D0002, quantity 1 (an item with filter code 4 Explosive).

**Order set 4**:

Create 1 new sales order:
- Customer = US-001
- Customer requisition = 1

For the order above:
-	Add a line for item A0001, quantity 1 (an item without filter code 4).

**Order set 5**:

Create 1 new sales order:
-	Customer = US-001
-	Customer requisition = 1

Create 2 new sales orders:
- Customer = US-001
- Customer requisition = 2

For each order of the above:
-	Add a line for item A0001, quantity 1 (an item without filter code 4).

**Order set 6**:

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

###	Automatic release to warehouse of sales orders

In order to simplify the process, it’s possible to use **Automatic release of sales orders** periodic operation with quantity set to **“All”**, and **Wave template** set to disable automatic processing.

Query should be used adding orders by sales order ID.

1.	Release orders from Order set 1:
  - Expected result: 4 shipments, where first 3 will use Policy 1, while the last one (without “Air”) will use Policy 3.
2.	Release orders from Order set 2:
  - Expected result: 3 shipments, where the first 1 will combine “Flammable” items, and the other two will contain “Explosive” items
3.	Release orders from Order set 3:
  - Expected result: 1 “Flammable” line will be added to the existing shipment, and the other one will create a new shipment.
4.	Release orders from Order set 4
  - Expected result: all lines will be added to the existing shipment where requisition was also “1”

5.	Release orders from Order set 5
  - Expected result: 1 order will be added to the existing shipment where requisition was also “1”. 2 other orders will be grouped into 1 shipment with requisition “2”
6.	Release orders from Order set 6
  - Expected result: orders for customers US-003 and US-004 will be grouped into 2 shipments respectively but using the same Policy 4. Orders for US-007 customer will be grouped into 1 shipment with Policy 5.


# Related articles and demo scripts

- [About shipment consolidation policies](../warehousing/about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md)
- [Consolidate shipments](../warehousing/consolidate-shipments.md)
