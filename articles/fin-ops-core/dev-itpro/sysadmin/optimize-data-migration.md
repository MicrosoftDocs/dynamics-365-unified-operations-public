---
title: Optimize data migration for finance and operations apps
description: Learn about steps and actions that you can use to optimize data migration for finance and operations apps, including an outline on disabling change tracking.
author: skaue-ms
ms.author: toskaue
ms.topic: how-to
ms.date: 03/13/2026
ms.custom:
ms.reviewer: johnmichalak 
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-01-31
ms.search.form: 
ms.dyn365.ops.version: 10.0.13
---

# Optimize data migration for finance and operations apps

[!include [banner](../includes/banner.md)]

Data migration is a key success factor in almost every implementation. Some customers are primarily concerned about the speed of data migration, especially if there's a vast amount of data and a small cutover window. You can also use the [Data migration framework](../data-entities/data-entities-data-packages.md) to move data as part of business requirements and operations.

The information in this article describes steps and actions that you can use to optimize the performance of data migration.

> [!NOTE]
> Don't compare or extrapolate testing results in a Tier-1 environment to performance in a Tier-2 or higher sandbox environment.

Not all standard entities are optimized for data migration. Some entities are optimized for integration with Open Data Protocol (OData). If a required entity can't be optimized to meet the performance requirements, [create a new optimized entity](../data-entities/build-consuming-data-entities.md). A developer can accelerate this process by duplicating an existing entity.

Begin the optimization phase by using a subset of the data. For example, if you must import one million records, consider starting with 1,000 records, then increase the number to 10,000 records, and then increase it to 100,000 records.

After you identify the entities to use, go through the following sections to explore opportunities for optimization.

## Disable change tracking

You can [enable and disable change tracking](../data-entities/entity-change-track.md) from the list of entities.

1. In the **Data management** workspace, select the **Data entities** tile.
1. On the **Target entities** page, select the entity in the grid. On the Action Pane, select **Disable Change Tracking** on the **Change tracking** tab.

## Enable set-based processing

Follow these steps to verify that an entity supports set-based processing:

1. In the **Data management** workspace, select the **Data entities** tile.
1. On the **Target entities** page, find the entity in the grid, and review the value in the **Set-based processing** column.

For an example that shows how to enable set-based processing for the **General Journal** entity, see [Best practices for importing vouchers by using the General journal entity](../data-entities/tips-tricks-import-general-journal-entity.md). Not all entities support set-based processing. For example, if you try to enable set-based processing for the **Customer definitions** (**CustCustomerBaseEntity**) entity and save your change, you receive the following warning message:

> Set operations not supported for 'Customer definitions' entity.

Here are some important considerations if you must create an entity that supports set-based processing:

