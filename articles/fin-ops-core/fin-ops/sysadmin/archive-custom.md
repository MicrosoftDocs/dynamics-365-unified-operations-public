---
title: Archive customization (preview)
description: This article describes how the archive feature supports customization 
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# Archive customization 

This article describes how the archive feature supports customization. The archival framework supports extensions to include table custom fields and custom tables in supported functional scenarios. 

## Add custom fields in history tables and business intelligence entities 

Custom fields added to a standard table are required to be added to the corresponding history table and the business intelligence entity. Customized BI entity is required to be refreshed in Dataverse to archive data with Dataverse long term retention. 

### History tables 

Transactions records are moved to the history tables and it's mandatory that history table schema matches with its corresponding live table. 
All columns in a live table must be present in its mirrored history table. 

 - Columns exclusion rule: SysRowVersion and SysDataState columns are added by the platform and are managed via table metadata properties. These columns aren't required to be added to the history table. 

Beginning in Dynamics 365 finance and operations version 10.0.39 archive General Ledger is in the standard product. Development in other functional areas is in progress to support archiving of other transaction data such as Sales Order or Inventory transactions. 

### Business entity 

Dataverse interacts with Dynamics 365 finance and operations using business entities. These virtual entities are used to retrieve data from the Dynamics 365 finance and operations database and save it to their corresponding Dataverse managed data lake tables.  

>[!Important]
> Don’t add relationships between the entities. 

### Step 1: Add fields to history table via extension 
The archive framework requires all live table columns be mirrored in the corresponding history tables. Use table extensions to add the custom fields to history tables. 
For more information about how to add fields to history tables through extension in Dynamics 365 finance and operations, see [Add fields to tables through extension](../dev-itpro/extensibility/add-field-extension). 

### Step 2: Add fields to business intelligence entities via extension 
Additional fields added to live tables are required to be added to corresponding BI entities. 

### Step 3: Refresh Virtual entity in Dataverse 
The customized business entity must be refreshed in Dataverse to archive data in Dataverse long term retention store.  

### Add new table to archive scenario 

Additional tables can be included in the archive scenario if they have a direct or indirect relationship to the main live table. 
To create a history table corresponding to the live table in the archive scope, follow these steps:  
1. Create a new history table mirroring all fields from the corresponding live table including all metadata properties on the live table. See column exclusion rule above.
2. Don't mirror indexes from the live table in the history table. For most history tables, a clustered index on RecId column is sufficient. Create additional index to improve query performance if needed and to maintain foreign key relationships.
3. Extend ArchiveAutomationJobRequestCreator class for a scenario to add the new table to archive table graph.

#### Dynamics 365 finance and operations table names in live, history and Dataverse managed data lake   

|Scenario|Live table     |  History table   |  Bi Entity     | Dataverse managed data lake table    |
|---|---|---|---|---|
|Finance General Ledger | GENERALJOURNALACCOUNTENTRY | GENERALJOURNALACCOUNTENTRYHISTORY | GeneraljournalaccountentryBiEntity|  mserp_GeneraljournalaccountentryBiEntity  |
|     |GENERALJOURNALACCOUNTENTRY_W  |GENERALJOURNALACCOUNTENTRYHISTORY_W  |GeneraljournalaccountentrywBiEntity |mserp_GeneraljournalaccountentrywBiEntity  |
|     |GENERALJOURNALENTRY  |GENERALJOURNALENTRYHISTORY  |cus  |mserp_GeneraljournalentryBiEntity  |
|     |GENERALJOURNALENTRY_W  |GENERALJOURNALENTRYHISTORY_W  |GeneraljournalentrywBiEntity  |mserp_GeneraljournalentrywBiEntity  |
|     |LEDGERCONSOLIDATEHISTREF  |LEDGERCONSOLIDATEHISTREFHISTORY  |LedgerconsolidatehistrefBiEntity  |mserp_LedgerconsolidatehistrefBiEntity  |
|     |LEDGERENTRY  | LEDGERENTRYHISTORY  |LedgerentryBiEntity  |mserp_LedgerentryBiEntity  |
|     |LEDGERENTRYJOURNAL  |LEDGERENTRYJOURNALHISTORY  |LedgerentryjournalBiEntity  |mserp_LedgerentryjournalBiEntity  |
|     |LEDGERENTRYJOURNALIZING  |LEDGERENTRYJOURNALIZINGHISTORY  |LedgerentryjournalizingBiEntity  |mserp_LedgerentryjournalizingBiEntity  |
|     |LEDGERTRANSSETTLEMENT  |LEDGERTRANSSETTLEMENTHISTORY  |LedgertranssettlementBiEntity  |mserp_LedgertranssettlementBiEntity  |
|     |SUBLEDGERVOUCHERGENERALJOURNALENTRY  |SUBLEDGERVOUCHERGENERALJOURNALENTRYHISTORY  |SubledgervouchergeneraljournalentryBiEntity  |mserp_SubledgervouchergeneraljournalentryBiEntity  |
|Supply Chain Management Sales order|MCRRETURNSALESTABLE  |MCRRETURNSALESTABLEHISTORY  |McrreturnsalestableBiEntity  |mserp_McrreturnsalestableBiEntity  |
|     |MCRSALESLINE  |MCRSALESLINEHISTORY  |McrsaleslineBiEntity  |mserp_McrsaleslineBiEntity  |
|     |MCRSALESTABLE |MCRSALESTABLEHISTORY |McrsalestableBiEntity |mserp_McrsalestableBiEntity  |
|     |RETAILSALESLINE |RETAILSALESLINEHISTORY  |RetailsaleslineBiEntity  |mserp_RetailsaleslineBiEntity  |
|     |RETAILSALESTABLE|  RETAILSALESTABLEHISTORY  |RetailsalestableBiEntity  |mserp_RetailsalestableBiEntity  |
|     |SALESLINE  |SALESLINEHISTORY  |SaleslineBiEntity  |mserp_SaleslineBiEntity  |
|     |SALESLINE_BR  |SALESLINEHISTORY_BR  |SaleslinebrBiEntity  |mserp_SaleslinebrBiEntity  |
|     | SALESLINE_IN  |SALESLINEHISTORY_IN  |SaleslineinBiEntity  |mserp_SaleslineinBiEntity  |
|     | SALESLINE_W  |SALESLINEHISTORY_W  |SaleslinewBiEntity  |mserp_SaleslinewBiEntity  |
|     | SALESTABLE  |SALESTABLEHISTORY  |SalestableBiEntity  | mserp_SalestableBiEntity  |
|     |SALESTABLE_BR  |SALESTABLEHISTORY_BR  |SalestablebrBiEntity  |mserp_SalestablebrBiEntity  |
|     |SALESTABLE_RU |SALESTABLEHISTORY_RU  |SalestableruBiEntity  |mserp_SalestableruBiEntity  |
|     |SALESTABLE_W  |SALESTABLEHISTORY_W  |SalestablewBiEntity  |mserp_SalestablewBiEntity  |
|Supply Chain Management Inventory transaction|INVENTTRANSARCHIVE  |INVENTTRANSARCHIVEHISTORY  |InventtransarchiveBiEntity  |mserp_InventTransArchiveBiEntity  |




