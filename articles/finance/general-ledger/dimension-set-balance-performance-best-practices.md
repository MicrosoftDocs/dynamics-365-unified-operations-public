---
title: Dimension set balance best practices
description: Guidance for users to avoid slowdowns and poor performance for misuse of financial dimension sets
author: ethanrimes
ms.author: ethankallett
ms.topic: article
ms.date: 02/23/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2026-02-23
ms.search.form: DimensionFocus, LedgerTrialBalanceListPage
---

# Best practices for managing financial dimension sets

[!include [banner](../includes/banner.md)]

This article suggests practices for managing dimension set balances that help keep trial balance reports, balance initialization, and financial reports running efficiently. Following these recommendations is important because misuse of dimension sets can degrade system performance for all users.

## Update vs. rebuild

Two options are available for refreshing dimension set balances. Run these updates before generating reports rather than concurrently to ensure the accuracy of their data.

- **Update balances** – This option processes only the transactions that were posted since the last update. It's a fast, incremental operation that adds new records to the existing balance.
- **Rebuild balances** – This option clears all existing balance data and recalculates from the very beginning. It's a much more resource-intensive operation.

In most situations, use **Update balances**. It's faster and places less load on the system.

> [!IMPORTANT]
>Don't cancel an update, even if it's taking a long time.

During updates and rebuilds of a dimension set, users can't view its trial balance.

## When to rebuild balances

Use **Rebuild balances** sparingly. In most cases, **Update balances** is sufficient. Use a rebuild when you identify a balance discrepancy and a balance update didn't resolve it.

> [!NOTE]
>If Trial Balance is correct but external reporting (Financial Reporter, MRDB) isn't, clearing or rebuilding balances has no impact and shouldn't be done.

## Limit the scope of balance calculations

Where possible, narrow the scope of balance calculations to avoid unnecessary processing.

- **Use date-range specific rebuilds** – Use date ranges that specifically target transactions that aren't yet added to the balances.
- **Don't include the current date in balance updates** - Including the current date in balance updates can lead to problems, as it settles balances while transactions are still being posted. At the latest, extend your date range days up to the current date minus 1.
- **Run calculations per legal entity** – Update balances per legal entity. For specific business cases, administrators can update balances for all legal entities via the dimension set form, though this process can be computationally expensive and time-consuming.

## Time balance calculations carefully

When and how you run balance calculations has a significant impact on overall system performance.

- **Run calculations sequentially** – Avoid running balance calculations for multiple dimension sets at the same time. Simultaneous balance updates and rebuilds can cause blocking and slowed performance. Running them one after another produces better performance than running them in parallel.
- **Avoid updates and rebuilds during year-end close** – Don't run updates or rebuilds while the year-end close process is in progress. Before year-end close completes, it automatically performs a targeted rebuild on a date range that might contain a large number of transactions. Running rebuilds in parallel during this time can be computationally expensive and unnecessary.
- **Avoid large operations during peak hours** – Large updates or rebuilds during periods of high system activity can slow down the experience for other users. Schedule them for off-peak times whenever possible.

## Only create dimension sets you need

Each update and rebuild cycle processes every active dimension set. Creating dimension sets that you don't actively use wastes system resources without providing any benefit. For example, if you never analyze the combination of main account and cost center together, don't create it as a financial dimension set.

For dimension sets that are no longer in use, consider clearing their balances rather than deleting them:

- Clearing balances effectively deactivates a dimension set without removing it, so it remains available if you need it again in the future.
- To clear balances, go to **General ledger** \> **Chart of accounts** \> **Dimensions** \> **Financial dimension sets**, and then select **Clear balances**.

## Schedule automated balance updates

> [!NOTE]
>The [Performance enhancement for general ledger dimension set balance calculation](financial-dimension-set-new.md) feature automatically schedules dimension set balance updates. Users with this feature enabled should disregard this best practice.

For environments where large transaction volumes are regularly posted or imported, scheduling periodic balance updates helps keep the number of unprocessed transactions low and thus prevents slowdowns when running reports. Schedule these jobs during off-peak hours, such as evenings, to minimize the impact on other users.

To set up a recurring update job, select the dimension set, and then select **Update**. In the pane that appears, select **Recurrence** under **Run in the background** to define the job schedule.

:::image type="content" source="media/update-job-recurrence.png" alt-text="Screenshot of the recurrence settings for scheduling a dimension set balance update job.":::

Keep the following points in mind:

- Running updates too frequently can slow performance. Choose a cadence that keeps data reasonably current without placing unnecessary load on the system. A default recommendation is to update balances daily, starting scheduled jobs soon after business hours. This recommendation might not fit your business needs.
- Some reports and inquiries automatically trigger a balance update. For example, selecting **Update** on the **Trial balance** list page runs an **Update balances** operation for that financial dimension set.
- Don't schedule a **Rebuild balances** job unless you have a specific, recurring need for it. If you must schedule a rebuild, run it infrequently - for example, monthly - and only during periods of minimal system activity.

## Factors influencing update performance

The time it takes to process balance updates depends on several factors:

- Number of journals to process
- Number of dimensions in your chart of accounts
- Complexity of dimension configurations
- Number of active dimension sets
- Number of distinct values used within each dimension
- Usage of [highly variable dimensions](../cost-accounting/high-var-dimensions.md) (highly specific and infrequently reused dimensions). For values of this nature, consider [financial tags](financial-tag.md).

To maximize performance, focus on optimizing these factors wherever possible.

## Enable the performance enhancement feature

The [**Performance enhancement for general ledger dimension set balance calculation**](financial-dimension-set-new.md) feature replaces the previous balance data model with a more scalable architecture. It significantly improves balance calculation performance, automatically schedules balance updates, and eliminates many of the manual management requirements for maintaining dimension set balances.

> [!WARNING]
> This feature might introduce breaking changes in some environments. Test it in a UAT or sandbox environment before you enable it in production.
>
> After you enable this feature, don't disable it.

## Disable change tracking on dimension set tables

Also, disable **change tracking** on dimension set tables where it's not required, such as intermediate tables. Change tracking adds overhead to tables that you frequently update. Reserve it for tables that reflect final computations where historical change visibility is a business or compliance requirement. In particular, consider disabling change tracking for **DimensionFocus** tables such as **DimensionFocusBalance**.

## Don't delete and recreate dimension sets

Don't delete and recreate a dimension set to resolve performance problems. Deleting and creating dimension sets can be compute and time intensive processes. These processes lead to further delays and slowdowns.

If you no longer need a dimension set, you might want to **clear** the balances instead of deleting the dimension set. For more information, see the **Only create dimension sets you need** section. If problems persist after following these practices, contact customer support.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
