---
title: Archive customization 
description: This article describes how Archive customization 
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# Archive customization 

The archival framework supports extensions to include table custom fields and custom tables in supported functional scenarios. 

Add custom fields in history tables and BI entities 

Custom fields added to a standard table, are always required to be added to the corresponding history table and the business intelligence entity. Customized BI entity is required to be refreshed in Dataverse to archive data with Dataverse long term retention. 

History tables 

Transactions records are moved as is to the history tables. Therefore, it is mandatory that history table schema matches with its corresponding live table. 

A screenshot of a computer

Description automatically generated with low confidence 

All columns in a live table must be present in its mirrored history table. 

Columns exclusion Rule: SysRowVersion and SysDataState columns are added by the platform and are managed via table metadata properties. These columns are not required to be added to the history table. 

Beginning in release 10.0.39 D365 Finance & Operations supports archiving of General Ledger in the standard product. Development in other functional areas is in progress to support archiving of other transaction data such as Sales Order, Inventory Transactions etc. 

Business Entity 

Dataverse interacts with Finance and Operation using business entities. These virtual entities are used to retrieve data from Finance and Operations database and save it to their corresponding Dataverse managed data lake tables.  

Important: Don’t add relationships between the entities. 

Step 1: Add fields to history table via extension 

Archive framework requires that all live table columns be mirrored in the corresponding history tables. Use table extensions to add the custom fields to history tables. 

Refer to documentation on how to add fields to history tables through extension in D365 Finance & Operations: https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/extensibility/add-field-extension 

Step 2:  Add fields to business intelligence (BI) entities via extension 

Additional fields that are added to live tables are required to be added to corresponding BI entities. 

Step 3: Refresh Virtual entity in Dataverse 

The customized business entity must be refreshed in Dataverse to archive data in Dataverse long term retention store.  

Add new table to archive scenario 

Addition tables can be included in the archive scenario if they have a direct or indirect relationship to the main live table. 

Create a history table corresponding to the live table being added to the archive scope using the following convention: 

Create a new history table mirroring all fields from the corresponding live table including all metadata properties on the live table. See column exclusion rule above. 

Do not mirror indexes from the live table in the history table. For most history tables, a clustered index on RecId column is sufficient. Create additional index to improve query performance if needed and to maintain foreign key relationships. 

Extend ArchiveAutomationJobRequestCreator class for a scenario to add the new table to archive table graph. See code example below. 
 
 

Example: extending general ledger archive job request creator class to add a new table. 
