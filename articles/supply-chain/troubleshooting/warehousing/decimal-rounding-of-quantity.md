---
title: Decimal rounding of the physical updating quantity is incorrect
description: When you generate a packing slip, the outbound load contains a quantity that doesn't match the decimal precision that is defined in the unit.
author: GalynaFedorova
ms.date: 5/31/2021
ms.topic: troubleshooting
ms.search.form: WHSLoadPlanningListPage_WHSSalesPackingSlipPost, WHSLoadTable_WHSSalesPackingSlipPost
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: v-gfedorova
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.18
---

# Decimal rounding of the physical updating quantity is incorrect

Error code: SYS19589

## Symptoms

When you generate a packing slip, the outbound load contains a quantity that doesn't match the decimal precision that is defined in the unit.

When you try to generate a packing slip, the system shows the following error message:

> Decimal rounding of the physical updating quantity in the unit %1 is incorrect.

Therefore, you can't generate the packing slip for the load.

## Cause

The system evaluates whether the decimal rounding of the shipping quantity corresponds to the decimal precision that is defined for the shipping unit. When the system rounds the shipping quantity to the specified number of decimal places, if it finds that the rounded shipping quantity doesn't match the actual shipping quantity, you can't generate the packing slip. For example, this issue might occur if the sales quantity is 1.75 kilograms (kg), but the decimal precision is set to *1*.

## Resolution

The load or shipment is currently in a state where packing slip generation fails. To fix this issue, complete one of the following tasks:

- Review your load lines, and make adjustments to ensure that the quantity can be cleanly converted without decimal numbers and any other rounding issues.
- Review your load lines, and make adjustments to ensure that the unit and quantity are aligned with the decimal precision of the unit.

### Review your load lines, and make adjustments to ensure that the quantity can be cleanly converted without decimal numbers and any other rounding issues

Use the following procedure to review your load lines and make adjustments to ensure that the quantity can be cleanly converted without decimal numbers and any other rounding issues.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the packing slip can't be generated for.
1. On the Action Pane, on the **Ship and receive** tab, in the **Reverse** group, select **Reverse shipment confirmation**.
1. On the **Load lines** tab, select the load line for the item that causes an issue.
1. Select **Reduce picked quantity** to adjust the picked quantity.
1. On the **Line details** tab, select **Order**.
1. Set the **Quantity** field to the picked quantity (that is, the value of the **Work created quantity** field), so that packing slip generation can proceed.

### Review your load lines, and make adjustments to ensure that the unit and quantity are aligned with the decimal precision of the unit

Use the following procedure to review your load lines and make adjustments to ensure that the unit and quantity are aligned with the decimal precision of the unit.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the packing slip can't be generated for.
1. On the **Load lines** FastTab, select the load line for the item that causes an issue. Make a note of the value of the **Quantity** and **Unit** fields.
1. Go to **Organization administration \> Units \> Units**.
1. Select the unit that the packing slip can't be generated for.
1. Adjust the value of the **Decimal precision** field as required.
