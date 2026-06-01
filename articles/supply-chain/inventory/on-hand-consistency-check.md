---
title: Troubleshoot on-hand inventory problems with the on-hand consistency check
description: Learn how to run the on-hand consistency check in Dynamics 365 Supply Chain Management, the performance impact, and how the Skip on-hand aggregation and clean up parameter interacts with the on-hand database cleanup jobs.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: SysConsistencyCheckForm
ms.topic: how-to
ms.date: 06/01/2026
ms.custom:
  - bap-template
---

# Troubleshoot on-hand inventory problems with the on-hand consistency check

The on-hand consistency check is a corruption-recovery tool that rebuilds the on-hand inventory tables (`InventSum` and, for warehouse management items, `WHSInventReserve`) from the inventory transactions table (`InventTrans`). Use it when you have confirmed on-hand data corruption—not as a periodic maintenance task.

This article explains when to run the check, how to run it safely, the performance characteristics you should plan for, and how the **Skip on-hand aggregation and clean up in on-hand consistency check** parameter interacts with the standard on-hand database cleanup jobs.

## Symptoms that justify running the check

Run the on-hand consistency check only after you confirm one or more of the following conditions:

- The **On-hand list** shows a quantity that doesn't match the sum of the related inventory transactions for the same dimensions.
- Inventory close or recalculation fails with an error referencing negative on-hand for an item whose item model group doesn't allow negative inventory (for example, *Inventory closing can't proceed because available physical on-hand inventory on item \<Item\> is currently negative*).
- A user, integration, or a data migration directly modified the `InventSum`, `WHSInventReserve`, or `InventTrans` table outside of standard posting paths.

If none of these conditions apply, don't run the check. The dedicated on-hand entries cleanup jobs are the correct tool for routine maintenance.

## When not to run the check

Here are some rules that illustrate when not to run the on-hand consistency check:

- Don't schedule the on-hand consistency check as a recurring batch job. It isn't a maintenance routine.
- Don't run it across all items during business hours. The check replays the entire `InventTrans` history per item and takes locks on `InventSum` and `WHSInventReserve`.
- Don't run it with **Check/Fix** set to *Fix error* as your first action. Always run it in *Check* mode first and review the log.
- Don't run it as a precaution before or after upgrades, cleanup jobs, or routine close. None of those operations corrupt on-hand data.

## How to run the check safely

To run the on-hand consistency check, follow these steps:

1. Go to **System administration** \> **Periodic tasks** \> **Database** \> **Consistency check**.
1. Set **Module** to *Inventory management*.
1. Expand the **Item** tree, and select the **On-hand** check box. If you suspect transaction-level corruption, select the **Inventory transactions** checkbox too.
1. Click on the text in the **Item** row (not the check box) so that the entire row has a blue background.
1. Open the **More** menu (**...**) and select **Dialog**.
1. Use the dialog box to filter the run to the specific item or item range that's affected. Running on *all items* is rarely the right choice.
1. Select **OK** to close the filter dialog.
1. In the **Consistency check** dialog, set **Check/Fix** to *Check* and then select **OK** to run the check. Review the log when it completes.
1. Select **Show messages** (bell icon at the top-right of the page) to open the **Action center** and review the messages for any errors or warnings.
1. If errors are confirmed, repeat this procedure with **Check/Fix** set to *Fix error*, ideally as a batch job outside business hours.

## Performance considerations

The run time of the on-hand consistency check scales with the volume of `InventTrans` history for the items in scope, not with the current on-hand quantity. An item with a long posting history takes longer to rebuild than an item with few transactions, even if both currently have similar on-hand values.

To keep the run predictable:

