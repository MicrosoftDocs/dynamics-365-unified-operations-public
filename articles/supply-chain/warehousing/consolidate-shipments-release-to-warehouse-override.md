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

## Override consolidation policy in “Release to warehouse” form

This scenario assumes that you went through shipment policies configuration scripts and have more than 1 consolidation policies (see [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md) for instructions).

Standard Contoso data is used with some additions done during configuration of policies.

### Sales orders

**Order set 1**:

Create 3 new sales orders:
- Customer = US-001

For each order of the above:
-	Add a line for item A0001, quantity 1 (an item without filter code 4).

### Release to warehouse (form)

1. Select order 1 created above.
2. Click **Add** to add the line to release to warehouse. Note that the _Default_ policy was applied in the grid below.
3. Click **Select new shipment consolidation policy**. Choose any other policy from the list (for this test, we assume you use a "ConsolidateOpen" policy that enables consolidation with other open shipments of the same policy).
4. Click **Release to warehouse**.

5. Select orders 2 and 3 created above.
6. Click **Add** to add the lines to release to warehouse. Note that the _Default_ policy was applied in the grid below.

7. Select line 2 and click **Select new shipment consolidation policy**. Choose _ConsolidateOpen_ from the list.
Click **Release to warehouse** for all lines.

- Expected result:
  - Shipment 1, policy: “ConsolidateOpen”, 2 lines.
  - Shipment 2, policy: Default, 1 line.

# Related articles and demo scripts

- [About shipment consolidation policies](../warehousing/about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md)
- [Consolidate shipments](../warehousing/consolidate-shipments.md)
