---
# required metadata

title: Consolidate shipments manually using the Consolidate shipments page
description: This topic provides a scenario where multiple orders are released to the warehouse and then consolidated later using the Consolidate shipments page.
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
ms.dyn365.ops.version: 10.0.3

---

# Consolidate shipments manually using the Consolidate shipments page

[!include [banner](../includes/banner.md)]

This topic provides a scenario where multiple orders are released to the warehouse and then consolidated later using the **Consolidate shipments** page.

## Enable demo data

Each of the scenarios in this topic reference values and records included in the standard demo data provided for Supply Chain Management. If you'd like to run the exercises using the values provided here, be sure to work on an environment with the demo data installed, and set the legal entity to **USMF** before you begin.

## Set up shipment consolidation policies and product filters

The scenario described here assumes that you have already done the exercises and created the records described in [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md). Please do those exercises before continuing with this scenario.

## Create the sales orders for this scenario

Start by creating a collection of sales orders that you can work with. You must work with a warehouse that is enabled for advanced warehouse (WMS) processes, and the same warehouse must be used for each of the following sets of orders unless another warehouse is explicitly mentioned.

Go to **Accounts receivable \> Orders \> All sales orders** and create a collection of sales orders with the settings described in the following subsections.

### Create sales orders 1 and 2

Create two identical sales orders with the following settings:

- **Customer account** - *US-007*
- **Pool** - *ShipCons*
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

### Create sales orders 3 and 4

Create two identical sales orders with the following settings:

- **Customer account** - *US-007*
- **Pool** - (Leave empty)
- Add an order line with the following settings:
  - **Item number** - *A0001* (an item without a **Code 4** filter assigned)
  - **Quantity** - *1.00*
  - Select **Inventory \> Reservation** and then select **Reserve lot** on the action pane to reserve the order line.

## Release to warehouse

Release to warehouse each of the sales orders you created for this scenario by doing the following:

1. Go to **Accounts receivable \> Orders \> All sales orders**.
1. Find and select the target sales order.
1. On the action pane, open the **Warehouse** tab and select **Actions \> Release to warehouse** to release the selected sales order.
1. Repeat this procedure for each sales order you created for this scenario.

## Consolidate shipments

1. Go to **Warehouse management \> Shipments \> All shipments**.
1. Find and select a shipment created when sales order 1 was released to warehouse (with its **Shipment consolidation policy** field set to *Order pool*).
1. On the action pane, open the **Shipments** tab and then select **Shipments \> Consolidate shipments**.
1. Verify the shipments suggested for consolidation. There should only be one shipment with the same policy suggested for consolidation.
1. Close the **Shipment consolidation** page.
1. Find and select a shipment created when sales order 3 was released to warehouse (with its **Shipment consolidation policy** field set to *Default*).
1. On the action pane, open the **Shipments** tab and then select **Shipments \> Consolidate shipments**.
1. Verify that there are no shipments suggested for consolidation.
1. Select **Show filters** to open the **Filters** pane.
1. Remove the **Order number** filter and select **Apply**.
1. Verify the shipments suggested for consolidation. There should only be one shipment with the same policy suggested for consolidation.

## Additional resources

- [About shipment consolidation policies](about-shipment-consolidation-policies.md)  
- [Configure shipment consolidation policies](configure-shipment-consolidation-policies.md)
- [Consolidate shipments](consolidate-shipments.md)
