---
# required metadata

title: Consolidate shipments when the shipment consolidation policy is overridden from the Release to warehouse page
description: This topic provides a scenario where one or more sales lines must be released to warehouse manually from the Release to warehouse page, and there is a need to override the shipment consolidation policy defined by the system before the release.
author: GarmMSFT
manager: tfehr
ms.date: 05/01/2020
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm:
# ms.custom:
ms.search.region: Global
# ms.search.industry:
ms.author: v-olbara
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: 10.0.6
---

# Consolidate shipments when the shipment consolidation policy is overridden from the Release to warehouse page

[!include [banner](../includes/banner.md)]

This topic provides a scenario where one or more sales lines must be released to warehouse manually from the **Release to warehouse** page, and there is a need to override the shipment consolidation policy defined by the system before the release (for example, to consolidate with open shipments for an order that isn't usually consolidated with open shipments).

During the scenario, you will create a set of sales orders and override the default shipment consolidation policy before release to warehouse.  

## Enable demo data

Each of the scenarios in this topic reference values and records included in the standard demo data provided for Supply Chain Management. If you'd like to run the exercises using the values provided here, be sure to work on an environment with the demo data installed, and set the legal entity to **USMF** before you begin.

## Set up shipment consolidation policies and product filters

The scenario described here assumes that you have already enabled the feature, done the exercises, and created the policies and other records described in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md). Please do those exercises before continuing with this scenario.

## Create three sales orders for this scenario

Go to **Accounts receivable \> Orders \> All sales orders** and create three identical sales orders with the following settings:

- **Customer account** - *US-002*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

## Release sales orders from the Release to warehouse page

To override shipment consolidation policy during release to warehouse, do the following:

1. Go to **Warehouse management > Release to warehouse > Release to warehouse**
1. In the upper section, select the first sales order that you created for this scenario.
1. Select **Add** to add the line to release to warehouse. Note that the **Default** policy is applied in the bottom section.
1. In the bottom section, select **Select new shipment consolidation policy**
1. Choose a policy that enables consolidation with other open shipments of the same policy, for example, **CustomerOrderNo** policy.
1. Select **Release to warehouse**.
1. Select the second and third sales orders that you created for this scenario.
1. Select **Add** to add the lines to release to warehouse. Note that the *Default* policy is applied in the bottom section.
1. Select the second line, open the **Select new shipment consolidation policy** drop-down list and choose the *CustomerOrderNo* policy from the list.
1. Select **Release to warehouse** for both lines.

## Verify the shipments

Two shipments should have been created:

- The first shipment is created using **CustomerOrderNo** policy and contains two lines ;
- The second shipment is created using **Default** policy and contains one line.

To review created shipments, follow these steps.

1. Go to **Warehouse management > Shipments > All shipments**.
1. Find and select required shipment.
1. Review consolidation policy that is used during shipment creation in the **Shipment consolidation policy** field.

## Additional resources

- [About shipment consolidation policies](about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md)
- [Consolidate shipments](consolidate-shipments.md)
