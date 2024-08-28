---
title: Consolidate shipments when the shipment consolidation policy is overridden
description: Learn about a scenario where one or more sales lines must be manually released to the warehouse from the Release to warehouse page.
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 05/12/2020
ms.custom:
ms.reviewer: kamaybac
ms.search.form: WHSShipConsolidationPolicy, WHSShipConsolidationWorkbench, WHSFilterGroupTable, WHSShipConsolidationSetShipment, WHSShipmentConsolidation, WHSFilterGenerallyAvail, WHSReleaseToWarehouse, WHSReleaseToWarehouseSalesOrder
---

# Consolidate shipments when the shipment consolidation policy is overridden

[!include [banner](../includes/banner.md)]

This article presents a scenario where one or more sales lines must be manually released to the warehouse from the **Release sales orders to warehouse** page, and the system-defined shipment consolidation policy must be overridden before the release. An override of the shipment consolidation policy might be required if, for example, an order that isn't usually consolidated with open shipments must be consolidated with open shipments.

During the scenario, you will create a set of sales orders and then override the default shipment consolidation policy before you release the orders to the warehouse.

## Make demo data available

The scenario in this article references values and records that are included in the standard demo data that is provided for Microsoft Dynamics 365 Supply Chain Management. If you want to use the values that are provided here as you do the exercises, be sure to work in an environment where the demo data is installed, and set the legal entity to **USMF** before you begin.

## Set up shipment consolidation policies and product filters

The scenario that is described here assumes that you've already turned on the feature, done the exercises in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md), and created the policies and other records that are described there. Be sure to do those exercises before you continue with this scenario.

## Create the sales orders for this scenario

1. Go to **Accounts receivable \> Orders \> All sales orders**, and create three identical sales orders that have the following settings:

    - **Customer account:** *US-002*

1. Add an order line that has the following settings:

    - **Item number:** *A0001* (an item that no **Code 4** filter is assigned to)
    - **Quantity:** *1.00*

1. Select **Inventory \> Reservation**, and then, on the Action Pane, select **Reserve lot** to reserve the order line.

## Release the sales orders from the Release sales orders to warehouse page

Follow these steps to override the shipment consolidation policy during the release to the warehouse.

1. Go to **Warehouse management \> Release to warehouse \> Release sales orders to warehouse**.
1. In the upper pane, select the first sales order that you created for this scenario.
1. Select **Add** to add the line to the release to the warehouse. Notice that the *Default* shipment consolidation policy is applied in the bottom pane.
1. In the bottom pane, select **Select new shipment consolidation policy**.
1. Select a policy that allows for consolidation with other open shipments of the same policy. For example, select the *CustomerOrderNo* policy.
1. Select **Release to warehouse**.
1. Select the second and third sales orders that you created for this scenario.
1. Select **Add** to add the lines to the release to the warehouse. Notice that the *Default* policy is applied in the bottom pane.
1. Select the second line, and then, in the **Select new shipment consolidation policy** field, select the *CustomerOrderNo* policy.
1. Select **Release to warehouse** for both lines.

## Verify the shipments

Two shipments should have been created:

- The first shipment contains two lines and was created by using the *CustomerOrderNo* shipment consolidation policy.
- The second shipment contains one line and was created by using the *Default* shipment consolidation policy.

Follow these steps to review the shipments that were created.

1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Find and select the required shipment.
1. In the **Shipment consolidation policy** field, review the consolidation policy that was used when the shipment was created.

## Related information

- [Shipment consolidation policies overview](about-shipment-consolidation-policies.md)
- [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]