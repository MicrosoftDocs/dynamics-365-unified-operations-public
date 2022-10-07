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

# Allow row version change tracking for tables and data entities
[!include[banner](../includes/banner.md)]

A new change tracking option has been added to finance and operations apps to enable incremental synchronization of data using Microsoft Dataverse. Change tracking is a prerequisite for several features such as Data archival, Synapse integration, Mobile offline and Relevance search. The goal is to over time unify all existing finance and operations data synchronization frameworks into one that is based on Dataverse synchronization services.

Before creating or updating data entities to use with row version change tracking, verify that all tables used as data sources for the entity allow row version change tracking.

To create a new entity, see [Build and consume data entities](/dev-itpro/data-entities/build-consuming-data-entities.md)

## Allow row version change tracking on tables

You can enable **Allow Row Version Change Tracking** on tables by setting its metadata property to **Yes**. All table(s) used as data source for a data entity, must have the property set to **Yes** to allow row version change tracking for the entity. A **SysRowVersionNumber** column, of data type **rowversion** is added to the table during build operations. 

The **SysRowVersionNumber** column performs version stamping of table rows. SQL server maintains a database level counter that is incremented for each insert or update operation. Changes to a table row can be detected by comparing the current value in **SysRowVersionNumber** with the previous value. 

> [!NOTE]
> The **SysRowVersionNumber** column, aka **rowversion** column, is read only in SQL. This means that direct SQL update statements will break if they try to create or update this column, e.g. statements similar to:
> ```SQL
> INSERT INTO table2
> SELECT * FROM table1
> ```

## Allow row version change tracking on data entities

You can enable **Allow Row Version Change Tracking** on data entities by setting their metadata properties to **Yes**. Not all existing data entities are configured to support row version change tracking, this is mainly due to the complexity of the entity. Validations rules are evaluated at build time when **Allow Row Version Change Tracking** is set to **Yes** for a data entity. It is still recommended you review and proactively apply these rules when creating or updating entities.

**Data entity validation rules**

| Rule | Comments | Error message |
|----------|--------|--------|
| Data entity with custom change tracking query isn't supported. |   | Change tracking can't be enabled because the F&O entity %1 uses a custom query. |
| Data entity with range filters isn't supported. | Range filters can cause records to be filtered out from the view. When this happens, the change won't be tracked as a delete. [![Data entity Ranges.](./dev-itpro/data-entities/media/DERanges.jpg)](./dev-itpro/data-entities/media/DERanges.jpg)|  Change tracking can't be enabled because the F&O entity %1 contains Ranges. |
| Data entity with data source(s) having group by condition isn't supported  | [![Data entity Group By.](./dev-itpro/data-entities/media/DataSourceGroupBy.jpg)](./dev-itpro/data-entities/media/DataSourceGroupBy.jpg) | Change tracking can't be enabled because the data source %1 in the F&O entity %2 contains group By conditions. |
| Count of data source(s) in a data entity must be below the threshold. | You will receive a warning when the threshold is exceeded by 10 and a warning when exceeded by 5. This is configurable up to a maximum of 10. This is limited to improve performance. | Change tracking can't be enabled because the F&O entity %1 contains more than %2 data sources. |
| Data entity with data source having range filters isn't supported. | [![Data Sources Ranges.](./dev-itpro/data-entities/media/DataSourceRangesjpg.jpg)](./dev-itpro/data-entities/media/DataSourceRangesjpg.jpg) | Change tracking can't be enabled because the data source %1 in the F&O entity %2 contains Ranges. |
| Data entity with non-table data source isn't supported. | Nested data entities or data entities containing a view(s) as a data source isn't supported. | Change tracking can't be enabled because the data source %2 in the F&O entity %1 isn't a table. |
| All tables in the data entity must allow row version change tracking. | [![Allow Row Version Change Tracking.](./dev-itpro/data-entities/media/AllowRowVersionChangeTracking.jpg)](./dev-itpro/data-entities/media/AllowRowVersionChangeTracking.jpg) | Change tracking can't be enabled because the **Allow Row Version Change Tracking** property isn't set to **Yes** for the table related to data source %2 for the F&O entity %1. |
| Data sources in the data entity must be joined using an outer join. | Inner join and exists join isn't supported. Non outer join can cause records to be filtered out of the view. When this happens, the change won't be tracked as a delete. [![Data Sources Join Mode.](./dev-itpro/data-entities/media/OuterJoinMode.jpg)](./dev-itpro/data-entities/media/OuterJoinMode.jpg) | Change tracking can't be enabled since the Join Mode between the data source %1 and the data source %2 in the F&O entity %3 isn't %4. | 
| The relationship between data sources must be many-to-one. | One-to-many relationship isn't supported. A one-to-many relationship will generate duplicate virtual table **entityids**. |  Change tracking can't be enabled because the Relation %1 between the data source %2 and the data source %3 in the F&O entity %4 is one-to-many. |
| Only normal relation constraint is supported for data sources in a data entity. | [![Data Sources Relation Constraints.](./dev-itpro/data-entities/media/DataSourceRelations.jpg)](./dev-itpro/data-entities/media/DataSourceRelations.jpgg) | Change tracking can't be enabled because the Relation %1 between the data source %2 and the data source %3 in the F&O entity %4 isn't set to Normal. |
| Rule to validate entities containing time state enabled tables. | A root table with **Apply Date** filter isn't supported because it can cause record disappearance. Time state tables are not supported for related data sources because it can cause either record disappearance or one-to-many relationships. |  Change tracking can't be enabled because the data source %3 in the F&O entity %1 has a time state enabled table %2. |

The **SysRowVersionNumber** column of the primary table is added to the data entity view when **Allow Row Version Change Tracking** is set to **Yes** for a data entity.

## Tracking delete and cleanup

Data entity row deletions are change tracked using the **AifChangeTrackingDeletedObject** table.

There's a system batch job **Delete tracking history clean-up** that cleans up records in the **AifChangeTrackingDeletedObject** table that has exceeded the retention period. Records are deleted in batches until the timeout criteria is reached. By default the job runs every day at 1 AM. The recurrence and frequency of the job is configurable in **System Administration>Batch Jobs**. The retention period is currently 10 days.

## Retrieve row version entity changes

This change tracking feature is fully compatible with the Dataverse change tracking, see [Use change tracking to synchronize data with external systems](../power-apps/developer/data-platform/use-change-tracking-synchronize-data-external-systems) There are some differences:

> [!NOTE]
> Changes for finance and operations will be returned if the last token is within a default value of 10 days instead of 90 days for Dataverse tables. 
 
[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
