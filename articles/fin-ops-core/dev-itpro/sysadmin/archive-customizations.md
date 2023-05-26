---
title: Extend the archive solution to support custom tables and fields
description: This article describes how to add your customizations to archive processes.
author: alexeiantao
ms.author: alexeiantao
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 06/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Extend the archive solution to support custom tables and fields

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

To move data from live tables to history tables, it is necessary that the underlying history table structures for transactions mirror the structure of its corresponding live table.

## Add all custom fields to history tables through extension

If you have custom fields added to live tables, you must extend your system's history table to include those fields. For more information, see [Add fields to tables through extension](../extensibility/add-field-extension.md).

## Add additional tables to the archive scope

Additional transaction tables can be added to the archive scope if they are related to the parent live table directly or via tables in its hierarchy chain.

Create history table corresponding to the live table being added to the archive scope using the following conventions:

1. Mirror all fields from the live table to the history table including all metadata properties on the live table. SysRowVersion and SysDataState tables are added by the system and are managed via table
metadata properties. These columns aren't required to be added to the history table.

1. Don't mirror indexes from the live table to the history table. For most history tables, a clustered index on RecId column should be sufficient. Add additional columns to index based on query needs and to
maintain table relations needs such as a foreign key index.

1. Add the created history table add its corresponding live table to the archive scope. Archive scope is defined by the archive job configuration which is managed by the corresponding archive type registered in process automation.

1. Find archive type class that implements `ArchiveServiceICreateArchiveJob` interface. From this class find `ArchiveAutomationJobRequestCreator` class for the archive type. Create extension of `ArchiveAutomationJobRequestCreator` class to extend `createPostJobRequest()` method to add new tables in archive scope using chain of command (CoC) design pattern.

1. In the extension class, see example below to add new tables to the archive scope by extending `createPostJobRequest()` method. Also refer to the original code to understand how archive contract is built to define the archive scope.

## Example: Extend the general ledger archive job request creator class to add an additional table

<!-- TODO get the code snip here. -->
<!-- KFM: Is the following code the code you mean? Is this X++? Should we add some indenting? Do I see incorrect carriage returns here? -->

```xpp
\[ExtensionOf(classStr(LedgerArchiveAutomationJobRequestCreator))\]

final class public final class
LedgerArchiveAutomationJobRequestCreator_Extension

{

public ArchiveJobPostRequest
createPostJobRequest(LedgerArchiveAutomationCriteria \_criteria)

{

ArchiveJobPostRequest postRequest = next
createPostJobRequest(\_criteria);

ArchiveServiceArchiveJobPostRequestBuilder builder =
ArchiveServiceArchiveJobPostRequestBuilder::constructFromArchiveJobPostRequest(postRequest);

// Using builder add additional live tables, history tables, join
conditions and where conditions (if needed)

// Example: Adding new ledger trans settlement table

DictTable generalJournalAccountEntryTable = new
DictTable(tableNum(GeneralJournalAccountEntry));

str generalJournalEntryTableName =
generalJournalEntryTable.name(DbBackend::Sql);

DictTable newLedgerTransSettlementTable = new
DictTable(tableNum(NewLedgerTransSettlement));

DictTable newLedgerTransSettlementHistoryTable = new
DictTable(tableNum(NewLedgerTransSettlementHistory));

str nltsTableName = newLedgerTransSettlementTable.name(DbBackend::Sql);

str nltsHisTableName =
NewLedgerTransSettlementHistoryTable.name(DbBackend::Sql);

builder.addDataSource(nltsTableName, nltsHisTableName,
generalJournalAccountEntryTableName)

.addJoinCondition(

nltsTableName,

newLedgerTransSettlementTable.fieldName(fieldNum(NewLedgerTransSettlement,
TransRecId), DbBackend::Sql),

generalJournalAccountEntryTable.fieldName(fieldNum(GeneralJournalAccountEntry,
RecId)))

.addPartitionWhereCondition(nltsTableName);

return builder.finalizeArchiveJobPostRequest();

}

}
```
