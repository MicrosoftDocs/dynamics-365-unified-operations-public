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
| Data entity with custom change tracking query is not supported.  | Entities that use custom query for change tracking. Entities supply custom query by adding a static method called defaultCTQuery to the entity.  | Change tracking cannot be enabled since F&O entity %1 uses a custom query. |
| Data entity with range filters is not supported. | Range filters can cause records to get filtered out from the view which will not be change tracked as delete. |  Change tracking cannot be enabled since the F&O entity %1 contains Ranges. |
| High | 15% |
| Critical | 30% |
| Reserved capacity | 40% + Dedicated X threads |



The **SysRowVersionNumber** column of the primary table is added to the data entity view when **Allow Row Version Change Tracking** is set to Yes for an Entity.

**Tracking deletes and cleanup**

Data entity row deletions are change tracked using the **AifChangeTrackingDeletedObject** tables.

There is a system batch job **Delete tracking history clean-up** that cleans up records in the **AifChangeTrackingDeletedObject** table that has exceeded the retention period. Records is deleted in batches until the timeout criteria is reached. By default the job runs every day at 1 AM. The recurrence and frequency of the job is configurable in **System Administration>Batch Jobs**. The retention period, delete batch size and timeout is configurable using **SysGlobalConfiguration settings**.

## Retrieve row version entity changes

For details for how to use the **RetrieveEntityChanges** API, see TBA
 
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
