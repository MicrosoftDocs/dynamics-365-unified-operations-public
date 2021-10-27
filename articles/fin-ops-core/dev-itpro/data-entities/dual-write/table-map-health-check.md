---
title: Errors codes for the table map health check
description: This topic describes error codes for the table map health check.
author: nhelgren
ms.date: 10/04/2021
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: rhaertle
ms.search.region: global
ms.author: nhelgren
ms.search.validFrom: 2021-10-04
---

# Errors codes for the table map health check

[!include [banner](../../includes/banner.md)]

[!include [rename-banner](~/includes/cc-data-platform-banner.md)]

This topic describes error codes for the table map health check.

## Error 100

The error is *Minimum required Finance and Operations platform version is PU 43 to run Finance and Operations recommendations.*

This feature requires platform updates for version 10.0.19 or later of Finance and Operations apps.

## Error 400

The error is *No business events registration data found for the entity {Finance and Operations UniqueEntityName} which means either the map is not running or all the field mapping are unidirectional.*

## Error 500

The error is *No project configurations found for project {project name}. This could be either the project is not enabled or all the field mappings are unidirectional from customer engagement to Finance and Operations.*

Check the mappings for the table map. If they are unidirectional from customer engagement to Finance and Operations, then no traffic is generated for live sync from Finance and Operations to Dataverse.

## Error 900

The error is *Invalid source filter {sourceFilter} format for entity {Finance and Operations UniqueEntityName}.*

The source filter specified on table map for Finance and Operations is not syntactically correct. To validate the filter criteria, see [Troubleshoot live synchronization issues](dual-write-troubleshooting-live-sync.ms#live-synchronization-issues-that-are-caused-by-incorrect-query-filter-syntax-on-the-dual-write-maps).

## Error 1000

The error is *Entity {Finance and Operations UniqueEntityName} query used for dual-write live sync is {Finance and Operations EntityFilterQueryString}. Records which meet the query criteria will be picked up for live sync.*

The entity query returned is the backing SQL query for the entity. Check for inner joins or filters on the query which might impact the business data being picked up for live sync. Inner joins and filters are mandatory conditions that needs to be fulfilled for each record being picked up for dual-write live sync.

## Error 1300

The error is *Virtual fields {s.EntityFieldName} for entity {Finance and Operations EntityMetadata.EntityProperties.LogicalEntityName} may not be tracked for dual-write.*

Virtual fields from Finance and Operations tables are not enabled for tracking. The live sync can synchronize the data but it won't be able to pick up the changes made on these columns.

## Error 1500

The error is *There should be at least one field mapped to a non lookup field on customer engagement to enable tracking on the data source {datasource.DataSourceName}.*

The data source from the entity does not have any field mapped for dual-write. Any modifications done on the underlying table will not be tracked for dual-write.

## Error 1600

The error is *Datasource : {datasource.DataSourceName} for entity {Finance and Operations EntityMetadata.EntityProperties.LogicalEntityName} has a range. Only records that satisfy the range condition are picked up for outbound.*

Entities in Finance and Operations apps can have data sources that have filter ranges enabled. These ranges define the records picked up as part of live sync. If some records are skipped from Finance and Operations to Dataverse, check if the records meet the range criteria on the entity. A simple way to check is to run a SQL query like this:

```sql
select * from <EntityName> where <filter criteria for the records> on SQL.
```

## Error 1700

The error is *Table : {datasourceTable.Key.subscribedTableName} for entity {datasourceTable.Key.entityName} is tracked for entity {origTableToEntityMaps.EntityName}. Same tables tracked for multiple entities can impact system performance for live sync transactions.*

If the same table is tracked by multiple entities then any modification on the table will trigger dual-write evaluation for the linked entities. The filter clauses would only send the valid records, but the evaluation might cause a performance issue if there are long running queries or unoptimized query plans. This problem may not be avoidable from the business point of view but if there are lot of intersecting tables across multiple entities, consider simplifying the entity or checking optimizations for entity queries.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
