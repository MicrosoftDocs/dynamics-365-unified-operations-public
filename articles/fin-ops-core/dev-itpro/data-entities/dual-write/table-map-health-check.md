---
title: Errors codes for the table map health check
description: This article describes error codes for the table map health check.
author: RamaKrishnamoorthy
ms.date: 05/31/2022
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: sericks
ms.search.region: global
ms.author: ramasri
ms.search.validFrom: 2021-10-04
---

# Errors codes for the table map health check

[!include [banner](../../includes/banner.md)]



This article describes error codes for the table map health check.

## Error 100

The error message is, "Minimum required finance and operations platform version is PU 43 to run finance and operations recommendations."

The feature requires platform updates for version 10.0.19 or later of finance and operations apps.

## Error 400

The error message is, "No business events registration data found for the entity \{finance and operations UniqueEntityName\} which means either the map isn't running or all the field mapping are unidirectional."

## Error 500

The error message is, "No project configurations found for project \{project name\}. This could be either the project isn't enabled or all the field mappings are unidirectional from customer engagement to finance and operations."

Check the mappings for the table map. If they're unidirectional from customer engagement apps to finance and operations apps, no traffic is generated for live synchronization from finance and operations apps to Dataverse.

## Error 900

The error message is, "Invalid source filter \{sourceFilter\} format for entity \{finance and operations UniqueEntityName\}."

The source filter that is specified on the table map for finance and operations apps isn't syntactically correct. To validate the filter criteria, see [Troubleshoot live synchronization issues](dual-write-troubleshooting-live-sync.md#live-synchronization-issues-that-are-caused-by-incorrect-query-filter-syntax-on-the-dual-write-maps).

## Error 1000

The error message is, "Entity \{finance and operations UniqueEntityName\} query used for dual-write live sync is \{finance and operations EntityFilterQueryString\}. Records which meet the query criteria will be picked up for live sync."

The entity query that was returned is the backing SQL query for the entity. Check for inner joins or filters on the query that determine the business data that is being picked up for live synchronization. Inner joins and filters are mandatory conditions that must be fulfilled for each record that is being picked up for dual-write live synchronization.

## Error 1300

The error message is, "Virtual fields \{s.EntityFieldName\} for entity \{finance and operations EntityMetadata.EntityProperties.LogicalEntityName\} may not be tracked for dual-write."

Virtual fields from finance and operations tables aren't enabled for tracking. Live synchronization can sync the data, but it won't be able to pick up the changes that are made on the columns.

## Error 1500

The error message is, "There should be at least one field mapped to a non lookup field on customer engagement to enable tracking on the data source \{datasource.DataSourceName\}."

The data source from the entity doesn't have any field that is mapped for dual-write. Changes to the underlying table won't be tracked for dual-write.

## Error 1600

The error message is, "Datasource: \{datasource.DataSourceName\} for entity \{finance and operations EntityMetadata.EntityProperties.LogicalEntityName\} has a range. Only records that satisfy the range condition are picked up for outbound."

Entities in finance and operations apps can have data sources where filter ranges are enabled. These ranges define the records that are picked up as part of live synchronization. If some records are skipped from finance and operations apps to Dataverse, check whether the records meet the range criteria on the entity. A simple way to do this check is to run a SQL query that resembles the following example.

```sql
select * from <EntityName> where <filter criteria for the records> on SQL.
```

## Error 1700

The error message is, "Table: \{datasourceTable.Key.subscribedTableName\} for entity \{datasourceTable.Key.entityName\} is tracked for entity \{origTableToEntityMaps.EntityName\}. Same tables tracked for multiple entities can impact system performance for live sync transactions."

If the same table is tracked by multiple entities, any change to the table will trigger dual-write evaluation for the linked entities. Although the filter clauses will send only the valid records, the evaluation might cause a performance issue if there are long-running queries or unoptimized query plans. This issue might not be avoidable from the business perspective. However, if there are many intersecting tables across multiple entities, you should consider simplifying the entity or checking optimizations for entity queries.

## Error 1800
The error message is, "Datasource : {} for entity CustCustomerV3Entity includes a range value. Inbound record upserts from Dataverse to finance and operations can be affected by range values on entity. Please test record updates from Dataverse to finance and operations with records that don't match the filter criteria to validate your settings."

If there's a range specified on the entity in finance and operations apps, then the inbound sync from Dataverse to finance and operations apps should be tested for update behavior on records that don't match this range criteria. Any record that doesn't match the range gets treated as an insert operation by the entity. If there's an existing record in the underlying table, then the insert will fail. We recommend that you test this use case for all scenarios before deploying to production.

## Error 1900
The error message is, "Entity: has {} data sources which aren't being tracked for outbound dual write. This can affect live sync query performance. Please remodel the entity in finance and operations to remove unused data sources and tables or implement getEntityRecordIdsImpactedByTableChange to optimize the runtime queries."

If there are many data sources which aren't being used for tracking in the actual live sync from finance and operations apps, then there's a possibility that entity performance can affect live sync. To optimize the tracked tables, use the method getEntityRecordIdsImpactedByTableChange.

## Error 2000
The error message is, "FnO Entity {} fields {} defined as Integration key attributes are not configured as mandatory."

It's recommended that fields included as integration key attributes are required fields for data entry in the application, ensuring that a value is always entered in the field. When this error occurs, the recommended action is to configure the fields to be required to avoid initial sync and live sync issues. See [Personalize the user experience](../../fin-ops/get-started/personalize-user-experience.md) for more information on designating fields are required using the personalization feature.

## Error 5000
The error message is, "Synchronous plugins are registered for data management events for entity accounts. These can impact initial sync and live sync import performance into Dataverse. For best performance, please change the plugins to asynchronous processing. List of registered plugins {}."

Synchronous plugins on a Dataverse entity can affect live sync and intial sync performance as it adds to the transaction load. The recommended approach is to either turn off the plugins or make these plugins async if you are facing slow load times in initial sync or live sync for a particular entity.

## Error 5100
The error message is, "Integration Key {IntegrationKeyDetails] is not defined as one of alternate keys in Dataverse for table {EntityName}."



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

