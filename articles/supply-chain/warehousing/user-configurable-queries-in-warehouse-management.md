---
title: User-configurable queries in warehouse management
description: Learn how user-configurable queries are used in warehouse management.
author: ivanma
ms.author: ivanma
ms.topic: article
ms.date: 02/18/2025
ms.reviewer: kamaybac
ms.search.form: SysQueryForm, WHSWaveTemplateTable, WHSWorkTemplateTable, WHSLocDirTable, WHSLaborStandards, WHSDocumentRouting, WHSWaveLabelTemplate, WHSWaveLabelLayout, WHSLabelLayoutDataSource, WHSContainerLabelRouting, WHSWaveFilterTable, WHSRFMenuItem, WHSClusterProfile, WHSLoadBuildTemplate, WHSCrossDockingTemplate, WHSContainerizationTable, WHSReplenishmentTemplates, WHSSlotTemplate, WHSOutboundSortTemplate, WHSCycleCountPlan, WHSCycleCountThreshold, WHSShipConsolidationPolicy, WHSShipConsolidationTemplate
---

# User-configurable queries in warehouse management

The purpose of user-configurable queries is to limit the data that is processed. You might want to limit this data either because of business requirements or for performance reasons. The exact behavior of a query and the way that the results are used depend on the functional areas where that query is used. However, most user-configurable queries have the same basic structure and behavior. The logic resembles the logic of regular SQL queries.

Many places in the **Warehouse management** module must be set up for user-configurable queries. Here are some typical examples:

- The **Edit query** button on the **Work templates** page
- The **Location directives** page
- The **Select products** button on the **Replenishment templates** page

Here are some more examples of pages:

- SysQueryForm
- Wave template
- Work templates
- Location directives
- Labor standards
- Document routing
- Wave label templates
- Wave label layouts
- Label layout data source
- Container label routing
- Wave filters
- Mobile device menu items
- Cluster profiles
- Wave load building templates
- Cross docking templates
- Container build templates
- Replenishment templates
- Slotting templates
- Outbound sorting template
- Cycle count plans
- Cycle counting threshold
- Shipment consolidation policies
- Shipment consolidation templates

Here are some more examples of buttons:

- Edit query
- Select items
- Select locations
- Select products
- Select product variants
- Select locations to replenish
- Select zones to replenish
- Define product query
- Define product variant query

> [!IMPORTANT]
> The most common mistake that users make in queries is to add table joins and expect the functionality to apply only to the added records. For example, the user adds a join to a sales table in the *Location directive action* query. The *Location directive action* query applies only when sales orders that meet the user-defined criteria are processed.
>
> Filters are added only to the tables that are in the default query. If the user adds a join to sales orders, the record doesn't add a filter to the sales order that is being released.

## Basic query structure

### Ranges

Ranges are filters that are used to limit which records are returned from the query. They are explicitly applied to individual table fields. In addition, they are implicitly applied when join relations are used.

### Joins

Joins are applied between two tables to define how the data between them is filtered and potentially combined. There can be multiple joins to the same table.

The queries in X++ support several types of joins: *InnerJoin*, *OuterJoin*, *ExistsJoin*, and *NoExistsJoin* (*NotExist*). However, only *ExistsJoin* and *NoExistsJoin* are available in user-configurable queries. *ExistsJoin* is the default join type, regardless of the join mode (for example, *1:n* or *n:1*).

> [!NOTE]
> In some special cases (for example, on the **Label layout data source** page), dedicated functionality was developed to support inner or outer joins in user-configurable queries, but those joins aren't available. If the default query has those types of joins, the user can add ranges to them. New table joins that are added through the user interface (UI) can be joins of the *ExistsJoin* or *NoExistsJoin* type only. Users can't view which type of join is used in the default query.

- *InnerJoin* returns the combined records from both joined tables. Therefore, it's a subset of the two table records. The join is made based on the specified relations between the two tables.
- *OuterJoin* returns the records from the first table, but any records that have a match in the other table will have those fields populated. The join is made based on the specified relations between the two tables.
- *ExistsJoin* resembles *InnerJoin*, but no record information from the second table is returned in the result.
- *NoExistsJoin* resembles *ExistsJoin* in that only record information from the first table is returned. However, the filtering is the opposite. Therefore, the record is returned if the match does **not** exist.

