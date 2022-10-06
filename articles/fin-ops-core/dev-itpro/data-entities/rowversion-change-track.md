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

# Allow Row version change tracking for tables and data entities
[!include[banner](../includes/banner.md)]

A new change tracking option has been added to finance and operations to enable incremental synchronization of data using the Dataverse. The new change tracking is a prerequisute for several features such as Data archival, Synapse integration, Mobile offline and Relevance search. The goal is to over time unify all existing Finance and Operations data synchronization frameworks into one that is based on Dataverse synchronization services

Before creating or updating Data entities that can be used for the new row version change tracking, it is required to validate that all tables used as data source for the entity allows row version change tracking.

To create a new entity, see [Build and consume data entities](/dev-tools/design-best-practices.md)

## Allow Row version change tracking on tables

A new metadata property, **Allow Row Version Change Tracking**, of type **No/Yes** has been added. All table(s) used as data source for a data entity, must have the property set to **Yes** to allow row version change tracking for the entity. 

The **SQL row version** column performs version stamping of table rows. SQL server maintains a database level counter that is incremented for each insert or update operation. Every time a row with a row version column is modified or inserted, the incremented database row version counter is inserted in the row version column. Changes to a table row can be detected by comparing the current value in row version column with the previous value. 

> [!NOTE]
> The SQL row version column is read only in SQL. This means that direct SQL update statements will break if they try to create or update this column, e.g. statements similar to:
```SQL
INSERT INTO table2
SELECT * FROM table1
```

## Allow Row version change tracking on data entities

A new metadata property **Allow Row Version Change Tracking** of type **No/Yes** has been added to the Data entity. Not all existing data entities are configured to support Row version change tracking, this is mainly due to the complexity of the entity. Validations rules are evaluated at build time when **Allow Row Version Change Tracking** is set to **Yes**. It is recommended to be aware about these rules when creating or updating entities.     

**Data entity validation rules**

| Rule | Comments | Error message |
|----------|--------|--------|
| Data entity with custom change tracking query is not supported. |   | Change tracking cannot be enabled since F&O entity %1 uses a custom query. |
| Data entity with range filters is not supported. | Range filters can cause records to get filtered out from the view which will not be change tracked as delete. [![Data entity Ranges.](./media/DERanges.jpg)](./media/DERanges.jpg)|  Change tracking cannot be enabled since the F&O entity %1 contains Ranges. |
| Data entity with data source(s) having group by condition is not supported  | [![Data entity Group By.](./media/DataSourceGroupBy.jpg)](./media/DataSourceGroupBy.jpg) | Change tracking cannot be enabled since the data source %1 in the F&O entity %2 contains  Group By conditions. |
| Count of data source(s) in a data entity must be below threshold. | Error when exceeding 10 and warning if more than 5. Configurable up to 10. This limitation is from performance standpoint. | Change tracking cannot be enabled since the F&O entity %1 contains more than %2 data sources. |
| Data entity with data source having range filters is not supported. | [![Data Sources Ranges.](./media/DataSourceRanges.jpg)](./media/DataSourceRanges.jpg) | Change tracking cannot be enabled since the data source %1 in the F&O entity %2 contains Ranges. |
| Data entity with non-table data source is not supported. | Nested data entities or data entities containing view(s) as data source is not supported. | Change tracking cannot be enabled since the data source %2 in the F&O entity %1 is not a table. |
| All tables in the data entity must allow row version change tracking. | [![Allow Row Version Change Tracking.](./media/AllowRowVersionChangeTracking.jpg)](./media/AllowRowVersionChangeTracking.jpg) | Change tracking cannot be enabled since the Allow Row Version Change T racking property is not set to Yes for the table related to data source %2 for the F&O entity %1. |
| Data sources in the data entity must be joined using an outer join. | Inner join and exists join is not supported. Non outer join can cause records to get filtered out from the view which will not be change tracked as delete. [![Data Sources Join Mode.](./media/OuterJoinMode.jpg)](./media/OuterJoinMode.jpg) | Change tracking cannot be enabled since the Join Mode between the data source %1 and the data source %2 in the F&O entity %3 is not %4. | 
| Relationship between data sources must be many-to-one. | One-to-many relationship is not supported. One-to-many  relationship will generate duplicate Virtual table **entityids**. |  Change tracking cannot be enabled since the Relation %1 between the data source %2 and the data source %3 in the F&O entity %4 is one-to-many. |
| Only normal relation constraint is supported for data sources in a data entity. | [![Data Sources Relation Constraints.](./media/DataSourceRelations.jpg)](./media/DataSourceRelations.jpg) | Change tracking cannot be enabled   since the Relation %1 between the data source %2 and the data source %3 in the F&O entity %4 is not set to Normal. |
| Rule to validate entities containing time state enabled tables. | Root table with **Apply Date** filter is not supported, it can cause record disappearance. Time state tables not supported for related data sources since it can cause either record disappearance or one-to-many relationships. |  Change tracking cannot be enabled since the data source %3 in the F&O entity %1 has a time state enabled table %2. |

The **SysRowVersionNumber** column of the primary table is added to the data entity view when **Allow Row Version Change Tracking** is set to **Yes** for a data entity.

## Tracking delete and cleanup

Data entity row deletions are change tracked using the **AifChangeTrackingDeletedObject** table.

There is a system batch job **Delete tracking history clean-up** that cleans up records in the **AifChangeTrackingDeletedObject** table that has exceeded the retention period. Records is deleted in batches until the timeout criteria is reached. By default the job runs every day at 1 AM. The recurrence and frequency of the job is configurable in **System Administration>Batch Jobs**. The retention period is currently 10 days.

## Retrieve row version entity changes

This new finance and operations change tracking feature in fully compatible with the Dataverse change tracking, see [Use change tracking to synchronize data with external systems](../power-apps/developer/data-platform/use-change-tracking-synchronize-data-external-systems) There are some differences:

- Changes for finance and operations will be returned if the last token is within a default value of 10 days instead of 90 days for Dataverse tables. 
 
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