- **Filter by item** – Use the dialog filter to scope the run to the affected items. Running on *all items* should be reserved for documented disaster recovery scenarios.
- **Run in batch and outside business hours** – The fix run takes exclusive locks on `InventSum` and `WHSInventReserve` rows for each item it touches. Concurrent posting against the same item can deadlock or be blocked.
- **Be aware of the cleanup side effect** – With the default parameter setting, the fix run also runs the equivalent of an on-hand cleanup job for each item in scope, which adds time to the run. Set the **Skip on-hand aggregation and clean up in on-hand consistency check** parameter to *Yes* if you want the fix run to focus only on rebuilding the on-hand tables. Learn more about this option in [Choose whether to apply on-hand aggregation and clean up](#choose-whether-to-apply-on-hand-aggregation-and-clean-up).

## Choose whether to apply on-hand aggregation and clean up

You can choose to either run or skip on-hand cleanup when the on-hand consistency check runs in *Fix error* mode. The **Skip on-hand aggregation and clean up in on-hand consistency check** parameter controls this option. To set this option, follow these steps:

1. Go to **Inventory management** \> **Setup** \> **Inventory and warehouse management parameters**.
1. Open the **General** tab.
1. In the **On-hand consistency check clean up** field group, set **Skip on-hand aggregation and clean up in on-hand consistency check** to one of the following values: 
    - *Yes* – The consistency check skips the on-hand cleanup side effect and focuses solely on rebuilding the on-hand tables. This choice results in a faster run, but zero-quantity rows aren't cleaned up.
    - *No* – The consistency check includes the on-hand cleanup side effect. It also aggregates and deletes zero-quantity rows for the items in scope. This choice results in a longer run time, but it tidies up the on-hand tables. This value is the default setting.

### What the check does in fix mode

When you run the on-hand consistency check with **Check/Fix** set to *Fix error*, the system performs the following steps for each item in scope:

1. **Always** – The system rebuilds `InventSum` (and `WHSInventReserve` for warehouse management items) from `InventTrans`. This is the corruption fix itself.
1. **Only when the parameter is *No* (default)** – The system also performs the following on-hand cleanup work for that item:
    - **On-hand entries aggregation by financial dimensions** – Aggregates zero-quantity `InventSum` rows up to the financial inventory dimension level. This operation uses the same logic as the standalone *On-hand entries aggregation by financial dimensions* cleanup job, scoped to the item.
    - **On-hand cleanup** – For warehouse management items, runs the same logic as the *Warehouse management on-hand entries cleanup* job to delete zero-quantity rows in `InventSum` and `WHSInventReserve` for the item. For non-warehouse-management items, the system runs the same logic as the *On-hand entries cleanup* job for the item's tracking-dimension rows.

If the aggregation or cleanup step fails for a specific item, the system logs a warning (*On-hand clean up is failed for item \<Item\> in consistency check*) and continues with the next item. The recalculation work for that item is still completed—only the cleanup operation is skipped.

### When to skip on-hand aggregation and clean up

Set **Skip on-hand aggregation and clean up in on-hand consistency check** to *Yes* in any of the following situations:

- You already scheduled the on-hand cleanup jobs and want the consistency check to focus only on rebuilding the on-hand tables.
- You want the fix run to finish faster, because the per-item cleanup work is skipped.
- You need to preserve zero-quantity rows that downstream historical reporting depends on, such as *Physical inventory by inventory dimension* with **As of date** set, or *On-hand list* with **Closed transactions** selected.
- You're running the fix on a tight maintenance window and can't accept the additional runtime of the inline cleanup.

### When not to skip on-hand aggregation and clean up

Set **Skip on-hand aggregation and clean up in on-hand consistency check** to *No* in either of the following situations:

- The on-hand cleanup jobs aren't yet scheduled in the environment and you want the fix run to also tidy up zero-quantity rows for the affected items.
- The scope of the fix run is small (a few items) and the additional cleanup time isn't a concern.

### Relationship to the standalone cleanup jobs

The standalone on-hand cleanup jobs are the correct tool for ongoing database maintenance. The consistency check, even with the cleanup side effect enabled, isn't a substitute for them.

| Job | Path | Purpose |
|---|---|---|
| On-hand entries cleanup | **Inventory management** \> **Periodic tasks** \> **Clean up** \> **On-hand entries cleanup** | Deletes closed and unused on-hand entries for items with tracking dimensions. |
| Warehouse management on-hand entries cleanup | **Inventory management** \> **Periodic tasks** \> **Clean up** \> **Warehouse management on-hand entries cleanup** | Deletes zero-quantity rows in `InventSum` and `WHSInventReserve` for warehouse management items. |
| On-hand entries aggregation by financial dimensions | **Inventory management** \> **Periodic tasks** \> **Clean up** \> **On-hand entries aggregation by financial dimensions** | Aggregates zero-quantity `InventSum` rows up to the financial inventory dimension level. |

Learn more in [Cleanup routines in Dynamics 365 Finance and Dynamics 365 Supply Chain Management](/dynamics365/fin-ops-core/dev-itpro/sysadmin/cleanuproutines?toc=/dynamics365/supply-chain/toc.json) and [Warehouse management on-hand entries cleanup job](/dynamics365/supply-chain/warehousing/onhand-cleanup).

## Reports that can be affected by cleanup

The cleanup process removes zero-quantity rows from the on-hand tables. This removal happens both when you run the standalone cleanup jobs and when you run the on-hand consistency check in *Fix error* mode with the **Skip on-hand aggregation and clean up in on-hand consistency check** parameter set to *No*. These rows don't contribute to current on-hand values, but several historical and "as of date" reports read them directly. After cleanup, those reports might return incomplete or missing data for periods where on-hand rows are removed.

Reports that depend on zero-quantity on-hand rows include those listed in the following table.

| Report | Impact when rows are deleted |
|---|---|
| *Inventory aging report* | "As of date" snapshots and aging buckets might be missing rows for inventory dimensions that have since dropped to zero quantity. |
| *Historical inventory financial calculation (Russia)* | Historical inventory value calculations rely on the full on-hand row history. Deleted zero-quantity rows can cause incorrect financial snapshots for past dates. |
| *Physical quantity summary engine (China)* | Physical quantity summaries that aggregate by inventory dimension might be missing closed or zero-quantity rows after cleanup. |
| *Physical inventory by inventory dimension* | When the **As of date** parameter is set, or when **Closed transactions** is selected, deleted rows no longer appear in the report output. |
| *On-hand list* (with the **Quantity \<\> 0** filter cleared or **Closed transactions** selected in **Dimensions display**) | Closed or zero-quantity dimensions no longer appear at the level (for example, license plate) where they were deleted. |

### How to mitigate the impact on reports

To mitigate the impact of cleanup on historical and "as of date" reports, use the following approaches:

- **Don't run the consistency check in *Fix error* mode with the default parameter setting if you rely on these reports for the items in scope** – Set **Skip on-hand aggregation and clean up in on-hand consistency check** to *Yes* for that run, so the recalculation doesn't also delete zero-quantity rows.
- **Run the historical reports before you schedule the cleanup jobs in environments where the reports are business-critical** – Reports that are already generated aren't affected retroactively.
- **Weigh the trade-off per environment** – The cleanup jobs and the inline cleanup in the consistency check exist for performance reasons. The performance gains are real, and the lost dimension-level visibility is usually acceptable. However, it isn't acceptable in environments where the reports listed earlier are part of statutory or business-critical reporting.

## Recommended workflow when corruption is suspected

If you suspect on-hand data corruption, use the following workflow to investigate and resolve it:

1. **Identify the affected item** – Use the original error message, the **On-hand list**, and **Inventory transactions** to confirm which item has corrupted on-hand data.
1. **Back up if you're in a position to do so** – The fix is set-based and not easily reversible.
1. **Run the check in *Check* mode for that item only** – Use the dialog filter to scope the run. Review the log.
1. **Decide on the parameter setting** – If the environment has scheduled cleanup jobs that already manage on-hand rows, set **Skip on-hand aggregation and clean up in on-hand consistency check** to *Yes* for this run. Otherwise, leave it at *No* so the fix also tidies up zero-quantity rows.
1. **Rerun in *Fix error* mode as a batch job** outside business hours.
1. **Verify** – After the fix completes, re-check the **On-hand list** and the original error condition.

## Related articles

- [Warehouse management on-hand entries cleanup job](/dynamics365/supply-chain/warehousing/onhand-cleanup)
- [Cleanup routines in Dynamics 365 Finance and Dynamics 365 Supply Chain Management](/dynamics365/fin-ops-core/dev-itpro/sysadmin/cleanuproutines?toc=/dynamics365/supply-chain/toc.json)