### Sorting

Sorting is applied after the results are returned from the ranges and joins. It's applicable only to the returned records and fields. Sorting can't be applied to the second table in a join of the *ExistsJoin* type.

> [!IMPORTANT]
> The addition of further ranges, sorting, and especially table joins negatively affects performance. In some cases, ranges and joins must be added to meet business requirements. However, users should not create queries that are too complex.

## Examples

### Work templates page

On the **Work templates** page, each work order type has a slightly different default query. The purpose of the query is to select the work template that is used to create warehouse work and remaining work lines from the initial temporary work transactions during wave processing. The temporary work transactions are initialized from the order lines and headers.

In the case of sales orders, for example, the top table is `Temporary work transactions`. Two tables are joined to it, `Order lines` and `Locations`. You can't view the join type from the UI. You can view it only from the development environment. In this case, both joins are inner joins. The `Locations` table has no further joins. However, the `Order lines` table has one inner join to the `Sales orders` table and another inner join to the `Items` table. The `Sales orders` table has no further joins. However, the `Items` table has an inner join to the `Warehouse item number` table. The `Warehouse item number` table has no further joins. No default ranges are added to the query.

Users can add ranges to any of the previously mentioned tables. Only records that meet all the conditions can use this work template during wave processing.

For example, the user selects the `Warehouse item number` table and sets the **Field** field to *Code 1* and the **Criteria** field to *A*. In this case, only items where product filter code *Code 1* is set to *A* can use this work template.

Next, the user adds a relation to the `Carrier (Shipping carrier)` table to the `Temporary work transactions` table. The join is an *ExistsJoin* join. The user can now add a range on that table. For example, the user adds a range on the `Carrier` table and the **Shipping carrier** field, and specifies the name of some carrier in the **Criteria** field. In this case, the work template applies only to temporary work transactions where the specified carrier name is set.

> [!NOTE]
> Although many tables are listed as available for joins, the related fields aren't populated in all cases. This behavior might lead to unexpected results.

### Location directives page

On the **Location directives** page, there are two different user-configurable queries. One is related to the location directive (header), and the other is related to the location directive actions. The action-related query has different default values, depending on the work type or the setting of the **Batch enabled** checkbox. The purpose of this query is to find a suitable warehouse location for the work line to pick from or put to.

If you use a sales order pick action where the **Batch enabled** checkbox is cleared, the top table is `Locations`. One table is joined to it, `On-hand inventory`. The join is an inner join. Ranges are predefined. The **Warehouse**, **Physical inventory**, and **No open quantities** fields have values set in the **Criteria** field and aren't editable. The **Location** and **Item number** fields are present, but they have no value in the **Criteria** field and are editable.

> [!NOTE]
> In older versions, there might be a third table (`Inventory dimensions`) between `Locations` and `On-hand inventory`.

The user can specify the desired **Location profile ID** ranges on the `Locations` table. In this case, only locations that match the criteria are evaluated when the query tries to find a valid location to pick the item from.

The user might also add sorting, such a sort on the **Location** field of the `Locations` table in the *Ascending* search direction. In this case, the locations are evaluated based on the order of their location IDs. For example, the location that has the ID *Location123* is evaluated before the location that has the ID *Location321*.

> [!NOTE]
> In some cases, additional ranges or tables are applied during processing but aren't visible to the user. In the preceding example, the item is always applied for the pick location directive action, because on-hand inventory is picked for a specific item.

Next, the user adds a relation to the `Order lines (Item number)` table to the `On-hand inventory` table. The join is an *ExistsJoin* join. The user can now add a range on that table. For example, the user adds a range on the `Order lines` table and the **Customer** field, and specifies some customer account in the **Criteria** field.

> [!IMPORTANT]
> You might think that the preceding query applies only when sales orders are processed for the specified customer account. However, the query actually has the following meaning: *find a location that has an item for which there is a sales line for the specified customer account*. If the item was ever added to a sales line for that customer account, the additional table join and range have no functional effect. However, they add performance overhead.
