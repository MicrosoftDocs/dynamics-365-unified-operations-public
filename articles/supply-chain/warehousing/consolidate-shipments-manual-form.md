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

# Consolidate shipments manually in Consolidate shipments form

[!include [banner](../includes/banner.md)]

*Released in version 10.0.3*

This demo will simulate a scenario where multiple orders are released to warehouse, and they will be consolidated later in **All shipments \> Consolidate shipments** form.

This scenario assumes that you went through shipment policies configuration scripts and have more than one consolidation policies (see [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md) for instructions).

Standard Contoso data is used with some additions done during configuration of policies.

## Sales orders creation

Go to **Accounts receivable \> Orders \> All sales orders** and create sales orders according to information below.

### Order set 1

Create two identical sales orders.

**Sales order 1 and 2**:

- In the **Customer account** field, select **US-007**.
- In the **Pool** field, select **ShipCons**.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

Create another two identical sales orders.

**Sales order 3 and 4**:

- In the **Customer account** field, select **US-007**;
- Leave **Pool** field empty.

Add an order line to each sales order.

**Line 1**:

- In the **Item number** field, select **A0001** (an item without filter code 4);
- In the **Quantity** field, enter **1.00**;
- Click **Inventory > Reservation** and then **Reserve lot** to reserve the order line.

## Release to warehouse

To release to warehouse a sales order using All sales orders form, follow these steps.

1. Go to **Accounts receivable > Orders > All sales orders**.
1. Find and select desired sales order.
1. On the Action Pane, on the **Warehouse** tab, click **Release to warehouse** to release a sales order.

Release all sales orders from the order set using instructions above.

## Consolidate shipments

1. Go to **Warehouse management > Shipments > All shipments**.
1. Find and select a shipment created when Sales order 1 was released to warehouse (this shipment **Shipment consolidation policy** field set to **Order pool**).
1. On the Action Pane, on the **Shipments** tab, click **Consolidate shipments**.
1. Verify shipments suggested for consolidation:
    - There is only one shipment with the same policy suggested for consolidation.
1. Close the **Shipment consolidation** form.
1. Find and select a shipment created when Sales order 3 was released to warehouse (this shipment **Shipment consolidation policy** field set to **Default**).
1. On the Action Pane, on the **Shipments** tab, click **Consolidate shipments**.
1. Verify there are no shipments suggested for consolidation.
1. Click **Show filters** icon to open **Filters** pane.
1. Remove **Order number** filter and click **Apply**.
1. Verify shipments suggested for consolidation:
    - There is only one shipment with the same policy suggested for consolidation.

## Related articles and demo scripts

- [About shipment consolidation policies](../warehousing/about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](../warehousing/configure-shipment-consolidation-policies.md)
- [Consolidate shipments](../warehousing/consolidate-shipments.md)
