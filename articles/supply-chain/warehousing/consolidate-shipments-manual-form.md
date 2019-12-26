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

## Consolidate shipments manually in “Consolidate shipments” form

This scenario assumes that you went through shipment policies configuration scripts and have more than 1 consolidation policies (see [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md) for instructions).

Standard Contoso data is used with some additions done during configuration of policies.

### Sales orders

**Order set 1**:

Create 2 new sales orders:
-	Customer = US-007
-	Pool = “Consolidate”

Create 2 new sales orders:
-	Customer = US-007
-	Pool = None

For each order of the above:
-	Add a line for item A0001, quantity 1.
- Reserve the order line.

### Release to warehouse

Release all sales orders manually by clicking on Release to warehouse button on All sales orders form (separately for each order).

### All shipments (form)

1. Select one of the shipments created above where **Shipment consolidation policy** is set to _"Order pool"_.
2. Click **Consolidate shipments** button.

- Expected result:
  - Only 1 other shipment with the same policy is suggested for consolidations

3. Select one of the shipments created above where **Shipment consolidation policy** is set to _"Default"_.
4. Click **Consolidate shipments** button.

- Expected result:
  - Only 1 other shipment with the same policy is suggested for consolidations

# Related articles and demo scripts

- [About shipment consolidation policies](../warehousing/about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md)
