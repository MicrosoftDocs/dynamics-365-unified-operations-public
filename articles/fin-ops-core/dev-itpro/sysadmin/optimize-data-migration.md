---
# required metadata

title: Optimizing data migration for Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management
description: The article provides an overview of how to optimize data migration for Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management.
author: skaue-ms
manager: AnnBe
ms.date: 01/04/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: toskaue
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.13

---

# Optimizing data migration for Microsoft Dynamics 365 Finance and Dynamics 365 Supply Chain Management

[!include [banner](../includes/banner.md)]

Data migration is a key component towards a successful go-live implementation. One of the main concerns some customers have is the speed in which the data can be migrated, especially if there are vast amounts of data and a small cut-over window. The Data Migration Framework is also used for moving data as part of business requirements and operations.

The information below represents a set of steps and actions that can be taken in order to optimize the performance of data migration. 

> [!NOTE]
> Testing results on a tier 1 environment should not be compared or extrapolated to performance on a tier 2+ sandbox environment.

The standard entities have not all been optimized for data migration. For example, some have been optimized for OData integration and therefore if the required entity cannot be optimized to meet the performance requirements, it is recommended that a new optimized entity is created. A developer can accelerate this process by duplicating an existing entity.

Begin the optimization phase by using a subset of the data. For example, if it is necessary to import a million records, consider starting with 1,000 records, and then increasing to 10,000 and then 100,000.

Once you have identified the entities, you will use then you will want to go through the following sections to explore opportunities for optimizations. 

## Disable Change Tracking

Change tracking can be [enabled and disabled](../data-entities/entity-change-track.md) from the list of entities. 

Data management > Data entities > Change tracking > Disable Change Tracking

## Enable Set-based processing

Verify the entity supports set-based processing from the list of entities. 

Data management > Data entities > Set-based processing (column in grid)

See example for [how it can be done with General Journal entity](../data-entities/tips-tricks-import-general-journal-entity.md).
Not all entities support set-based processing and you may receive a message such as "Customer definitions" (CustCustomerBaseEntity).

If it is necessary to create an entity that allows set-based processing, some key considerations are:

* The data sources can't be read-only
* The parameter on the data entity ValidTimeStateEnabled must be "No"
* All data sources must have TableType set to Regular
* The parameter of QueryType on the Metadata node can't be Union
* The main data source can't prevent saving data across companies however embedded data sources allow it
* The main data source can't prevent saving data across partitions however embedded data sources allow it

## Create data migration batch group

During cut-over, execute the data migration while there is little to no other activity is going on. It can help to configure and use a batch group with all or at least most AOS nodes assigned.

System administration > Setup > Batch group

## Priority-based batch scheduling

In Platform update 31, we introduced is a new feature that will optimize the way batch jobs are executed. Consider enabling [Priority-based batch scheduling](priority-based-batch-scheduling.md) if contention is identified in the batch framework.

## Maximum batch threads

You can configure the maximum number of batch threads per AOS to better utilize parallelism and multithreading. This value should be changed cautiously. If the number is too high, it can have negative performance implications. The default value is currently 4. If necessary, the value can be changed to 8. It should not be configured above 8 without significant performance testing.

System administration > Setup > Server configuration

## Import in batch

Whenever running an import job, ensure that it is run in batch. Otherwise it will be run using a single thread, which will prevent the system from using the most of these optimization configurations.

## Clean staging tables

It is recommended to clean up the staging tables. This optimization can be achieved by scheduling the [Job history cleanup job](batch-history-cleanup.md) (available in Platform update 29 and later). After enabling the feature "Execution history cleanup" via Feature management, you will be able to access it from:

Data management > Job history cleanup

## Defragmentation of indexes

Review the [configuration of the index defragmentation job](batch-job-sql-defragmentation.md). It is recommended that this runs daily, though not when a data migration job is executing. Review the parameters to ensure the job captures the tables and indexes that are being changed via the data migration job. 

## Update statistics

Prior to running a data migration job for a large volume of data, consider updating the statistics across the associated tables. This is automatically taken care of in production environments. You can run [update statistics for a specific table from LCS](../lifecycle-services/querycookbook.md), or in a sandbox environment use sp_updatestats stored procedure through direct SQL.

## Clean the data

Rectify the errors related to data quality to reduce the code churn for validations and error processing. With a high volume of invalid or inconsistent set of data, the time spent on validations and reporting errors will add to the total time spent doing the migration.

## Configurations to test during data migration test runs

The following set of configurations can impact performance of data migration and therefore it is recommended that these are tested with different values to find the optimal configuration for your data migration scenario.

### Configure entity execution parameters

You can modify the execution parameters for all or specific entities here:

Data management > Framework parameters > Entity settings > Configure entity execution parameters

#### Import threshold record count

This value configures the number of records that will be split and assigned to separate tasks.

#### Import task count

This value configures how many threads will be used for the data migration job for a specific entity. For example, if the Maximum batch threads are 8 for each server, and there are four servers assigned to the data migration batch group, the maximum value for Import task count should be eight times four, which is 32.

If a data entity does not support multithreading, when you attempt to configure the entity, you will see an error message.
Example: "Custom sequence is defined for the entity 'Customers V3', more than one task is not supported."

### Validations

Validation logic for record inserts or updates may have been incorporated into the system, and/or there may be validation on individual fields. If the validation logic is taking too long and if the data migration process is mature enough to confidently disable these options for cutover this should be considered. You will find these settings on each entity under: 

Data management > Data entities > Entity structure

#### Run business validations

If this flag is enabled, the system will execute any logic written into the validateWrite() method on the table, and related event handlers.

#### Run business logic in insert or update method

If this flag is enabled, the system will execute any logic written into the insert() or update() method on the table, and related event handlers.

#### Call validate Field method on target

Field validation can be found under:
Data management > Data entities > Modify target mapping

If this option is enabled the validateField(FieldId p1) method will be called for the specific field.

### Data migration performance optimization process

Here are some general recommendations how to approach data migration performance optimization.

* It is recommended to break up large files into smaller chunks. The reason for this is that it allows time for the SQL optimizer to determine if a new query plan will be optimal.
* Performance should be tested in an appropriate tier 2+ environment.
* Performance should be tested in a mock cutover prior to Go-Live. 

Data migration performance testing is an iterative process, thus it is suggested that information regarding each test is collected and compared to determine the optimal configuration for a specific entity. You will want to collect and verify some of the following settings:

* Batch group used
* Number of AOS assigned to each batch group
* Maximum batch threads to each AOS

Example of information to collect for each entity:

| Entity | Number of Records | Source Format | Change Tracking Disabled | Set-based Processing | Import Threshold Record Count | Import Task Count | Run Business Validation | Run Business Logic In Insert Or Update Method | Call Validate Field Method | Required Performance | Actual Performance |
|------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|-------------|
| (Name of entity being tested) | (Number of records being imported) | (Source format of data to be imported) | (Yes/No) | (Yes/No) | (Number of records) | (Number of tasks) | (Yes/No) | (Yes/No) | (Yes/No) (Potential field list) | (Time required for import to complete in order to achieve cutover window) | (Actual time taken to import records) |

There are additional areas where performance can be optimized, for example analyzing the specific queries and query plans, however those processes are covered in other articles and are not intended for this article.

For more information about performance troubleshooting and optimization, see the following content:

* [Performance troubleshooting using tools in Lifecycle Services (LCS)](../lifecycle-services/performancetroubleshooting.md)
* [Query cookbook](../lifecycle-services/querycookbook.md)












