---
title: Allow row version change tracking for data entities 
description: This article explains how to allow row version change tracking for data entities and tables for Finance and Operations apps.
author: peakerbl
ms.date: 09/28/2022
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: 
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: peakerbl
ms.search.validFrom: 2022-10-10
ms.dyn365.ops.version: 10.0.31
---

# Allow Row version change tracking for tables and Data entities

[!include[banner](../includes/banner.md)]

## Allow Row version change tracking on tables

A new metadata property, **Allow Row Version Change Tracking**, of type **No/Yes** has been added. All table(s) used as data source for a data entity, must have the property set to **Yes** to allow row version change tracking for the entity. 



When this metadata property is set to **Yes** for a table in, the AOT automatically adds a new SQL row version field to the table named **SysRowVersionNumber**. This field cannot be manually deleted or modified in AOT. The Finance and Operations implementation does not populate row version values to existing records. This means that the value will be NULL for rows that existed before the SQL row version field was added. This will not impact data synchronization since full sync is always performed first. Any incremental changes will have SQL row version populated. 

The **SQL row version** column performs version stamping of table rows. SQL server maintains a database level counter that is incremented for each insert or update operation. Every time a row with a row version column is modified or inserted, the incremented database row version counter is inserted in the row version column

**The SQL roversionL**

The SQL row version column is read only in SQL. Validation has been added in X++ validator to generate a compilation error if the **SysRowVersionNumber** field is specified in X++ insert or update statements. Also, Defensive fixes have been added in both managed and native Kernel to make sure that the **SysRowVersionNumber** field does not get added to kernel generated DML statements. This defensive fix will not guard against any direct raw SQL executed by X++ code using ADO.NET command object or X++ raw SQL statement object.

## Allow Row version change tracking on Data entities

A new metadata property **Allow Row Version Change Tracking** of type **No/Yes** has been added to the **AxDataEntityView**. Not all existing data entities are configured to support Row version change tracking, this is mainly due to the complexity of the entity configuration. 

**Data entlty validation rules**

| Rule | Comments | Error message |
|----------|--------|--------|
| Data entity with custom change tracking query is not supported.  |   | Change tracking cannot be enabled since F&O entity %1 uses a custom query. |
| Data entity with range filters is not supported. | Range filters can cause records to get filtered out from the view which will not be change tracked as delete. |  Change tracking cannot be enabled since the F&O entity %1 contains Ranges. |
| Data entity with data source(s) having group by condition is not supported  | | Change tracking cannot be enabled since the data source %1 in the F&O entity %2 contains  Group By conditions. |
| Count of data source(s) in a data entity must be below threshold. | Max limit is controlled bu Microsoft and is currenlty set to 10. | Change tracking cannot be enabled since the F&O entity %1 contains more than %2 data sources. |
| Data entity with data source having range filters is not supported. |  | Change tracking cannot be enabled since the data source %1 in the F&O entity %2 contains Ranges. |
| Data entity with non-table data source is not supported. | Nested data entities or data entities containing view(s) as data source is not supported. | Change tracking cannot be enabled since the data source %2 in the F&O entity %1 is not a table. |
| All tables in the data entity must allow row version change tracking. | | Change tracking cannot be enabled since the Allow Row Version Change Tracking property is not set to Yes for the table related to data source %2 for the F&O entity %1. |
| Data sources in the data entity must be joined using an outer join. | Inner join and exists join is not supported. Non outer join can cause records to get filtered out from the view which will not be change tracked as delete. | Change tracking cannot be enabled  since the Join Mode between the data source %1 and the data source %2 in the F&O entity %3 is not %4. | 
| Relationship between data sources must be many-to-one. | One-to-many relationship is not supported. One-to-many  relationship will generate duplicate Virtual table entityids. |  Change tracking cannot be enabled  since the Relation %1 between the data source %2 and the data source %3 in the F&O entity %4 is one-to-many. |
| Only normal relation constraint is supported for data sources in a data entity. | | Change tracking cannot be enabled   since the Relation %1 between the data source %2 and the data source %3 in the F&O entity %4 is not set to Normal. |
| Rule to validate entities containing time state enabled tables. | Root table with **Apply Date** filter is not supported, it can cause record disappearance. Time state tables not supported for related data sources since it can cause either record disappearance or one-to-many relationships. |  Change tracking cannot be enabled since the data source %3 in the F&O entity %1 has a time state enabled table %2. |

 




The **SysRowVersionNumber** column of the primary table is added to the data entity view when **Allow Row Version Change Tracking** is set to Yes for an Entity.

**Tracking deletes and cleanup**

Data entity row deletions are change tracked using the **AifChangeTrackingDeletedObject** tables.

There is a system batch job **Delete tracking history clean-up** that cleans up records in the **AifChangeTrackingDeletedObject** table that has exceeded the retention period. Records is deleted in batches until the timeout criteria is reached. By default the job runs every day at 1 AM. The recurrence and frequency of the job is configurable in **System Administration>Batch Jobs**. The retention period, delete batch size and timeout is configurable using **SysGlobalConfiguration settings**.

## Retrieve row version entity changes

For details for how to use the **RetrieveEntityChanges** API, see TBA
 
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
