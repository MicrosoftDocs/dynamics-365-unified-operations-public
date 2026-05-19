---
title: Run an on-hand consistency check
description: Learn when to run an on-hand consistency check, what it does, and how to run it for one or more items in Supply Chain Management.
author: ChihunL
ms.author: chihunlee
ms.reviewer: kamaybac
ms.search.form: SysConsistencyCheck
ms.topic: how-to
ms.date: 05/13/2026
ms.custom: 
  - bap-template
---

# Run an on-hand consistency check

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Supply Chain Management provides an on-hand consistency check that recalculates inventory on-hand data from the inventory transactions (`InventTrans`) table. The check reconstructs the `InventSum` and `WHSInventReserve` tables for the items that you select, so that the on-hand list and physical inventory match the underlying transactions.

## When to run an on-hand consistency check

Run an on-hand consistency check when you observe symptoms such as the following for one or more items:

- Negative on-hand quantities that can't be explained by posted transactions.
- Physical inventory or available quantity that doesn't match the sum of posted inventory transactions.
- Discrepancies between the on-hand list and the underlying transaction history.

These symptoms typically indicate that the `InventSum` or `WHSInventReserve` tables are out of sync with `InventTrans`. The most common cause is a data inconsistency introduced by a script or external process that updated `InventTrans` directly without recalculating the summary tables. Running the consistency check in *Fix error* mode rebuilds the summary tables from the transactions, which resolves the discrepancy.

> [!NOTE]
> If Inventory Visibility is enabled, complete the additional preparation steps in [Run on-hand consistency checks while Inventory Visibility is enabled](inventory-onhand-consistency-check.md) before you run the check.

## Run a consistency check for selected items

To rebuild on-hand data for one or more specific items, follow these steps:

1. Go to **System administration \> Periodic tasks \> Database \> Consistency check**.
1. In the **Consistency check** dialog, set the following values:

    - **Module:** *Inventory management*
    - **Check/Fix:** *Fix error*

1. Expand the **Inventory management** tree, expand **Item**, and then select the **On-hand** checkbox.
1. With the **Item** node still in focus, open the **More** menu (three dots) and select **Dialog**.
1. In the dialog, filter for the specific item or items that you want to check.
1. Select **OK** to run the check. To run it asynchronously, use the **Batch** tab to schedule it as a batch job.

> [!TIP]
> Scope the check to a single item, or to as few items as possible, whenever you can. Running an on-hand consistency check for all items processes the entire `InventTrans` table and can take a long time on large datasets. Limiting the scope through the **Dialog** filter makes the check finish much faster and reduces the risk of timeouts.

If the *Fix error* run doesn't resolve the discrepancy, contact Microsoft Support or your partner.

## Speed up the check by skipping non-essential clean up

For very large datasets, you can shorten the run time of the consistency check by skipping the aggregation and clean-up steps that the check performs alongside the core recalculation. The recalculation that recreates `InventSum` records still runs; only the non-essential clean up is skipped.

To turn on this option, follow these steps:

1. Go to **Inventory management** > **Setup** > **Inventory and warehouse management parameters**.
1. On the **General** tab, in the **On-hand consistency check clean up** section, set **Skip on-hand aggregation and clean up in on-hand consistency check** to *Yes*.

The setting applies the next time you run the consistency check with **Check/Fix** set to *Fix error*. When the option is enabled, the check skips inventory-sum aggregation by financial inventory dimensions and the removal of obsolete or closed `InventSum` rows. Leave the option set to *No* if you want the check to also consolidate and remove obsolete `InventSum` rows as part of the run.

## Related information

- [Run on-hand consistency checks while Inventory Visibility is enabled](inventory-onhand-consistency-check.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
