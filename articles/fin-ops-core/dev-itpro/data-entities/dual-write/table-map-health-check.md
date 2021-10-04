---
title: Errors codes for table map health check
description: This topic describes how to use the Microsoft Dynamics 365 Commerce pricing engine to create sales quotations in Dynamics 365 Sales.
author: 
ms.date: 11/19/2020
ms.topic: article
audience: Application User, IT Pro
ms.reviewer: v-chgri
ms.search.region: global
ms.author: shajain
ms.search.validFrom: 2020-01-06
---

# Errors codes for table map health check

[!include [banner](../../includes/banner.md)]

100 (Minimum required FnO platform version is PU 43 to run FnO recommendations)
This feature required FnO platform to be on PU 43 and above.

400 (No business events registration data found for the entity {fnoUniqueEntityName} which means either the map is not running or all the field mapping are unidirectional)
500 No project configurations found for project {project.Name }. This could be either the project is not enabled or all the field mappings are unidirectional from CE -> FO
Check the mappings for the table map . If they are unidirectional from CE to FnO then there will not be any traffic generated for live sync from FnO -> Dataverse

900 Invalid source filter {sourceFilter} format for entity {fnoUniqueEntityName}.
The source filter specified on table map for FnO is not syntactically correct. Use TSG to validate the filter criteria.

1000 Entity {fnoUniqueEntityName} query used for Dual write live sync is {fnoEntityFilterQueryString}. Records which meet the query criteria will be picked up for live sync.
The entity query returned is the backing SQL query for the entity. Please check for inner joins or filters on the query which can potentially impact the business data being picked up for live sync. Inner Joins and filters are mandatory conditions that needs to be fulfilled for each records being picked up for Dual-write live sync.

1300 Virtual fields {s.EntityFieldName} for entity {fnoEntityMetadata.EntityProperties.LogicalEntityName} may not be tracked for dual write.
Virtual fields from FnO are not enabled for tracking. The live sync can synchronize the data but it wont be able to pick up the changes made on such columns.

1500 There should be at least one field mapped to a non lookup field on CE to enable tracking on the data source {datasource.DataSourceName}
The data source from the entity does not have any field mapped for Dual write. Any modifications done on the underlying table will not be tracked for Dual write.

1600 Datasource : {datasource.DataSourceName} for entity {fnoEntityMetadata.EntityProperties.LogicalEntityName} has a range. only records that satisfy the range condition are picked up for outbound
Entities in FnO can have datasources which have filter ranges enabled. These ranges define the records picked up as part of live sync. If there are some records that are getting skipped from FnO to CE please check if the records meet the range criteria on the entity. A simple way to check is to run a select * from <EntityName> where <Provide Appropriate filter criteria for the records in question> on SQL.

1700 Table : {datasourceTable.Key.subscribedTableName} for entity {datasourceTable.Key.entityName} is tracked for entity {origTableToEntityMaps.EntityName}. Same table tracked for multiple entities can impact system performance for live sync transactions.
If same table is tracked by multiple entities then any modification on the table will trigger DW evaluation for the linked entities. Although the filter clauses would only send the valid records the evaluation can potentially lead to performance issue if there are long running query or unoptimized query plans. This may not be avoidable from the business point of view but if there are lot of intersecting tables across multiple entities consider simplifying the entity or checking optimizations for entity queries.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
