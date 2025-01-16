---
title: Consolidate inventory transactions
description: Learn how to consolidate inventory transaction data to help improve system performance with an outline on toggling the feature in your system.
author: Weijiesa
ms.author: weijiesa
ms.topic: article
ms.date: 04/11/2024
ms.custom:
ms.reviewer: kamaybac
ms.search.form: InventTransArchiveProcessForm
---

# Consolidate inventory transactions

[!include [banner](../../includes/banner.md)]

Over time, the inventory transaction table (`InventTrans`) will continue to grow and consume more database space. Therefore, queries that are made against the table will gradually become slower. This article describes how you can use the *Inventory transaction consolidation* feature to consolidate data about inventory transactions to help improve system performance.

> [!NOTE]
> Only financially updated inventory transactions can be consolidated in a selected closed ledger period. To be consolidated, financially updated outbound inventory transactions must have an issue status of *Sold*, and inbound inventory transactions must have a receipt status of *Purchased*.

When you consolidate inventory transactions, all related transactions are moved to the `InventTransArchive` table. Inventory issue transactions and inventory receipt transactions are consolidated separately, based on the combination of the item ID (`itemId`) and inventory dimension ID (`inventDimId`), and they're put into the summarized issue and summarized receipt transactions.

If an `itemId` and `inventDimId` combination contains only one receipt or issue transaction, the transaction won't be consolidated.

> [!NOTE]
> After consolidating your inventory transactions, you can further optimize storage and system performance by using the *Archive with Dataverse long term retention* feature to move `InventTransArchive` records to a Microsoft Azure data lake. Learn more in [Archive inventory transaction data in Dynamics 365 Supply Chain Management](../../fin-ops-core/dev-itpro/sysadmin/archive-inventory.md).

## Turn on the feature in your system

If your system doesn't already include the feature that is described in this article, go to [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), and turn on the *Inventory transaction consolidation* feature. This feature can't be disabled after being enabled.

## Things to consider before you consolidate inventory transactions

Before you consolidate inventory transactions, you should consider the following business scenarios, because they'll be affected by the operation:

- When you audit inventory transactions from related documents, such as purchase order lines, they're shown as consolidated. To review the consolidated transactions, you must go to **Inventory management \> Periodic tasks \> Clean up \> Inventory transaction consolidation**.
- Inventory closing can't be canceled for consolidated periods.
- Standard cost conversion can't be done for consolidated periods.
- Inventory reports that are sourced from inventory transactions are affected when you consolidate inventory transactions. These reports include the inventory aging report and inventory value reports.
- Inventory forecasts might be affected if they're run during the time horizon of consolidated periods.
- All necessary actions (such as potential returns) on sales orders and their related inventory transactions should be completed before consolidating a period.

## Prerequisites

Inventory transactions can be consolidated only during periods where the following conditions are met:

- The ledger period must be closed.
- Inventory closing must be run on or after the to-period date of the consolidation.
- The period must be at least one year before the from-period date of the consolidation.
- There must not be any existing inventory recalculations.

## Consolidate your inventory transactions

To consolidate inventory transactions, follow these steps.

1. Go to **Inventory management** \> **Periodic tasks** \> **Clean up** \> **Inventory transaction consolidation**.

    The **Inventory transaction consolidation** page appears and shows a list of consolidated process records.

