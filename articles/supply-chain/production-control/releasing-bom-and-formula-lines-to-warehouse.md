---
title: Release BOM and formula lines to the warehouse
description: Learn about the process for releasing raw material for BOM lines and formula lines to the warehouse with an outline on methods for releasing BOM and formula lines.
author: johanhoffmann
ms.author: johanho
ms.topic: article
ms.date: 11/24/2026
ms.reviewer: kamaybac
ms.search.form: SysOperationTemplateForm, ProdParmReleaseToWarehouse, WHSReleaseToWarehouseProdBOM
ai-usage: ai-assisted
---

# Release BOM and formula lines to the warehouse

[!INCLUDE [banner](../includes/banner.md)]

This article describes the process for releasing raw material for bill of materials (BOM) lines and formula lines to the warehouse. When you release a BOM or formula line to the warehouse, the system first determines whether material is already available at the production input location on the shop floor where the material will be consumed for the production process.

- If the material is available at the production input location, the system picks it from that location immediately after the signal is given for the release of material to the warehouse.
- If the material isn't available at the production input location, the material release indicates that material must be moved from locations in the warehouse to the production input location. The system moves the material via warehouse work for raw material picking. Therefore, you must configure warehouse processes for raw material picking. Learn more in [Replenishment overview](../warehousing/replenishment.md) and [Control warehouse work by using work templates and location directives](../warehousing/control-warehouse-location-directives.md).

## Methods for releasing BOM and formula lines

You can configure the release of BOM and formula lines so that it occurs as part of the release of a production order or batch order. Alternatively, a batch job can control the release, or you can release the lines manually.

The **Production line release** parameter controls the method for releasing BOM and formula lines. Find this parameter at **Production control** > **Setup** > **Production parameters**.

- **Release BOM and formula lines as part of production or batch order release** – In this method, the system releases BOM and formula lines for a production or batch order as part of the process of releasing the order. Usually, during the release of a production or batch order, the system releases production jobs to the shop floor workers and prints production papers. During this process, the system also changes the status of the order to **Released**.
- **Release BOM and formula lines via a batch job or as a manual interaction** – In this method, you can release BOM and formula lines only through the **Automatic release of BOM and formula lines** batch job or as a manual interaction. To manually release BOM and formula lines, on the production order list page or the production order details page, on the Action Pane, select **Release to warehouse**.

For a quick demonstration of how to release BOM and formula lines to production by using a batch job, watch this short YouTube video:
[Release production picking to the warehouse in batch](https://www.youtube.com/watch?v=8urAJn50dQ8).

## Releasing the BOM and formula lines by using a batch job

The **Automatic release of BOM and formula lines** batch job goes through selected BOM and formula lines that have a remaining quantity to release. The job considers only orders that have a status of **Released**, **Started**, or **Reported as finished**. If a BOM or formula line has a remaining quantity to release, the job releases up to the quantity that the system can cover by the quantity that is already physically reserved and the quantity that is physically available.

If the system requires same-batch selection for a raw material, reservation during release can be constrained to inventory from a single batch for each BOM or formula line. When on-hand inventory is split across batches, the quantity available to reserve and release can be less than the total on-hand quantity. The default requirement is set in the released product's item model group and can be overridden on individual BOM or formula lines. Learn more in [Reserve the same batch for a production order](reserve-same-batch-production-order.md).

### Example of a batch job release

Batch-selection rules, such as same-batch selection, can further limit the physically available quantity in these examples when you enable those rules for the item or line.

| Scenario | Remaining quantity to release | Physically reserved quantity | Physically available quantity | Quantity released by the batch job |
|--|--|--|--|--|
| 1 | 100 | 20 | 90 | 100 |
| 2 | 100 | 20 | 70 | 90 |
| 3 | 100 | 0 | 90 | 90 |
| 4 | 100 | 0 | 110 | 100 |
| 5 | 100 | 20 | 0 | 20 |

### Batch job setup

In the query for the **Automatic release of BOM and formula lines** batch job, set up a filter criterion to specify how many days ahead the job should look for lines that have unreleased quantities. In the query for the job, use the **(LessThanDate())** function as a filter criterion in the **Raw material date** field.

The following illustration shows a production order that has two jobs, 10 and 20, that cover the assembly and packing for the production order. Each job is set up to consume a quantity of material. In this illustration, the release time fence that is indicated by the green arrow below the time line equals the number of days that you specify in the **(LessThanDate())** criterion. For example, **(LessThanDate(2))** indicates that the job should look for unreleased quantities only within a time fence of two days.

:::image type="content" source="media/production-order-batch-jobs-release-time-fence.png" alt-text="Diagram of production order jobs 10 and 20 on a timeline, each consuming material M9203, with a green arrow showing the release time fence." lightbox="media/production-order-batch-jobs-release-time-fence.png":::

## Releasing material per operation number or in proportion to the amount of finished goods

If you release materials by using the **On production order release** parameter setting, when you do a manual release, you have two options for controlling the material release:

- Release material per operation number.
- Release material in proportion to the amount of finished goods.

### Release material per operation number

Use the **Release to warehouse** page to control which operations receive the material release.

- Select **Production control** > **Production orders** > **All production orders**, select a production order, and then, on the **Warehouse** tab, select **Release to warehouse**. Use the **From Oper. No.** and **To Oper. No.** fields to specify the range of operation numbers.

The following illustration shows a production order that has two operations, 10 and 20. In this example, if you limit the release to operation 10, only material M9203 is released.

:::image type="content" source="media/material-release-per-operation-number.png" alt-text="Diagram of a production order timeline with operations 10 and 20, each marked with material M9203 at its start." lightbox="media/material-release-per-operation-number.png":::

For a quick demonstration of how to release material in proportion to the amount of finished goods, watch this short YouTube video about [enhancements to the production order release process](https://www.youtube.com/watch?v=Rm3ojAz6Zu0).

### Release material in proportion to the amount of finished goods

You can release raw material for a partial quantity of finished goods or in a specific unit.

- To release raw material for a partial quantity of finished goods, select **Production control** > **Production orders** > **All production orders**, select a production order, and then, on the **Warehouse** tab, select **Release to warehouse**. Enter a quantity in the **Quantity** field.

    For example, you create and schedule a production order for 1,000 pieces (pcs.). The shop floor supervisor plans to produce 100 pcs. in the next shift and wants to release materials only for that shift. In this case, the supervisor can use the **Quantity** field to release materials for the 100 pcs. planned for the next shift.

- To release raw material in a specific unit, select **Production control** > **Production orders** > **All production orders**, select a production order, and then, on the **Warehouse** tab, select **Release to warehouse**. Use the **Unit** field to select the unit of the finished good to release material in.

    The available units are defined in the unit sequence group ID of the finished good.

    For example, a finished good has the following unit conversion between pounds (lbs.) and pallet (PL): 1 PL = 100 lbs. To create a production order for 10,000 lbs. of the finished good, you can release raw materials for the number of pallets that you plan to produce. Select **PL** as the unit, and then select a corresponding number in the **Quantity** field.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
