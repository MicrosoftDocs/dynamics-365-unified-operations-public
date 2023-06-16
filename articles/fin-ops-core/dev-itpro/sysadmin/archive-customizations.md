---
title: Extend the archive solution to support custom tables and fields
description: This article describes how to add your customizations to archive processes.
author: alexeiantao
ms.author: alexeiantao
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 06/13/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Extend the archive solution to support custom tables and fields

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.34 GA -->

Data can be moved from live tables to history tables only if the underlying history table structures for transactions mirror the structure of the corresponding live table.

## Add all custom fields to history tables through extension

If you've added custom fields to live tables, you must extend your system's history table so that it includes those fields. For more information, see [Add fields to tables through extension](../extensibility/add-field-extension.md).

## Add tables to the archive scope

Transaction tables can be added to the archive scope if they're related to the parent live table either directly or via tables in its hierarchy chain.

Follow these conventions to create a history table that corresponds to a live table that's being added to the archive scope:

1. Mirror all fields from the live table to the history table. These fields include all metadata properties on the live table. `SysRowVersion` and `SysDataState` tables are added by the system and managed via table metadata properties. These columns don't have to be added to the history table.
1. Don't mirror indexes from the live table to the history table. For most history tables, a clustered index on the `RecId` column should suffice. Add additional columns to index based on query needs, and to maintain table relation needs such as a foreign key index.
1. Add the created history table and its corresponding live table to the archive scope. The archive scope is defined by the archive job configuration. That configuration is managed by the corresponding archive type that's registered in process automation.
1. Find the archive type class that implements the `ArchiveServiceICreateArchiveJob` interface. From this class, find the `ArchiveAutomationJobRequestCreator` class for the archive type. Create an extension of the `ArchiveAutomationJobRequestCreator` class. Extend the `createPostJobRequest()` method to add new tables in the archive scope by using the chain of command (CoC) design pattern.
1. In the extension class, add new tables to the archive scope by extending the `createPostJobRequest()` method. See the example that follows. Also review the original code to learn how the archive contract is built to define the archive scope.

## Example: Extend the general ledger archive job request creator class to add an additional table

The following example shows how to extend the `LedgerArchiveAutomationJobRequestCreator` class to add an additional table to the archive scope.

```xpp
[ExtensionOf(classStr(LedgerArchiveAutomationJobRequestCreator))]

final class public final class LedgerArchiveAutomationJobRequestCreator_Extension
{
    public ArchiveJobPostRequest
    createPostJobRequest(LedgerArchiveAutomationCriteria _criteria)
    {
        ArchiveJobPostRequest postRequest = next createPostJobRequest(_criteria);
        ArchiveServiceArchiveJobPostRequestBuilder builder = ArchiveServiceArchiveJobPostRequestBuilder::constructFromArchiveJobPostRequest(postRequest);

        // Using builder add additional live tables, history tables, join conditions and where conditions (if needed)
        // Example: Adding new ledger trans settlement table
        DictTable generalJournalAccountEntryTable = new DictTable(tableNum(GeneralJournalAccountEntry));
        str generalJournalEntryTableName = generalJournalEntryTable.name(DbBackend::Sql);
        DictTable newLedgerTransSettlementTable = new DictTable(tableNum(NewLedgerTransSettlement));
        DictTable newLedgerTransSettlementHistoryTable = new DictTable(tableNum(NewLedgerTransSettlementHistory));
        str nltsTableName = newLedgerTransSettlementTable.name(DbBackend::Sql);
        str nltsHisTableName = NewLedgerTransSettlementHistoryTable.name(DbBackend::Sql);
        builder.addDataSource(nltsTableName, nltsHisTableName, generalJournalAccountEntryTableName)
            .addJoinCondition(nltsTableName,
            newLedgerTransSettlementTable.fieldName(fieldNum(NewLedgerTransSettlement, TransRecId), DbBackend::Sql),
            generalJournalAccountEntryTable.fieldName(fieldNum(GeneralJournalAccountEntry, RecId))).addPartitionWhereCondition(nltsTableName);
        return builder.finalizeArchiveJobPostRequest();
    }
}
```
