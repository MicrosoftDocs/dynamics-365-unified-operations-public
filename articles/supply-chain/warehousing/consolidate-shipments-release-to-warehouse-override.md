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

# Override consolidation policy in Release to warehouse form

[!include [banner](../includes/banner.md)]

*Released in version 10.0.3*

[TBD] Oleksandr - Add explanation of a scenario like for Scenario 1

This scenario assumes that you went through shipment policies configuration scripts and have more than one consolidation policy (see [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md) for instructions).

[TBD] Olga - During the demo, you will...

Standard Contoso data is used with some additions done during configuration of policies.

## Sales orders creation

### Order set 1

Create three identical sales orders.

**Sales order 1, 2 and 3**:

- In the **Customer account** field, select **US-001**.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**.

## Release of sales orders via Release to warehouse form

[TBD] Olga - Add explanation details like in scenario 1

1. Go to **Warehouse management > Release to warehouse > Release to warehouse**
1. In the upper section, select sales order 1 created above.
1. Click **Add** to add the line to release to warehouse. Note that the **Default** policy is applied in the bottom section.
1. Click **Select new shipment consolidation policy** and choose a policy from the list that enables consolidation with other open shipments of the same policy, for example, **ConsolidateOpen** policy).
1. Click **Release to warehouse**.
1. Select orders 2 and 3 created above.
1. Click **Add** to add the lines to release to warehouse. Note that the **Default** policy is applied in the bottom section.
1. Select line 2 and click **Select new shipment consolidation policy**. Choose _ConsolidateOpen_ from the list.
Click **Release to warehouse** for all lines.

As a result, two shipments are created:

- The first shipment is created using **ConsolidateOpen** policy and contains two lines ;
- The second shipment is created using **Default** policy and contains one line.

To review created shipments, follow these steps.

1. Go to **Warehouse management > Shipments > All shipments**.
1. Find and select required shipment.
1. Review consolidation policy that is used during shipment creation in the **Shipment consolidation policy** field.

## Related articles and demo scripts

- [About shipment consolidation policies](../warehousing/about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md)
- [Consolidate shipments](../warehousing/consolidate-shipments.md)
