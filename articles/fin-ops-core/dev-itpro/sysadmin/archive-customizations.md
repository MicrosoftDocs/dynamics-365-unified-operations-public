---
title: Customizations for archiving
description: This article describes how to add your customiztion to archive processes.
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

# Customizing Archive Scenarios

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

To move data from Live tables to History tables, it is necessary that
the underlying history table structures for transactions mirror the
structure of its corresponding live table.

## Add fields to history table through extension

If you have custom fields added to live tables, please refer to
following documentation on adding fields to history tables through
extension in D365 Finance & Operations:
<https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/extensibility/add-field-extension>

## Add additional table to archive scope 

Additional transaction tables can be added to the archive scope if they
are related to the parent live table directly or via tables in its
hierarchy chain.

**Create history table corresponding to the live table being added to the archive scope using the following convention:**

1\. Mirror all fields from the live table to the history table including
all metadata properties on the live table. SysRowVersion and
SysDataState tables are added by the system and are managed via table
metadata properties. These columns are not required to be added to the
history table.

2\. Do not mirror indexes from the live table to the history table. For
most history tables, a clustered index on RecId column should be
sufficient. Add additional columns to index based on query needs and to
maintain table relations needs such as a foreign key index.

3\. Add the created history table add its corresponding live table to
the archive scope. Archive scope is defined by the archive job
configuration which is managed by the corresponding archive type
registered in process automation.

4\. Find archive type class that implements
ArchiveServiceICreateArchiveJob interface. From this class find
ArchiveAutomationJobRequestCreator class for the archive type. Create
extension of ArchiveAutomationJobRequestCreator class to extend
createPostJobRequest() method to add new tables in archive scope using
Chain of Command (CoC) design pattern.

5\. In the extension class, see example below to add new tables to the
archive scope by extending createPostJobRequest() method. Also refer to
the original code to understand how archive contract is built to define
the archive scope.

**Example: Extending general ledger archive job request creator class to add an additional table.**

<!-- TODO get the code snip here. -->

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


