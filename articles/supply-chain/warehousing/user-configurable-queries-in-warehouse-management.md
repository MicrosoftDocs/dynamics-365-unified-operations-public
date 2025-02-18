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

The Warehouse management module has many setup forms on which a part of the setup is done in the User-configurable queries. Typical examples would be the **Edit query** button in the **Work templates** or **Location directives** forms and **Select products** button in the **Replenishment templates** form. The purpose of these queries is to limit the data being processed, either due to the business requirements or in some cases for performance reasons. The exact behavior of the query (i.e. how are the results of the query used) depends on the functional areas it is used in, but most follow the same basic structure and behavior.The logic behind them is similar to regular SQL queries, so having knowledge about them is very helpful, and we won't be going into great many details how exactly each of the components work. Instead, we'll show the basic overview of the functionality.

Example forms:
**SysQueryForm**, **Wave template**, **Work templates**, **Location directives**, **Labor standards**, **Document routing**, **Wave label templates**, **Wave label layouts**, **Label layout data source**, **Container label routing**, **Wave filters**, **Mobile device menu items**, **Cluster profiles**, **Wave load building templates**, **Cross docking templates**, **Container build templates**, **Replenishment templates**, **Slotting templates**, **Outbound sorting template**, **Cycle count plans**, **Cycle counting threshold**, **Shipment consolidation policies**, **Shipment consolidation templates**.

Example buttons:
**Edit query**, **Select items**, **Select locations**, **Select products**, **Select product variants**, **Select locations to replenish**, **Select zones to replenish**, **Define product query**, **Define product variant query**.

> [!IMPORTANT]
> - The most common mistake users make in these queries is adding table joins and expecting that the functionality will only be applicable to those added records (e.g. is a sales table is joined to the **Location directive action** query, that the **Location directive action** would now only be applicable when processing those sales orders which fulfill the user defined criteria). A more detailed explanation can be found below, and in the **Location directives** form example.
> - The system can only be expected to add filters to the tables that were in the default query. If the user adds a join to sales orders, then it can't be expected that this record will now automatically have a filter added to "the sales order being released", for example.

## Basic query structure

### Ranges

Ranges are basically filters used to limit which records are returned from the query. They are explicitly applied to the individual table fields, and implicitly when join relations are used.

### Joins

Joins are applied between two tables and decide how the data between them is filtered and potentially combined. There can be multiple joins to the same table.

The queries in X++ support several different joins: *InnerJoin*, *OuterJoin*, *ExistsJoi*n and *NoExistsJoin*. However, only *ExistsJoin* (the default value regardless of the join mode, like *1:n* or *n:1*) and *NoExistsJoin* (*NotExist*) are available in the User-configurable queries.

> [!NOTE]
> - There are some special cases where dedicated functionality was developed to support inner or outer joins in User-configurable queries, like in the **Label layout data** source form, but in general, those are not available.
> - Another exception is that if the default query has those types of joins, the user can add ranges to them, for example, but any new table joins added through the UI can only be exists or not exists joins.
> - The user is not able to see which type of join is used in the default query.

- The *InnerJoin* will return the combined records from both of the joined tables, so it most cases a subset of the two table records. The join will be made based on the specified relations between the two tables.

- The *OuterJoin* will only return the records from the first table, but the records that have a match in the other table will also have those fields populated. The join will be made based on the specified relations between the two tables.

- The *ExistsJoin* is similar to the *InnerJoin* with the difference that no record information from the second table is returned in the result.

- The *NoExistsJoin* is similar to the *ExistsJoin* in the sense that only records information from the first table will be returned, but in this case the filtering will be the opposite, i.e. if the match doesn't exist, then the record will be returned. 

### Sorting

Sorting is applied after getting the results from the ranges and joins. It is only applicable to the returned records and fields. So, having sorting on the second table in an *ExistsJoin* isn't applicable.

> [!IMPORTANT]
> Adding additional ranges, sorting and especially table joins will almost certainly have a negative performance impact. In some cases, ranges and joins must be added to fulfill the business requirements, but the user should be careful not to make too complex queries.

