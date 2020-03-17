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

# Consolidate shipments when Shipment consolidation policy is overridden in Release to warehouse form

[!include [banner](../includes/banner.md)]

*Released in version 10.0.3*

This demo will simulate a scenario where one or more sales lines have to be released to warehouse manually from the **Release to warehouse** form. There is a need to override the shipment consolidation policy defined by the system before the release (for example, consolidate with open shipments for an order that is usually not consolidated with open shipments).

This scenario assumes that you went through shipment policies configuration scripts and have more than one consolidation policy (see [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md) for instructions).

During the demo, you will create a set of sales orders and override the default shipment consolidation policy before release to warehouse.  

Standard Contoso data is used with some additions done during configuration of policies.

## Sales orders creation

### Order set 1

Create three identical sales orders.

**Sales order 1, 2 and 3**:

- In the **Customer account** field, select **US-002**.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**.
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

## Release of sales orders via Release to warehouse form

To override shipment consolidation policy during relase to warehouse, following these steps.

1. Go to **Warehouse management > Release to warehouse > Release to warehouse**
1. In the upper section, select sales order 1 created above.
1. Click **Add** to add the line to release to warehouse. Note that the **Default** policy is applied in the bottom section.
1. In the bottom section, click **Select new shipment consolidation policy**
1. Choose a policy that enables consolidation with other open shipments of the same policy, for example, **CustomerOrderNo** policy.
1. Click **Release to warehouse**.
1. Select orders 2 and 3 created above.
1. Click **Add** to add the lines to release to warehouse. Note that the **Default** policy is applied in the bottom section.
1. Select the second line and click **Select new shipment consolidation policy**.
1. Choose **CustomerOrderNo** policy from the list.
1. Click **Release to warehouse** for both lines.

## Shipments verification

As a result, two shipments are created:

- The first shipment is created using **CustomerOrderNo** policy and contains two lines ;
- The second shipment is created using **Default** policy and contains one line.

To review created shipments, follow these steps.

1. Go to **Warehouse management > Shipments > All shipments**.
1. Find and select required shipment.
1. Review consolidation policy that is used during shipment creation in the **Shipment consolidation policy** field.

## Related articles and demo scripts

- [About shipment consolidation policies](../warehousing/about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md)
- [Consolidate shipments](../warehousing/consolidate-shipments.md)