1. On the Action Pane, select **Inventory transaction consolidation** to create an inventory transaction consolidation.
1. In the **Inventory transaction consolidation** dialog box, on the **Parameters** FastTab, set the following fields:

    - **From date in closed ledger period** – Select the earliest transaction date to include in the consolidation.
    - **To date in closed ledger period** – Select the newest transaction date to include in the consolidation.

    > [!NOTE]
    > Only periods that meet the [prerequisites](#prerequisites) will be available for selection.

1. On the **Run in the background** FastTab, set up batch processing details as you require. Follow the usual steps for batch jobs in Microsoft Dynamics 365 Supply Chain Management.
1. Select **OK**.
1. You receive a message that prompts you to confirm that you want to continue. Read the message carefully, and then select **Yes** if you want to continue.

    You receive a message that states that your inventory transaction consolidation job is added to the batch queue. The job starts to consolidate inventory transactions from the selected period.

## View consolidated inventory transactions

The **Inventory transaction consolidation** page shows your full consolidating history. Each row in the grid shows information such as the date when the consolidation was created, the user who created it, and its status.

In the drop-down list at the top of the page select one of the following values to filter the consolidations that are shown in the grid:

- **Active** – Show only active consolidations.
- **All** – Show all consolidations.

For each consolidation in the grid, the following information is provided:

- **Active** – A check mark indicates that the consolidation is active.
- **From date** – The date of the oldest transaction that can be included in the consolidation.
- **To date** – The date of the newest transaction that can be included in the consolidation.
- **Scheduled by** – The user account that created the consolidation.
- **Executed** – The date when the consolidation was created.
- **Stop current update** – A check mark indicates that the consolidation is in progress, but it has been paused.
- **State** – The processing status of the consolidation. The possible values are *Waiting*, *In progress*, and *Finished*.

The toolbar above the grid provides the following buttons that you can use to work with a selected consolidation:

- **Consolidated transactions** – View the full details of the selected consolidation. The **Consolidated transactions** page that appears shows all the transactions in the consolidation.

    To view more information about a specific transaction on the **Consolidated transactions** page, select it in the grid, and then, on the Action Pane, select **Consolidated transaction details**. The **Consolidated transaction details** page that appears shows information such as the ledger posting, related subledger references, and financial dimensions.

- **Pause** – Pause a selected consolidation that is currently being processed. The pause takes effect only after the archiving task is generated. Therefore, there might be a short delay before the pause takes effect. If a consolidation is paused, a check mark appears in its **Stop current update** field.
- **Resume** – Resume processing for a selected consolidation that is currently paused.
- **Progress details** – Open a log that shows the progress of your inventory consolidation jobs.

## Extend your code to support custom fields

If the `InventTrans` table contains one or more custom fields, then you might need to extend the code to support them, depending on how they're named.

- If the custom fields from the `InventTrans` table have the same field names as in the `InventtransArchive` table, that means they're 1:1 mapped. Therefore, you can just put the custom fields into the `InventoryArchiveFields` fields group of the `inventTrans` table.
- If the custom field names in the `InventTrans` table don't match the field names in the `InventtransArchive` table, then you need to add code to map them. For example, if you have a system field called  `InventTrans.CreatedDateTime`, then you must create a field in the `InventTransArchive` table with a different name (such as `InventtransArchive.InventTransCreatedDateTime`) and add extensions to the `InventTransArchiveProcessTask` and  `InventTransArchiveSqlStatementHelper` classes, as shown in the following sample code.

The following sample code shows an example of how to add the required extension to the `InventTransArchiveProcessTask` class.

```xpp
[ExtensionOf(classStr(InventTransArchiveProcessTask))]
Final class InventTransArchiveProcessTask_Extension
{

    protected void addInventTransFields(SysDaSelection _selectionObject)
    {
        _selectionObject.add(fieldStr(InventTrans, ModifiedBy))
            .add(fieldStr(InventTrans, CreatedBy)).add(fieldStr(InventTrans, CreatedDateTime));

        next addInventTransFields(_selectionObject);
    }


    protected void addInventTransArchiveFields(SysDaSelection _selectionObject)
    {
        _selectionObject.add(fieldStr(InventTransArchive, InventTransModifiedBy))
            .add(fieldStr(InventTransArchive, InventTransCreatedBy)).add(fieldStr(InventTransArchive, InventTransCreatedDateTime));

        next addInventTransArchiveFields(_selectionObject);
    }
}
```

The following sample code shows an example of how to add the required extension to the `InventTransArchiveSqlStatementHelper` class.

```xpp
[ExtensionOf(classStr(InventTransArchiveSqlStatementHelper))]
final class InventTransArchiveSqlStatementHelper_Extension
{
    private str     inventTransModifiedBy;  
    private str     inventTransCreatedBy;
    private str     inventTransCreatedDateTime;

    protected void initialize()
    {
        next initialize();
        inventTransModifiedBy = new SysDictField(tablenum(InventTrans), fieldNum(InventTrans, ModifiedBy)).name(DbBackend::Sql);
        inventTransCreatedDateTime = new SysDictField(tablenum(InventTrans), fieldNum(InventTrans, CreatedDateTime)).name(DbBackend::Sql);
        inventTransCreatedBy = new SysDictField(tablenum(InventTrans), fieldNum(InventTrans, CreatedBy)).name(DbBackend::Sql);
    }

    protected str buildInventTransArchiveSelectionFieldsStatement()
    {
        str     ret;

        ret = next buildInventTransArchiveSelectionFieldsStatement();
        
        if (inventTransModifiedBy)
        {
            ret += ',';
            ret += strFmt('%1',  new SysDictField(tablenum(InventTransArchive), fieldNum(InventTransArchive, InventTransModifiedBy)).name(DbBackend::Sql));
        }

        if (inventTransCreatedBy)
        {
            ret += ',';
            ret += strFmt('%1',  new SysDictField(tablenum(InventTransArchive), fieldNum(InventTransArchive, InventTransCreatedBy)).name(DbBackend::Sql));
        }

        if (inventTransCreatedDateTime)
        {
            ret += ',';
            ret += strFmt('%1',  new SysDictField(tablenum(InventTransArchive), fieldNum(InventTransArchive, InventTransCreatedDateTime)).name(DbBackend::Sql));
        }

        return ret;
    }

    protected str buildInventTransTargetFieldsStatement()
    {
        str     ret;

        ret = next buildInventTransTargetFieldsStatement();

        if (inventTransModifiedBy)
        {
            ret += ',';
            ret += strFmt('%1', inventTransModifiedBy);
        }

        if (inventTransCreatedBy)
        {
            ret += ',';
            ret += strFmt('%1', inventTransCreatedBy);
        }

        if (inventTransCreatedDateTime)
        {
            ret += ',';
            ret += strFmt('%1', inventTransCreatedDateTime);
        }

        return ret;
    }
}
```

## Learn more

- [Consolidate inventory transactions FAQ](inventory-transactions-consolidation-faq.md)
