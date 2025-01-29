---
title: Archive customization
description: Learn about how the archive feature in Microsoft Dynamics 365 finance and operations apps supports table customizations, including code examples.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 06/13/2024
ms.custom:
ms.reviewer: twheeloc

---
# Archive customization (preview)

This article describes how the archive feature in Microsoft Dynamics 365 finance and operations apps supports customization. The archival framework supports extensions to include custom table fields and custom tables in supported functional scenarios.

## Add custom fields in history tables and business intelligence entities

Custom fields that are added to a standard table must be added to the corresponding history table and the business intelligence (BI) entity. The customized BI entity must be refreshed in Dataverse to archive data with Dataverse long term retention.

### History tables

Transactions records are moved to the history tables. The schema of a history table must match its corresponding live table. All columns in the live table must be present in its mirrored history table.

<a id="excl-rule"></a>**Column exclusion rule:** `SysRowVersion` and `SysDataState` columns are added by the platform and managed by using table metadata properties. These columns don't have to be added to the history tables.

### Business entity

Dataverse interacts with finance and Operations. These virtual entities are used to retrieve data from the finance and operations database and save it to the corresponding tables in the Dataverse long term retention.

> [!IMPORTANT]
> Don't add relationships between the entities.

### Step 1: Add fields to the history table via extensions

The archival framework requires that all live table columns are mirrored in the corresponding history tables. Use table extensions to add the custom fields to history tables. For more information about how to add fields to history tables through extension in finance and operations apps, see [Add fields to tables through extension](../../dev-itpro/extensibility/add-field-extension.md).

### Step 2: Add fields to BI entities via extensions

Additional fields that are added to live tables must be added to the corresponding BI entities.

### Step 3: Refresh the virtual entity in Dataverse

The customized business entity must be refreshed in Dataverse to archive data in the Dataverse long-term retention store.

## Add new tables to the archive scenario

Additional tables can be included in the archive scenario if they have a direct or indirect relationship with the main live table.

To create a history table that corresponds to the live table in the archive scope, follow these steps.