## Examples

### Work templates form

In this form, each of the different Work order types has a slightly different default query. The purpose of the query is to select which work template can be used to create warehouse work (and remaining work lines) from the initial **Temporary work transactions** during wave processing. The **Temporary work transactions** are usually initialized from the order lines and headers.

If we use *Sales orders* as an example, the top table is **Temporary work transactions**. There are two tables joined to it, *Order lines* and *Locations*. Unfortunately, it is not possible to see the join type from the UI, only from the development environment. In this case, both are inner joins. We have a few more joins with the *Order lines* table. *Locations* doesn’t have any more joins. *Order lines* is joined to the *Sales orders* table (inner join, and *Sales orders* table has no further joins) and the *Items* table (inner join, and the *Items* table has more joins). *Items* is joined to the *Warehouse item number* table (inner join, and *Warehouse item number* table has no further joins). Also, there are not default ranges added to the query.

Given the above knowledge, we can conclude that the user will be able to add ranges to any of the above mentioned tables, and only those records that fulfill all of those conditions will be able to use this work template during wave processing.

For example, if the user selects the *Warehouse item number* table and sets **Field** to *Code 1*, and **Criteria** to *A*, it would mean that only those items that have **Product filter code** **Code 1** set to *A* will be able to use this work template.

Let's say the user now adds a relation to the *Carrier (Shipping carrier)* table to the **Temporary work transactions** table. This would be an exists type of join. The user can now add a **Range** on that table, for example on the **Carrier** table and **Shipping carrier** field with some carrier name in the **Criteria** field. This would mean this work template is now applicable only to those temporary work transactions which has that specific carrier name set.

> [!NOTE]
> -	Have in mind that even if there are many tables listed as available for being joined, it doesn't mean that the related fields are actually populated in all the cases, which might lead to unexpected results.

### Location directives form
In this form, there are two different User-configurable queries, the one related to the **Location directive** (header), and the other related to the **Location directive actions**. We'll take a closer look at the second. The action query has different default values depending on, for example **Work type** or if **Batch enabled** is selected (not an exhaustive list). The purpose of this query is to find a suitable warehouse location for the work line to pick from or put to, for example.

If we use a *Sales orders* *Pick* without **Batch enabled** as an example, the top table is *Locations*. There is one table joined to it *On-hand inventory* (it is inner joined). We can also see that there are already some ranges predefined. **Warehouse**, **Physical inventory** and **No open quantities** have **Criteria** set, and are not editable, while **Location** and **Item number** are present, but have no values in the **Criteria** and are editable.

> [!NOTE]
> In older versions, there might be a third table (*Inventory dimensions*) in between *Locations* and *On-hand inventory*.

The user can now specify the desired ranges, for example, *Location profile ID* on the **Locations** table. In that case, only those locations that match the **Criteria** will be evaluated when trying to find a valid location to pick the item from.

If the user adds a sorting, for example table *Locations*, field *Location*, Search direction *Ascending*, then the locations will be evaluated based on the order of their location IDs. For example, a location with the ID *Location123* will be evaluated before *Location321*.

> [!NOTE]
> In some cases, there are additional ranges or tables applied during the processing, which is not visible to the user. In the example above, the item will always be applied for the pick location directive action, as the on-hand inventory will be picked for a specific item.

Let's say the user now adds a relation to the *Order lines (Item number)* table to the *On-hand inventory* table. This would be an exists type of join. The user can now add a **Range** on that table, for example on the *Order lines* table and the *Customer* field with some *Customer account* in the **Criteria** field (e.g. *Customer1*).

> [!IMPORTANT]
> The user might think that the above query will now only be applicable when processing sales orders for that given *Customer account*. However, that is not what will happen! If we analyze what the query does, and how it is built, the meaning is the following: find a location which has an item for which there exists a sales line for *Customer1*. Basically, if the given item was ever added to a sales line for *Customer1*, this additional table join and range will basically have no functional effect, and will only add a performance overhead.