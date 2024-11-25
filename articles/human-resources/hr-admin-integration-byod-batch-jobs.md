---
# required metadata

title: Optimize BYOD scheduled batch jobs
description: This article explains how to optimize performance when you're using the bring your own database (BYOD) feature with Microsoft Dynamics 365 Human Resources.
author: twheeloc
ms.date: 08/17/2020
ms.topic: article
# optional metadata

# ms.search.form: BatchJob, BatchJobEnhanced
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-08-10
ms.dyn365.ops.version: Platform update 36
---

# Optimize BYOD scheduled batch jobs



[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article explains how to optimize performance when you're using the bring your own database (BYOD) feature. For more information about BYOD, see [Bring your own database (BYOD)](../fin-ops-core/dev-itpro/analytics/export-entities-to-your-own-database.md?toc=%2fdynamics365%2fhuman-resources%2ftoc.json).

## Performance considerations for data export

After entities are published to the destination database, you can use the Export function in the **Data management** workspace to move data. The Export function lets you define a Data movement job that contains one or more entities. For more information about data export, see [Data import and export jobs overview](../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md?toc=%2fdynamics365%2fhuman-resources%2ftoc.json).

You can use the **Export** page to export data into different target data formats, such as a comma-separated values (CSV) file. This page also supports SQL databases as another destination.

You can create a data project that has multiple entities and use a batch job to schedule that data project to run. If you select the **Export in batch** option, you can schedule the data export job to run periodically.

To help preserve the overall reliability of the BYOD export, you must be careful when you add multiple entities to an export project. When you're determining the number of entities to add to the same project, consider the following parameters:

- The complexity of the entities
- The expected data volume per entity
- The overall time that will be required to complete the export at the job level

For the best performance, avoid adding hundreds of entities to a single project. We recommend that you create multiple jobs, each of which contains fewer entities.

## Scheduling BYOD batch jobs

To help reduce the impact on users of Microsoft Dynamics 365 Human Resources, run BYOD batch jobs at night or after hours. Be sure to check the time zone for recurring batch jobs. Some batch jobs might use Pacific Standard Time (PST).

To help avoid performance issues, consider the following factors when you configure the scheduling frequency for BYOD batch jobs:

- The time that is required to complete each batch job
- The business need for the data in BYOD

Set the frequency for each batch job to a value that ensures that the job can be completed well before its next scheduled run time. Avoid running multiple jobs in parallel, because this approach can negatively affect the performance of Human Resources.

For the best performance, always use the **Export in batch** option on the **Export** page to schedule BYOD batch jobs. Avoid scheduling recurring exports at **Manage \> Manage recurring data jobs**.

## Incremental export

When you add an entity for data export, you can do either an incremental push (export) or a full push. A full push deletes all existing records from an entity in the BYOD database. It then inserts the current set of records from the Human Resources entity.

To do an incremental push, you must turn on change tracking for each entity on the **Entities** page. For more information, see [Enable change tracking for entities](../fin-ops-core/dev-itpro/data-entities/entity-change-track.md?toc=%2fdynamics365%2fhuman-resources%2ftoc.json).

If you select an incremental push, the first push is always a full push. SQL tracks changes from this first full push. When a new record is inserted, or when a record is updated or deleted, the change is reflected in the destination entity.

## Time-outs

Here are the default time-outs for BYOD exports:

- Ten minutes for truncation operations
- One hour for bulk insert operations

When volumes are high, these time-out settings might not be sufficient. To update them, go to **Data management \> Framework parameters \> Bring your own database**. These time-outs are company-specific and must be set separately for each company.

## Known limitations

The BYOD feature has the following limitations:

- There should be no active locks on your database during synchronization. Active locks can cause slow writes or even failure to export data to your Azure SQL database.
- You can't export composite entities into your own database. Currently, composite entities aren't supported. You must export individual entities that make up the composite entity. However, you can export both entities in the same data project.
- Entities that don't have unique keys can't be exported by using incremental push. You might face this limitation especially when you try to incrementally export records from a few ready-made entities. Because these entities were designed to enable the import of data, they don't have a unique key.

## Troubleshooting

### Incremental push doesn't work correctly

**Issue:** When a full push occurs for an entity, you see a large set of records in BYOD when you use a **select** statement. However, when you do an incremental push, you see only a few records in BYOD. It seems as though the incremental push deleted all the records and added only the changed records in BYOD.

**Solution:** The SQL change tracking tables might not be in the expected state. In cases of this type, we recommend that you turn off change tracking for the entity and then turn it back on. For more information, see [Enable change tracking for entities](../fin-ops-core/dev-itpro/data-entities/entity-change-track.md?toc=%2fdynamics365%2fhuman-resources%2ftoc.json).

### Staging tables aren't clearing

**Issue:** When using staging for the project, the staging tables don't clear out correctly. The data in the tables then continues to grow, causing performance issues.

**Solution:** Seven days of history is maintained in the staging tables. Historical data older than seven days is automatically cleared from the staging tables by the **Import export staging cleanup** batch job. If this job gets stuck, the tables won't clear out correctly. Restarting this batch job will continue the process to automatically clear out the staging tables.

## See also

[Data management overview](../fin-ops-core/dev-itpro/data-entities/data-entities-data-packages.md?toc=%2fdynamics365%2fhuman-resources%2ftoc.json)<br>
[Bring your own database (BYOD)](../fin-ops-core/dev-itpro/analytics/export-entities-to-your-own-database.md?toc=%2fdynamics365%2fhuman-resources%2ftoc.json)<br>
[Data import and export jobs overview](../fin-ops-core/dev-itpro/data-entities/data-import-export-job.md?toc=%2fdynamics365%2fhuman-resources%2ftoc.json)<br>
[Enable change tracking for entities](../fin-ops-core/dev-itpro/data-entities/entity-change-track.md?toc=%2fdynamics365%2fhuman-resources%2ftoc.json)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