1. Create a new history table that mirrors all fields from the corresponding live table, including all metadata properties on the live table. See the [column exclusion rule](#excl-rule) earlier in this article.
1. Don't mirror indexes from the live table in the history table. For most history tables, a clustered index on the `RecId` column is sufficient. Create an additional index to improve query performance as required and to maintain foreign key relationships.
1. Extend the `ArchiveAutomationJobRequestCreator` class for a scenario to add the new table to archive table chart.

### Code example

The following example shows how to customize the General ledger archive job request creator class to add a new table.

```
using Microsoft.Dynamics.Archive.Contracts; 
[ExtensionOf(classStr(LedgerArchiveAutomationJobRequestCreator] 
final class LedgerArchiveAutomationJobRequestCreator_GeneralLedger_Extension 
{
    public ArchiveJobPostRequest createPostJobRequestForArchiveTrans(LedgerArchiveTrans _archiveTrans 
    { 
        ArchiveJobPostRequest postRequest = next createPostJobRequestForArchiveTrans(_archiveTrans; 
        ArchiveServiceArchiveJobPostRequestBuilder builder = 
            ArchiveServiceArchiveJobPostRequestBuilder::createFromArchiveJobPostRequest(postRequest; 

        // Use builder to add more live tables, history tables, join conditions and where conditions (if needed 
        // Example: Adding my new general ledger table to archive table graph 
        var generalJournalAccountEntryTable = new DictTable(tableNum(GeneralJournalAccountEntry; 
        var generalJournalAccountEntryTableName = generalJournalAccountEntryTable.name(DbBackend::Sql; 
        var newMyNewGeneralLedgerTable = new DictTable(tableNum(MyNewGeneralLedgerTable; 
        var newMyNewGeneralLedgerTableName = newMyNewGeneralLedgerTable.name(DbBackend::Sql; 
        var newMyNewGeneralLedgerTableHistory = new DictTable(tableNum(MyNewGeneralLedgerTableHistory; 
        var newMyNewGeneralLedgerTableHistoryName = newMyNewGeneralLedgerTableHistory.name(DbBackend::Sql; 
        var myNewGeneralLedgerTableSourceTable = ArchiveServiceSourceTableConfiguration::newForSourceTable( 
            newMyNewGeneralLedgerTableName, 
            newMyNewGeneralLedgerTableHistoryName, 
            tableStr(MyNewGeneralLedgerTableBiEntity; 

        // Add parent table 
        myNewGeneralLedgerTableSourceTable.parmParentSourceTableName(generalJournalAccountEntryTableName; 
        builder.addSourceTableForLongTermRetention(myNewGeneralLedgerTableSourceTable 
            .addJoinCondition(newMyNewGeneralLedgerTableName, 
            newMyNewGeneralLedgerTable.fieldName(fieldNum(MyNewGeneralLedgerTable, GeneralJournalAccountEntry, DbBackend::Sql, 
            generalJournalAccountEntryTable.fieldName(fieldNum(GeneralJournalAccountEntry, RecId, DbBackend::Sql; 

        return builder.completeArchiveJobPostRequest(; 
```

### Finance and operations table names in live, history, and Dataverse-managed data lake tables

| Scenario | Live table | History table | BI entity | Dataverse-managed data lake table |
|---|---|---|---|---|
| Finance General ledger | GENERALJOURNALACCOUNTENTRY | GENERALJOURNALACCOUNTENTRYHISTORY | GeneraljournalaccountentryBiEntity | mserp\_GeneraljournalaccountentryBiEntity |
| | GENERALJOURNALACCOUNTENTRY\_W | GENERALJOURNALACCOUNTENTRYHISTORY\_W | GeneraljournalaccountentrywBiEntity | mserp\_GeneraljournalaccountentrywBiEntity |
| | GENERALJOURNALENTRY | GENERALJOURNALENTRYHISTORY | cus | mserp\_GeneraljournalentryBiEntity |
| | GENERALJOURNALENTRY\_W | GENERALJOURNALENTRYHISTORY\_W | GeneraljournalentrywBiEntity | mserp\_GeneraljournalentrywBiEntity |
| | LEDGERCONSOLIDATEHISTREF | LEDGERCONSOLIDATEHISTREFHISTORY | LedgerconsolidatehistrefBiEntity | mserp\_LedgerconsolidatehistrefBiEntity |
| | LEDGERENTRY | LEDGERENTRYHISTORY | LedgerentryBiEntity | mserp\_LedgerentryBiEntity |
| | LEDGERENTRYJOURNAL | LEDGERENTRYJOURNALHISTORY | LedgerentryjournalBiEntity | mserp\_LedgerentryjournalBiEntity |
| | LEDGERENTRYJOURNALIZING | LEDGERENTRYJOURNALIZINGHISTORY | LedgerentryjournalizingBiEntity | mserp\_LedgerentryjournalizingBiEntity |
| | LEDGERTRANSSETTLEMENT | LEDGERTRANSSETTLEMENTHISTORY | LedgertranssettlementBiEntity | mserp\_LedgertranssettlementBiEntity |
| | SUBLEDGERVOUCHERGENERALJOURNALENTRY | SUBLEDGERVOUCHERGENERALJOURNALENTRYHISTORY | SubledgervouchergeneraljournalentryBiEntity |mserp\_SubledgervouchergeneraljournalentryBiEntity |
| Supply Chain Management Sales order | MCRRETURNSALESTABLE | MCRRETURNSALESTABLEHISTORY | McrreturnsalestableBiEntity | mserp\_McrreturnsalestableBiEntity |
| | MCRSALESLINE | MCRSALESLINEHISTORY | McrsaleslineBiEntity | mserp\_McrsaleslineBiEntity |
| | MCRSALESTABLE | MCRSALESTABLEHISTORY | McrsalestableBiEntity | mserp\_McrsalestableBiEntity |
| | RETAILSALESLINE | RETAILSALESLINEHISTORY | RetailsaleslineBiEntity | mserp\_RetailsaleslineBiEntity |
| | RETAILSALESTABLE | RETAILSALESTABLEHISTORY | RetailsalestableBiEntity | mserp\_RetailsalestableBiEntity |
| | SALESLINE | SALESLINEHISTORY | SaleslineBiEntity | mserp\_SaleslineBiEntity |
| | SALESLINE\_BR | SALESLINEHISTORY\_BR | SaleslinebrBiEntity | mserp\_SaleslinebrBiEntity |
| | SALESLINE\_IN | SALESLINEHISTORY\_IN | SaleslineinBiEntity | mserp\_SaleslineinBiEntity |
| | SALESLINE\_W | SALESLINEHISTORY\_W | SaleslinewBiEntity | mserp\_SaleslinewBiEntity |
| | SALESTABLE | SALESTABLEHISTORY | SalestableBiEntity | mserp\_SalestableBiEntity |
| | SALESTABLE\_BR | SALESTABLEHISTORY\_BR | SalestablebrBiEntity | mserp\_SalestablebrBiEntity |
| | SALESTABLE\_RU | SALESTABLEHISTORY\_RU | SalestableruBiEntity | mserp\_SalestableruBiEntity |
| | SALESTABLE\_W | SALESTABLEHISTORY\_W | SalestablewBiEntity | mserp\_SalestablewBiEntity |
| Supply Chain Management Inventory transaction | INVENTTRANSARCHIVE | INVENTTRANSARCHIVEHISTORY | InventtransarchiveBiEntity | mserp\_InventTransArchiveBiEntity |
| Supply Chain Management Inventory Journal | INVENTJOURNALTABLE | INVENTJOURNALTABLEHISTORY | InventjournaltableBiEntity | mserp\_InventjournaltableBiEntity |
| | INVENTJOURNALTABLE_IN | INVENTJOURNALTABLE_INHISTORY | InventjournaltableinBiEntity | mserp\_InventjournaltableinBiEntity |
| | INVENTJOURNALTRANS | INVENTJOURNALTRANSHISTORY | InventjournaltransBiEntity | mserp\_InventjournaltransBiEntity |
| | INVENTJOURNALTRANS_IN | INVENTJOURNALTRANS_INHISTORY | InventjournaltransinBiEntity | mserp\_InventjournaltransinBiEntity |
| Finance Tax Trans | TAXTRANS | TAXTRANSHISTORY | TaxtransBiEntity | mserp\_TaxtransBiEntity |
| | TAXTRANS\_BR | TAXTRANSHISTORY\_BR | TaxtransbrBiEntity | mserp\_TaxtransbrBiEntity |
| | TAXTRANSGENERALJOURNALACCOUNTENTRY | TAXTRANSGENERALJOURNALACCOUNTENTRYHISTORY | TaxtransgeneraljournalaccountentryBiEntity | mserp\_TaxtransgeneraljournalaccountentryBiEntity |
| | TAXTRANS\_IN | TAXTRANSHISTORY\_IN | TaxtransinBiEntity | mserp\_TaxtransinBiEntity |
| | TAXTRANS_IT | TAXTRANSHISTORY\_IT | TaxtransitBiEntity | mserp\_TaxtransitBiEntity |
| | TAXTRANS_REPORTING | TAXTRANSHISTORY_REPORTING | TaxtransreportingBiEntity | mserp\_TaxtransreportingBiEntity |
| | TAXTRANS\_RU | TAXTRANSHISTORY\_RU | TaxtransruBiEntity | mserp\_TaxtransruBiEntity |
| | TAXTRANSSUBLEDGERJOURNALACCOUNTENTRY | TAXTRANSSUBLEDGERJOURNALACCOUNTENTRYHISTORY | TaxtranssubledgerjournalaccountentryBiEntity | mserp\_TaxtranssubledgerjournalaccountentryBiEntity |
| | TAXTRANS\_TH | TAXTRANSHISTORY\_TH | TaxtransthBiEntity | mserp\_TaxtransthBiEntity |
| | TAXTRANS\_W | TAXTRANSHISTORY\_W | TaxtranswBiEntity | mserp\_TaxtranswBiEntity | 
