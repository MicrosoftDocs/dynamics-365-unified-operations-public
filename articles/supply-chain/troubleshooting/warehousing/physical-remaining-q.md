---
title: Physical remaining quantity in the unit must not be zero
description: When you generate a packing slip, the data that is supplied to it has a non-zero inventory quantity but a zero sales quantity.
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

# Physical remaining quantity in the unit must not be zero

Error code: SYS19591

## Symptoms

When you generate a packing slip, the data that is supplied to it has a non-zero inventory quantity but a zero sales quantity.

When you try to generate the packing slip, the system shows the following error message:

> Physical remaining quantity in the unit %1 must be other than zero.

Therefore, you can't generate the packing slip for the load.

## Cause

The system evaluates the physical remaining quantity in the inventory unit and the physical remaining quantity in the shipping unit. If the system finds that the physical remaining quantity in the shipping unit is 0 (zero), but the physical remaining quantity in the inventory unit isn't 0, you can't generate the packing slip. For example, this issue might occur if the sales unit and inventory unit for the item differ, and the conversion between units isn't accurate.

## Resolution

The load or shipment is currently in a state where packing slip generation fails. To fix this issue, complete one of the following tasks:

- Review your load lines, and make sure that all the related work has been completed at the final shipping location, and that the quantities match.
- Review your load lines, and make adjustments to ensure that the quantity can be cleanly converted without rounding issues.
- Review your load lines, and make adjustments to ensure that the unit and quantity are aligned with the decimal precision of the unit.
- Make sure that the inventory unit of measure is smaller than the sales unit of measure.

### Review your load lines, and make sure that all the related work has been completed at the final shipping location, and that the quantities match

Use the following procedure to review your load lines and make sure that all the related work has been completed at the final shipping location, and that the quantities match.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the shipment can't be confirmed for.
1. On the **Load lines** FastTab, select the load line.
1. Make a note of the value of the **Work created quantity** field.
1. On the Action Pane, on the **Loads** tab, in the **Related information** group, select **Work**.
1. Verify that the work has been completed at the final shipping location, and that the picked work quantity matches the created work quantity on the load line.
1. Repeat this procedure for all load lines to make sure that all criteria are met.

### Review your load lines, and make adjustments to ensure that the quantity can be cleanly converted without rounding issues

Use the following procedure to review your load lines and make adjustments to ensure that the quantity can be cleanly converted without rounding issues.

1. Go to **Warehouse management \> Loads \> All loads**.
1. Select the load that the packing slip can't be generated for.
1. On the Action Pane, on the **Ship and receive** tab, in the **Reverse** group, select **Reverse shipment confirmation**.
1. On the **Load lines** tab, select the load line for the item that exceeds the over-delivery.
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

### Make sure that the inventory unit of measure is smaller than the sales unit of measure

Make sure that the inventory unit of measure is smaller than the sales unit of measure. Consider reconfiguring the unit of measure for the item as required.
