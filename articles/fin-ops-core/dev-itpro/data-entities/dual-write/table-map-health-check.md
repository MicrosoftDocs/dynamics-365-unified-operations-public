---
title: Errors codes for the table map health check
description: This topic describes error codes for the table map health check.
author: nhelgren
ms.date: 10/04/2021
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: tfehr
ms.search.region: global
ms.author: nhelgren
ms.search.validFrom: 2021-10-04
---

# Errors codes for the table map health check

[!include [banner](../../includes/banner.md)]



This topic describes error codes for the table map health check.

## Error 100

The error message is, "Minimum required Finance and Operations platform version is PU 43 to run Finance and Operations recommendations."

The feature requires platform updates for version 10.0.19 or later of Finance and Operations apps.

## Error 400

The error message is, "No business events registration data found for the entity \{Finance and Operations UniqueEntityName\} which means either the map is not running or all the field mapping are unidirectional."

## Error 500

The error message is, "No project configurations found for project \{project name\}. This could be either the project is not enabled or all the field mappings are unidirectional from customer engagement to Finance and Operations."

Check the mappings for the table map. If they are unidirectional from customer engagement apps to Finance and Operations apps, no traffic is generated for live synchronization from Finance and Operations apps to Dataverse.

## Error 900

The error message is, "Invalid source filter \{sourceFilter\} format for entity \{Finance and Operations UniqueEntityName\}."

The source filter that is specified on the table map for Finance and Operations apps isn't syntactically correct. To validate the filter criteria, see [Troubleshoot live synchronization issues](dual-write-troubleshooting-live-sync.md#live-synchronization-issues-that-are-caused-by-incorrect-query-filter-syntax-on-the-dual-write-maps).

## Error 1000

The error message is, "Entity \{Finance and Operations UniqueEntityName\} query used for dual-write live sync is \{Finance and Operations EntityFilterQueryString\}. Records which meet the query criteria will be picked up for live sync."

The entity query that was returned is the backing SQL query for the entity. Check for inner joins or filters on the query that determine the business data that is being picked up for live synchronization. Inner joins and filters are mandatory conditions that must be fulfilled for each record that is being picked up for dual-write live synchronization.

## Error 1300

The error message is, "Virtual fields \{s.EntityFieldName\} for entity \{Finance and Operations EntityMetadata.EntityProperties.LogicalEntityName\} may not be tracked for dual-write."

Virtual fields from Finance and Operations tables aren't enabled for tracking. Live synchronization can sync the data, but it won't be able to pick up the changes that are made on the columns.

## Error 1500

The error message is, "There should be at least one field mapped to a non lookup field on customer engagement to enable tracking on the data source \{datasource.DataSourceName\}."

The data source from the entity doesn't have any field that is mapped for dual-write. Changes to the underlying table won't be tracked for dual-write.

## Error 1600

The error message is, "Datasource: \{datasource.DataSourceName\} for entity \{Finance and Operations EntityMetadata.EntityProperties.LogicalEntityName\} has a range. Only records that satisfy the range condition are picked up for outbound."

Entities in Finance and Operations apps can have data sources where filter ranges are enabled. These ranges define the records that are picked up as part of live synchronization. If some records are skipped from Finance and Operations apps to Dataverse, check whether the records meet the range criteria on the entity. A simple way to do this check is to run a SQL query that resembles the following example.

```sql
select * from <EntityName> where <filter criteria for the records> on SQL.
```

## Error 1700

The error message is, "Table: \{datasourceTable.Key.subscribedTableName\} for entity \{datasourceTable.Key.entityName\} is tracked for entity \{origTableToEntityMaps.EntityName\}. Same tables tracked for multiple entities can impact system performance for live sync transactions."

If the same table is tracked by multiple entities, any change to the table will trigger dual-write evaluation for the linked entities. Although the filter clauses will send only the valid records, the evaluation might cause a performance issue if there are long-running queries or unoptimized query plans. This issue might not be avoidable from the business perspective. However, if there are many intersecting tables across multiple entities, you should consider simplifying the entity or checking optimizations for entity queries.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
