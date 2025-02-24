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

# Introduction

The **Warehouse management** module has many pages that need to be set up for User-configurable queries. 
Some typical examples are: 
 - **Edit query** button in the **Work templates**
 - **Location directives** page
 - **Select products** button on the **Replenishment templates** page

The purpose of these queries is to limit the data being processed, either due to the business requirements or performance reasons. The exact behavior of the query, how are the results of the query are used, depends on the functional areas it's used in, but most follow the same basic structure and behavior. The logic is similar to regular SQL queries. 

Example forms:
**SysQueryForm**, **Wave template**, **Work templates**, **Location directives**, **Labor standards**, **Document routing**, **Wave label templates**, **Wave label layouts**, **Label layout data source**, **Container label routing**, **Wave filters**, **Mobile device menu items**, **Cluster profiles**, **Wave load building templates**, **Cross docking templates**, **Container build templates**, **Replenishment templates**, **Slotting templates**, **Outbound sorting template**, **Cycle count plans**, **Cycle counting threshold**, **Shipment consolidation policies**, and **Shipment consolidation templates**.

Example buttons:
**Edit query**, **Select items**, **Select locations**, **Select products**, **Select product variants**, **Select locations to replenish**, **Select zones to replenish**, **Define product query**, **Define product variant query**.

> [!IMPORTANT]
> The most common mistake in queries is adding table joins and expecting the functionality to apply only to the added records. For example, a sales table is joined to the **Location directive action** query. The **Location directive action** only applies when processing those sales orders that fulfill the user defined criteria.
> Filters are added only to the tables that are in the default query. If the user adds a join to sales orders, this record won't add a filter to the sales order being released.

## Basic query structure

### Ranges

Ranges are filters used to limit which records are returned from the query. They're explicitly applied to the individual table fields, and implicitly when join relations are used.

### Joins

Joins are applied between two tables to determine how the data between them is filtered and potentially combined. There can be multiple joins to the same table.

The queries in X++ support several different joins: *InnerJoin*, *OuterJoin*, *ExistsJoi*n, and *NoExistsJoin*. However, only *ExistsJoin* (the default value regardless of the join mode, like *1:n* or *n:1*) and *NoExistsJoin* (*NotExist*) are available in the User-configurable queries.

> [!NOTE]
> There are special cases where dedicated functionality was developed to support inner or outer joins in User-configurable queries, like in the **Label layout data** source page, but those aren't available.
> If the default query has those types of joins, the user can add ranges to them. Any new table joins added through the UI can only be exists or not exists joins.
> The user isn't able to see which type of join is used in the default query.

- The *InnerJoin* returns the combined records from both of the joined tables, so it's a subset of the two table records. The join is made based on the specified relations between the two tables.

- The *OuterJoin* returns the records from the first table, but the records that have a match in the other table will have those fields populated. The join is made based on the specified relations between the two tables.

- The *ExistsJoin* is similar to the *InnerJoin* with the difference that no record information from the second table is returned in the result.

- The *NoExistsJoin* is similar to the *ExistsJoin* as only records information from the first table are returned. In this case, the filtering is the opposite, if the match doesn't exist, then the record is returned. 

### Sorting

Sorting is applied after getting the results from the ranges and joins. It's only applicable to the returned records and fields. Having sorting on the second table in an *ExistsJoin* isn't applicable.

> [!IMPORTANT]
> Adding additional ranges, sorting and especially table joins will have a negative performance impact. In some cases, ranges and joins must be added to fulfill the business requirements, the user shouldn't create queries that are too complex.

## Examples

### Work templates page

In this page, each of the different **Work order types** has a slightly different default query. The purpose of the query is to select the work template to be used to create warehouse work and remaining work lines from the initial **Temporary work transactions** during wave processing. The **Temporary work transactions** are initialized from the order lines and headers.

If we use Sales orders as an example, the top table is **Temporary work transactions**. There are two tables joined to it, **Order lines** and **Locations**. It's not possible to see the join type from the UI, only from the development environment. In this case, both are inner joins. There are a few more joins with the **Order lines** table. **Locations** doesn’t have any more joins. **Order lines** is joined to the **Sales orders** table (inner join, and **Sales orders** table has no further joins) and the **Items** table (inner join, and the **Items** table has more joins). **Items** is joined to the **Warehouse item number** table (inner join, and **Warehouse item number** table has no further joins). There aren't default ranges added to the query.

Users can add ranges to any of the above mentioned tables. Only those records that fulfill all of those conditions can use this work template during wave processing.

For example, if the user selects the **Warehouse item number** table and sets **Field** to **Code 1**, and **Criteria** to **A**. It means that only those items that have **Product filter code** **Code 1** set to **A** can use this work template.

Let's say the user now adds a relation to the **Carrier (Shipping carrier)** table to the **Temporary work transactions** table. This would be an exists type of join. The user can now add a **Range** on that table, for example on the **Carrier** table and **Shipping carrier** field with some carrier name in the **Criteria** field. This work template applies only to those temporary work transactions which has that specific carrier name set.

> [!NOTE]
> There are many tables listed as available for being joined. It doesn't mean that the related fields are populated in all the cases, which might lead to unexpected results.

### Location directives page
In this page, there are two different User-configurable queries, the one related to the **Location directive** (header), and the other related to the **Location directive actions**. The action query has different default values depending on **Work type** or if **Batch enabled** is selected. The purpose of this query is to find a suitable warehouse location for the work line to pick from or put to.

If we use a **Sales orders** **Pick** without **Batch enabled**, the top table is *Locations*. There's one table joined to it **On-hand inventory** (inner join). There are already ranges predefined. **Warehouse**, **Physical inventory** and **No open quantities** have **Criteria** set, and aren't editable, while **Location** and **Item number** are present, but have no values in the **Criteria** and are editable.

> [!NOTE]
> In older versions, there might be a third table (*Inventory dimensions*) in between *Locations* and *On-hand inventory*.

The user can specify the desired ranges **Location profile ID** on the **Locations** table. In that case, only those locations that match the **Criteria** are evaluated when trying to find a valid location to pick the item from.

If the user adds a sorting, for example, table **Locations**, **Location** field, search direction **Ascending**. The locations are evaluated based on the order of their location IDs. For example, a location with the **Location123** ID is evaluated before **Location321**.

> [!NOTE]
> In some cases, there are additional ranges or tables applied during the processing, not visible to the user. In the example above, the item is always be applied for the pick location directive action, as the on-hand inventory is picked for a specific item.

The user now adds a relation to the **Order lines (Item number)** table to the **On-hand inventory** table. This would be an exists type of join. The user can add a **Range** on that table. For example, on the **Order lines** table and the **Customer** field with some **Customer account** in the **Criteria** field.

> [!IMPORTANT]
> The user might think that the above query only applies when processing sales orders for that given **Customer account**. However, that's not what happens. The meaning of the query is: find a location that has an item for which there's a sales line for **Customer1**. If the given item was ever added to a sales line for **Customer1**, this additional table join and range doesn't have a functional effect, and adds performance overhead.