* The data sources can't be read-only.
* The [**ValidTimeStateEnabled**](../dev-tools/date-effectivity.md) property of the data entity view must be set to **No**.
* All tables on the data sources must have the **TableType** property set to **Regular**.
* The [**QueryType**](../dev-ref/application-explorer-aot-properties.md#query-properties-1) property on the used **Query** can't be set to **Union**.
* The main data source can't prevent data from being saved across companies. However, embedded data sources can.
* The main data source can't prevent data from being saved across partitions. However, embedded data sources can.

## Create a data migration batch group

During cutover, run the data migration while there's little or no other activity. It can be helpful to configure and use a batch group where most or all compute nodes are assigned.

You can configure a batch group on the **Batch group** page (**System administration** > **Setup** > **Batch group**).

## Enable priority-based batch scheduling

In Platform update 31, the new [priority-based batch scheduling](priority-based-batch-scheduling.md) feature optimizes how batch jobs run. If the batch platform identifies contention, consider enabling priority-based batch scheduling.

## Configure the maximum number of batch threads

To better use parallelism and multithreading, configure the maximum number of batch threads per instance of Application Object Server (AOS) by setting the **Maximum batch threads** field on the **Server configuration** page (**System administration \> Setup \> Server configuration**). Be careful when changing the value of this field. A value that's too high can negatively affect performance. Currently, the default value is **8**. You can increase the value to **12** or **16**. However, don't set the field to a value that's more than 16 unless you do significant performance testing.

## Import in batch mode

Run an import job in batch mode. Otherwise, a single thread runs the job. In this case, the system can't take full advantage of these optimization configurations.

## Clean staging tables

Clean up the staging tables. You can achieve this optimization by scheduling the [Job history cleanup job](../data-entities/data-import-export-job.md#job-history-cleanup). To schedule this job, select the **Job history cleanup** tile in the **Data management** workspace.

> [!NOTE]
> You must first turn on the **Execution history cleanup** feature in the **Feature management** workspace.


## Update statistics

Before you run a data migration job that involves a large volume of data, consider updating the statistics across the associated tables. This optimization specifically applies to sandbox environments, because it's handled automatically in production environments. You can [update statistics for a specific table from LCS](../lifecycle-services/querycookbook.md). Alternatively, in a sandbox environment, you can use the **sp\_updatestats** stored procedure through direct SQL.

## Clean the data

The time that validations and error reporting take increases the total time of the migration. Consider this fact when you import a high volume of invalid or inconsistent data. Fix and reduce errors that are related to data quality to help prevent unnecessary executions of validation and error handling.

## Configurations to test during test runs of data migration

The following configurations can affect performance. Test changes by using different values that are suitable for your scenario.

### Configure entity execution parameters

Follow these steps to change the execution parameters for all entities or specific entities.

1. In the **Data management** workspace, select the **Framework parameters** tile.
1. On the **Data import/export framework parameters** page, on the **Entity settings** tab, select **Configure entity execution parameters**.
1. On the **Entity import execution parameters** page, set the **Import threshold record count** and **Import task count** fields as appropriate for the desired entities.

#### Import threshold record count

This value determines the number of records to process per thread. [By modifying the **Import threshold record count**](../data-entities/data-import-export-job.md#parallel-imports) you can control how you split the import into smaller tasks.

#### Import task count

This field defines the number of threads to use for the data migration job for a specific entity. For example, the **Maximum batch threads** field for each server is set to **8**, and four servers are assigned to the data migration batch group. In this case, the total maximum value of the **Import task count** field is **32** (= 8 × 4).

If a data entity doesn't support multithreading, you receive an error message when you try to configure the entity. For example:

> Custom sequence is defined for the entity 'Customers V3', more than one task is not supported.

### Validations

The system might include validation logic for record insertions or updates, or it might validate individual fields. If the data migration process is mature, you can reduce the time spent on imports by disabling this validation.

Follow these steps to change the settings for each entity.

1. In the **Data management** workspace, select the **Data entities** tile.
1. On the **Target entities** page, select the entity in the grid. On the Action Pane, select **Entity structure**.
1. On the **Entity structure** page, set the **Run business validations** and **Run business logic in insert or update method** fields as appropriate.

#### Run business validations

If you select this check box, the system runs any logic that's written into the **validateWrite()** method on the table. It also runs any related event handlers.

#### Run business logic in insert or update method

If you select this check box, the system runs any logic that's written into the **insert()** or **update()** method on the table. It also runs any related event handlers.

#### Call the validateField method on the target

Follow these steps to run field validation.

1. In the **Data management** workspace, select the **Data entities** tile.
1. On the **Target entities** page, select the entity in the grid. On the Action Pane, select **Modify target mapping**.
1. On the **Map staging to target** page, select the **Call validate Field method** check box for the field that you want to run validation for. The **validateField(FieldId p1)** method is then called for that field.

### Recommendations for optimizing data migration performance

To optimize the performance of data migration, use the following approach:

* Break up large files into smaller chunks. This approach gives the SQL optimizer time to determine whether a new query plan is optimal.
* Test performance in an appropriate Tier 2 or higher environment.
* Test performance in a mock cutover before go-live.

Testing data migration performance is an iterative process. Collect and compare information about each test to determine the optimal configuration for a specific entity. Collect and verify some of the following settings:

* The batch group that you use
* The number of batch servers that you assign to each batch group
* The maximum number of batch threads per batch server

Here's an example of the information that you might collect for each entity.

| Information | Description |
|---|---|
| Entity | The name of the entity that you're testing |
| Number of records | The number of records that you're importing |
| Source format | The source format of the data that you're importing |
| Change tracking disabled | Yes/No |
| Set-based processing | Yes/No |
| Import threshold record count | The number of records |
| Import task count | The number of tasks |
| Run business validations | Yes/No |
| Run business logic in insert or update method | Yes/No |
| Call validate Field method | Yes/No (potential field list) |
| Required performance | The amount of time that the import must be completed within to achieve the cutover window |
| Actual performance | The actual amount of time that was required to import records |

You can optimize performance in other areas. For example, you can analyze the specific queries and query plans. However, those processes are covered in other topics.

For more information about performance troubleshooting and optimization, see the following topics:

* [Performance troubleshooting using tools in Lifecycle Services (LCS)](../lifecycle-services/performancetroubleshooting.md)
* [Query cookbook](../lifecycle-services/querycookbook.md)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

