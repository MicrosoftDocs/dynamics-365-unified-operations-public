---
title: Consolidate inventory transactions (preview)
description: Learn how to consolidate inventory transaction data to help improve system performance with an outline on toggling the feature in your system.
author: banluo-ms
ms.author: banluo
ms.reviewer: kamaybac
ms.search.form: InventTransArchiveProcessForm
ms.topic: how-to
ms.date: 08/19/2026
ms.custom:
  - bap-template
---

# Consolidate inventory transactions (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Over time, the inventory transaction table (`InventTrans`) grows and consumes more database space. This article describes how to consolidate data about inventory transactions to help improve system performance and reduce storage consumption.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

> [!NOTE]
> Only financially updated inventory transactions can be consolidated in a selected closed ledger period. To be consolidated, financially updated outbound inventory transactions must have an issue status of *Sold*, and inbound inventory transactions must have a receipt status of *Purchased*.

When you consolidate inventory transactions, the system moves all related transactions to the `InventTransArchive` table. It then creates summary transactions in the `InventTrans` table, grouped by `ItemId` and `InventDimId`. If the combined quantity and cost fields for a group equal zero, the system doesn't create a new summary transaction.

If an `itemId` and `inventDimId` combination contains only one receipt or issue transaction, the transaction isn't consolidated.

> [!NOTE]
> After consolidating your inventory transactions, you can further optimize storage and system performance by using the *Archive with Dataverse long term retention* feature to move `InventTransArchive` records to a Microsoft Azure data lake. Learn more in [Archive inventory transaction data in Dynamics 365 Supply Chain Management](../../fin-ops-core/dev-itpro/sysadmin/archive-inventory.md).

## Considerations before consolidating inventory transactions

Before you consolidate inventory transactions, consider the following impacts on your business processes:

- **Transaction auditing** – When you audit inventory transactions from related documents (such as purchase order lines), you can view the consolidated transactions under **Archived transactions** until they're moved to long-term storage by using the *Archive with Dataverse Long term retention* feature. To review all consolidated transactions, go to **Inventory management** > **Periodic tasks** > **Clean up** > **Inventory transaction consolidation**.
- **Inventory closing** – You can't cancel inventory closing for periods that are consolidated.
- **Cost conversion** – You can't perform standard cost conversion for periods that are consolidated.
- **Inventory reports** – Reports that rely on detailed inventory transaction data show consolidated values instead of individual transactions. Affected reports include the inventory aging report and inventory value reports.
- **Inventory forecasts** – Forecasts that run during consolidated periods might produce different results because they use summary data rather than detailed transaction history.
- **Transaction-dependent operations** – You can't perform business processes that require the original inventory transactions, such as creating return orders and adjustments, after a period is consolidated.
- **Inventory settlements clean up** – If you plan to clean up inventory settlements, run *Inventory settlements clean up* before running *Inventory transaction consolidation*. This cleanup allows the system to process relevant closed `InventTrans` records before running the consolidation.
- **Clean up license plate registration history** – If you plan to clean up license plate registration history, run *Clean up license plate registration history* before running *Inventory transaction consolidation* to help improve consolidation performance.

## Prerequisites

### Version requirements

To consolidate inventory transactions, you must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.49 or later.

### Feature management requirements

To consolidate inventory transactions, the feature named *(Preview) Optimized inventory transaction consolidation* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

### Configure a number sequence for the consolidation process

Before you start the first inventory transaction consolidation job, configure a number sequence for the consolidation process. Configure this number sequence under **Inventory management** > **Inventory and warehouse management parameters** > **Number sequences** and assign a number sequence to the **Inventory transaction consolidation voucher** reference.

<a name="conditions"></a>

### Conditions for consolidating inventory transactions

You can consolidate inventory transactions only for periods that meet all of the following conditions:

- The ledger period is on hold or permanently closed.
- The period is at least one year before the current system date.
- Inventory closing ran on or after the end date of the consolidation period.
- The period length is less than 365 days from the last consolidation or from the earliest transaction date.
- No inventory recalculations are currently running or pending.
- No license plate cleanup jobs, cost conversion jobs, or inventory recalculations are currently running.
- All inventory transactions and related data pass the validation checks described in the next section.

## Validate inventory transactions

The system performs the following validations during the consolidation process to ensure data integrity and prevent inconsistencies:

- **Open issue transactions** – Settle all issue transactions through inventory closing before consolidation.
- **Physically updated transactions that aren't financially posted** – Financially post all transactions before consolidation to prevent downstream process issues.
- **Inconsistent inventory settlements** – Inventory settlements must sum to zero in the selected period.

> [!NOTE]
> The validation phase duration depends on the number of inventory transactions in your system. In environments with a high volume of inventory transactions, expect the validation to take considerable time.

## Allow inventory transaction consolidation without inventory closing

To allow inventory transaction consolidation without inventory closing, follow these steps:

1. Go to **Inventory management** > **Setup** > **Inventory and warehouse management parameters**.
1. Open the **General** tab.
1. Set **Allow inventory transaction consolidation without inventory closing** to one of the following values:
    - *No* – The system can only consolidate inventory transactions for closed inventory.
    - *Yes* – The system can also consolidate inventory transactions on unclosed inventory for items that use the *Standard cost* or *Moving average* inventory model.

    By default, this setting is permanently set to *No*. If you want to change it to *Yes*, contact Microsoft Technical Support for assistance.

> [!IMPORTANT]
> After you consolidate an inventory transaction, you can no longer close that inventory period.

## Consolidate your inventory transactions

To consolidate inventory transactions, follow these steps:

1. Go to **Inventory management** > **Periodic tasks** > **Clean up** > **Inventory transaction consolidation**.

    The **Inventory transaction consolidation** page appears and shows a list of consolidated process records.

1. On the Action Pane, select **Inventory transaction consolidation** to create an inventory transaction consolidation.
1. In the **Inventory transaction consolidation** dialog box, on the **Parameters** FastTab, set the following fields:

    - **To date in closed ledger period** – Select the end date of the consolidation period. The system consolidates all eligible transactions up to and including this date. Previously unconsolidated transactions before this date are included if they now meet the consolidation requirements.

    > [!NOTE]
    > Only periods that meet the [conditions for consolidating inventory transactions](#conditions) are available for selection.

1. On the **Run in the background** FastTab, set up batch processing details as you require. Follow the usual steps for batch jobs in Microsoft Dynamics 365 Supply Chain Management.
1. Select **OK**.
1. You receive a message that prompts you to confirm that you want to continue. Read the message carefully, and then select **Yes** if you want to continue.

    You receive a message that states that your inventory transaction consolidation job is added to the batch queue. The job starts to consolidate inventory transactions from the selected period. You can find the batch job under **System administration** > **Inquiries** > **Batch jobs**, where you can also review any logs generated by the batch tasks.

## View consolidated inventory transactions

The **Inventory transaction consolidation** page shows your full consolidating history. Each row in the grid shows information such as the date when the consolidation was created, the user who created it, and its status.

### Filter the list of consolidations

In the drop-down list at the top of the page, select one of the following values to filter the consolidations that appear in the grid:

- *Active* – Show only active consolidations.
- *All* – Show all consolidations.

You can also filter and sort the grid by using the column headers.

### Information shown in the grid

For each consolidation in the grid, the following information is provided:

- **Active** – A check mark indicates that the consolidation is active.
- **To date** – The date of the newest transaction that can be included in the consolidation.
- **Voucher** - The voucher for the consolidation session, generated by the configured number sequence.
- **Scheduled by** – The user account that created the consolidation.
- **Executed** – The date when the consolidation was created.
- **Stop current update** – A check mark indicates that the consolidation is in progress, but it has been paused.
- **State** – The processing status of the consolidation. The possible values are *Waiting*, *In progress*, and *Finished*.

### The grid toolbar

The toolbar above the grid provides the following buttons that you can use to work with a selected consolidation:

- **Consolidated transactions** – View the full details of the selected consolidation. The **Consolidated transactions** page shows all the transactions in the consolidation. To view more information about a specific transaction on the **Consolidated transactions** page, select it in the grid. On the Action Pane, select **Consolidated transaction details**. The **Consolidated transaction details** page shows information such as the ledger posting, related subledger references, and financial dimensions.
- **Pause** – Pause a selected consolidation that is currently being processed. The pause takes effect only after the archiving task is generated. Therefore, there might be a short delay before the pause takes effect. If a consolidation is paused, a check mark appears in its **Stop current update** field.
- **Resume** – Resume processing for a selected consolidation that is currently paused.
- **Progress details** – Open a log that shows the progress of your inventory consolidation jobs.

## Extend your code to support custom fields

If your `InventTrans` table contains one or more custom fields, you might need to extend the code to support them, depending on how they are named.

- If the custom field has the same name in both `InventTrans` and `InventTransArchive`, add it to the `InventoryArchiveFields` field group on `InventTrans`. No code is required—the engine automatically resolves the matching field on `InventTransArchive`.
- If the field names differ between the two tables, use the field mapper extension described in this section.

> [!IMPORTANT]
> The pattern for mapping custom field names changed in Supply Chain Management version 10.0.47. In version 10.0.46 and earlier, you mapped custom fields by extending the `InventTransArchiveProcessTask` and `InventTransArchiveSqlStatementHelper` classes. In version 10.0.47 and later, you map custom fields by extending the `InventTransArchiveFieldMapper` class. If your customizations still use the legacy extension pattern, you must migrate them to use the new pattern. You can't run inventory transaction consolidation until you migrate your customizations to use the new extension pattern.

In Supply Chain Management version 10.0.47 and later, custom field mapping is done through a dedicated `InventTransArchiveFieldMapper` class. Create a Chain of Command (CoC) extension and override the two list methods. Each method returns a `List` of field IDs that the consolidation engine adds to the source query (`InventTrans`) and the destination insert (`InventTransArchive`).

The following sample code includes the `CreatedBy` field from `InventTrans` and writes it to a custom `InventTransCreatedBy` field on `InventTransArchive`.

```xpp
[ExtensionOf(classStr(InventTransArchiveFieldMapper))]
final class InventTransArchiveFieldMapper_Foundation_Extension
{
    public List getInventTransFields()
    {
        List inventTransFields = next getInventTransFields();

        inventTransFields.addEnd(fieldNum(InventTrans, CreatedBy));

        return inventTransFields;
    }

    public List getInventTransArchiveFields()
    {
        List inventTransArchiveFields = next getInventTransArchiveFields();

        inventTransArchiveFields.addEnd(fieldNum(InventTransArchive, InventTransCreatedBy));

        return inventTransArchiveFields;
    }
}
```

Keep the following points in mind when you write the extension:

- **The engine pairs the two lists positionally.** The first field returned by `getInventTransFields()` is paired with the first field returned by `getInventTransArchiveFields()`, and so on. The lists must contain the same number of entries in the same order.
- **Always call `next` and append to the returned list.** This step preserves the contributions of any other extensions and keeps your code forward-compatible.

## Related information

- [Consolidate inventory transactions FAQ](inventory-transactions-consolidation-faq.md)
