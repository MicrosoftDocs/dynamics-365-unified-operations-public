---
title: Errors codes for the table map health check
description: Learn about error codes for the table map health check, including a table that provides messages and details associated with various error codes.
author: RamaKrishnamoorthy
ms.author: ramasri
ms.topic: article
ms.date: 05/31/2022
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: global
ms.search.validFrom: 2021-10-04
---

# Errors codes for the table map health check

[!include [banner](../../includes/banner.md)]



This article describes error codes for the table map health check.

| Error code | Message | Detail |
| --- | --- | --- |
| 100 | Minimum required finance and operations platform version is PU 43 to run finance and operations recommendations. | This feature requires platform updates for version 10.0.19 or later of finance and operations apps. |
| 400 | Minimum required finance and operations platform version is PU 43 to run finance and operations recommendations. | This feature requires platform updates for version 10.0.19 or later of finance and operations apps. |
| 500 | No project configurations found for project \{project name\}. This could be either the project isn't enabled or all the field mappings are unidirectional from customer engagement to finance and operations. | Check the mappings for the table map. If they're unidirectional from customer engagement apps to finance and operations apps, no traffic is generated for live synchronization from finance and operations apps to Microsoft Dataverse. |
| 900 | Invalid source filter \{sourceFilter\} format for entity \{finance and operations UniqueEntityName\}. | The source filter that's specified on the table map for finance and operations apps isn't syntactically correct. To validate the filter criteria, see [Troubleshoot live synchronization issues](dual-write-troubleshooting-live-sync.md#live-synchronization-issues-that-are-caused-by-incorrect-query-filter-syntax-on-the-dual-write-maps). | 
| 1000 | Entity \{finance and operations UniqueEntityName\} query used for dual-write live sync is \{finance and operations EntityFilterQueryString\}. Records that meet the query criteria are picked up for live sync. | The entity query that was returned is the backing SQL query for the entity. Check for inner joins or filters on the query that determine the business data that's being picked up for live synchronization. Inner joins and filters are mandatory conditions that must be fulfilled for each record that's being picked up for dual-write live synchronization. | 
| 1300 | Virtual fields \{s.EntityFieldName\} for entity \{finance and operations EntityMetadata.EntityProperties.LogicalEntityName\} may not be tracked for dual-write. | Virtual fields from finance and operations tables aren't enabled for tracking. Live synchronization can sync the data but can't pick up the changes that are made on the columns. | 
| 1500 | There should be at least one field mapped to a non lookup field on customer engagement to enable tracking on the data source \{datasource.DataSourceName\}. | The data source from the entity doesn't have any field that's mapped for dual-write. Changes to the underlying table aren't tracked for dual-write. |
| 1600 | Datasource: \{datasource.DataSourceName\} for entity \{finance and operations EntityMetadata.EntityProperties.LogicalEntityName\} has a range. Only records that satisfy the range condition are picked up for outbound. | <p>Entities in finance and operations apps can have data sources where filter ranges are enabled. These ranges define the records that are picked up as part of live synchronization. If some records are skipped from finance and operations apps to Dataverse, check whether the records meet the range criteria on the entity. A simple way to do this check is to run a SQL query that resembles the following example.</p><p><pre>```select * from <Entity> where <filter criteria>```</pre></p>| 
| 1700 | Table: \{datasourceTable.Key.subscribedTableName\} for entity \{datasourceTable.Key.entityName\} is tracked for entity \{origTableToEntityMaps.EntityName\}. Same tables tracked for multiple entities can impact system performance for live sync transactions. | If the same table is tracked by multiple entities, changes to the table trigger dual-write evaluation for the linked entities. Although the filter clauses send only the valid records, the evaluation might cause a performance issue if there are long-running queries or unoptimized query plans. This issue might not be avoidable from the business perspective. However, if there are many intersecting tables across multiple entities, you should consider simplifying the entity or checking optimizations for entity queries. |
| 1800 | Datasource: \{\} for entity CustCustomerV3Entity includes a range value. Inbound record upserts from Dataverse to finance and operations can be affected by range values on entity. Test record updates from Dataverse to finance and operations with records that don't match the filter criteria to validate your settings. | If there's a range specified on the entity in finance and operations apps, then the inbound sync from Dataverse to finance and operations apps should be tested for update behavior on records that don't match this range criteria. Any record that doesn't match the range gets treated as an insert operation by the entity. If there's an existing record in the underlying table, then the insert fails. We recommend that you test this use case for all scenarios before deploying to production. |
| 1900 | Entity: has \{\} data sources that aren't being tracked for outbound dual write. This can affect live sync query performance. Remodel the entity in finance and operations to remove unused data sources and tables or implement getEntityRecordIdsImpactedByTableChange to optimize the runtime queries. | If there are many data sources that aren't being used for tracking in the actual live sync from finance and operations apps, then there's a possibility that entity performance can affect live sync. To optimize the tracked tables, use the method getEntityRecordIdsImpactedByTableChange. | 
| 2000 | FnO Entity \{\} fields \{\} defined as Integration key attributes aren't configured as mandatory. | It's recommended that fields included as integration key attributes are required fields for data entry in the application, ensuring that a value is always entered in the field. When this error occurs, the recommended action is to configure the fields of the finance and operations table to be required to avoid initial sync and live sync issues. For more information on designating fields are required using the personalization feature, see [Personalize the user experience](../../../fin-ops/get-started/personalize-user-experience.md). | 
| 5000 | Synchronous plugins are registered for data management events for entity accounts. These can impact initial sync and live sync import performance into Dataverse. For best performance, change the plugins to asynchronous processing. List of registered plugins \{\}. | Synchronous plugins on a Dataverse entity can affect live synchronization and initial synchronization performance, because they add to the transaction load. If you experience slow load times during initial synchronization or live synchronization for a specific entity, either turn off the plugins or make them asynchronous. |
| 5100 | Integration Key \{IntegrationKeyDetails\} isn't defined as one of alternate keys in Dataverse for table \{EntityName\}. | To fix this error, align the indicated integration key with one of the alternate keys of the table to avoid initial synchronization and live synchronization issues. For more information about integration keys, including alignment with alternate keys, see [Manage dual-write integration keys](dual-write-integration-keys.md). | 
| 5200 | Dataverse Entity \{Entity Name\} fields \{Entity Fields\} defined as Integration key attributes aren't configured as mandatory. | It's recommended that fields included as integration key attributes are required fields for data entry in the application, ensuring that a value is always entered in the field. When this error occurs, the recommended action is to configure the fields of the Dataverse table to be required to avoid initial sync and live sync issues. For information on setting columns to be required in Dataverse, see [How to create columns using Power Apps portal](/power-apps/maker/data-platform/create-edit-field-portal). |



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

