---
title: Decimal rounding of the physical updating quantity is incorrect
description: As part of the packing slip generation, the outbound load contains quantity that doesn't match to the decimal precision defined in the unit
author: Henrikan
ms.date: 5/31/2021
ms.topic: troubleshooting
ms.search.form: WHSLoadPlanningListPage_WHSSalesPackingSlipPost, WHSLoadTable_WHSSalesPackingSlipPost
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: Henrikan
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.18
---

# Decimal rounding of the physical updating quantity is incorrect

Error code: SYS19589

## Symptoms

When you are generating a packing slip, the outbound load contains a quantity that doesn't match to the decimal precision defined in the unit.

When you try to generate a packing slip, the system shows the following error message:

> Decimal rounding of the physical updating quantity in the unit %1 is incorrect.

Therefore, you can't generate the packing slip for the load.

## Cause

The system evaluates whether the decimal rounding of the shipping quantity corresponds to the decimal precision defined per shipping unit. If the system finds that rounding the shipping quantity to the specified number of decimal places defined in the unit that doesn't match to the shipping unit, you can't generate the packing slip. For example, this issue might occur if the sales quantity is 1.75 kg, but decimal precision is set to 1.

<!-- KFM: Something is wrong with the sentence "If the system finds that rounding the shipping quantity to the specified number of decimal places defined in the unit that doesn't match to the shipping unit, you can't generate the packing slip.". Please revise. -->

## Resolution

The load or shipment is currently in a state where packing slip generation fails.

To fix this issue, complete one of the following tasks:

- Check your load lines and make adjustments to ensure that quantity can be cleanly converted without decimal numbers and any other rounding issues.
- Check your load lines and make adjustments to ensure that the unit and quantity are aligned with the decimal precision of the unit.

### Make adjustments to ensure that quantity can be cleanly converted without rounding issues

Use the following procedure to check your load lines and make adjustments to ensure that quantity can be cleanly converted without decimal numbers and any other rounding issues:

1. Go to **Warehouse management \> Loads \> All loads**.  
1. Select the load that the packing slip can't be generated for.
1. On the Action Pane, open the **Ship and receive** tab and, from the **Reverse** group, select **Reverse shipment confirmation**.
1. Open the **Load lines** tab and select the load line for the item that exceeds the over delivery. <!-- KFM: Is this really about over delivery? -->
1. Select **Reduce picked quantity** to adjust the picked quantity.
1. Open the **Line details** tab and and select **Order**.
1. In the **Quantity** field, set the value to the picked quantity (**Work created quantity**) to allow packing slip generation to proceed.  

### Make sure that your units and quantities are aligned with the decimal precision of the unit

Use the following procedure to check your load lines and make adjustments to ensure that the unit and quantity are aligned with the decimal precision of the unit:

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the packing slip can't be generated for.
1. On the **Load lines** FastTab, select the load line for the item that causes an issue. Make a note of the value of the **Quantity** and **Unit** field.
1. Go to **Organization administration \> Units \> Units**.
1. Select the unit that the packing slip can't be generated for.
1. Adjust the value of the **Decimal precision** as required.
